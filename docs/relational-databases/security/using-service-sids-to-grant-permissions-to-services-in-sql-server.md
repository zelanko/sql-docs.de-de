---
description: Verwenden von Dienst-SIDs zum Erteilen von Berechtigungen für Dienste in SQL Server
title: Verwenden von Dienst-SIDs zum Erteilen von Berechtigungen für Dienste
ms.custom: seo-dt-2019
author: randomnote1
ms.author: dareist
ms.date: 05/02/2019
ms.topic: conceptual
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.openlocfilehash: f366af08581accf5ef1f1c8fc00830f6cc592537
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88403566"
---
# <a name="using-service-sids-to-grant-permissions-to-services-in-sql-server"></a>Verwenden von Dienst-SIDs zum Erteilen von Berechtigungen für Dienste in SQL Server

In SQL Server werden [Pro-Dienst-SIDs (Sicherheits-IDs für einzelne Dienste)](https://support.microsoft.com/help/2620201/sql-server-uses-a-service-sid-to-provide-service-isolation) verwendet, um einem bestimmten Dienst direkt Berechtigungen zu erteilen. Mit dieser Methode werden in SQL Server Berechtigungen für die Engine- und Agent-Dienste (NT SERVICE\MSSQL$<InstanceName> bzw. NT SERVICE\SQLAGENT$<InstanceName>) erteilt. Damit können diese Dienste nur auf die Datenbank-Engine zugreifen, solange sie ausgeführt werden.

Mit dieser Methode können auch anderen Diensten Berechtigungen erteilt werden. Mithilfe einer Dienst-SID kann auf den Mehraufwand für das Verwalten und Warten von Dienstkonten verzichtet und das Erteilen von Berechtigungen für Systemressourcen enger und präziser gesteuert werden.

Eine Dienst-SID kann beispielsweise für die folgenden Dienste verwendet werden:

- Integritätsdienst von System Center Operations Manager (NT SERVICE\HealthService)
- WSFC-Dienst (Windows Server-Failoverclustering) (NT SERVICE\ClusSvc)

Einige Dienste besitzen standardmäßig keine Dienst-SID. In diesen Fällen muss die Dienst-SID über [SC.exe](/windows/desktop/services/configuring-a-service-using-sc) erstellt werden. Mit dieser von den Administratoren von Microsoft System Center Operations Manager übernommenen [Methode](https://kevinholman.com/2016/08/25/sql-mp-run-as-accounts-no-longer-required/) können Berechtigungen für HealthService in SQL Server erteilt werden.

Nachdem die Dienst-SID erstellt und bestätigt wurde, muss ihr in SQL Server eine Berechtigung erteilt werden. Berechtigungen werden erteilt, indem entweder über [SQL Server Management Studio (SSMS)](/sql/ssms/download-sql-server-management-studio-ssms) oder über eine Abfrage ein Windows-Anmeldename erstellt wird. Sobald der Anmeldename erstellt wurde, kann er wie jeder andere Anmeldename Berechtigungen erhalten, Rollen hinzugefügt und Datenbanken zugeordnet werden.

> [!TIP]
> Tritt der Fehler `Login failed for user 'NT AUTHORITY\SYSTEM'` auf, vergewissern Sie sich, dass die Dienst-SID für den gewünschten Dienst vorhanden ist, der Anmeldename für die Dienst-SID in SQL Server erstellt wurde und der Dienst-SID die entsprechenden Berechtigungen in SQL Server erteilt wurden.

## <a name="security"></a>Sicherheit

### <a name="eliminate-service-accounts"></a>Entfernen von Dienstkonten

Bisher wurden Dienstkonten dafür verwendet, Diensten das Anmelden bei SQL Server zu ermöglichen. Damit war auch ein Mehraufwand an Verwaltung verbunden, da das Kennwort des Dienstkontos verwaltet und regelmäßig aktualisiert werden musste. Außerdem konnten die Anmeldeinformationen des Dienstkontos von Personen benutzt werden, die beim Ausführen von Aktionen in der Instanz ihre Aktivitäten maskieren wollten.

### <a name="granular-permissions-to-system-accounts"></a>Präzise Berechtigungen für Systemkonten

Berechtigungen für Systemkonten wurden bislang durch Erstellen eines Anmeldenamens für die Konten [LocalSystem](https://msdn.microsoft.com/library/windows/desktop/ms684190) ([NT-AUTORITÄT\SYSTEM in de-DE](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions#Localized_service_names)) oder [NetworkService](/windows/desktop/Services/networkservice-account) ([NT-AUTORITÄT\NETZWERKDIENST in de-DE](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions?#Localized_service_names)) erteilt. Diesem Anmeldenamen wurden dann die Berechtigungen erteilt. Bei dieser Methode werden jedem Vorgang oder Dienst, der als Systemkonto ausgeführt wird, Berechtigungen in SQL erteilt.

Mit einer Dienst-SID werden Berechtigungen nur für einen bestimmten Dienst erteilt. Der Dienst kann nur auf die Ressourcen zugreifen, für die er Berechtigungen erhielt, solange er ausgeführt wird. Wird beispielsweise `HealthService` als `LocalSystem` ausgeführt und erhält die Berechtigung `View Server State`, erhält das `LocalSystem`-Konto nur eine Berechtigung für `View Server State`, solange es im Kontext von `HealthService` ausgeführt wird. Versucht ein anderer Vorgang auf den SQL-Serverstatus als `LocalSystem` zuzugreifen, wird der Zugriff verweigert.

## <a name="examples"></a>Beispiele

### <a name="a-create-a-service-sid"></a>A. Erstellen einer Dienst-SID

Mit dem folgenden PowerShell-Befehl können Sie eine Dienst-SID für den Integritätsdienst von System Center Operations Manager erstellen:

```PowerShell
sc.exe --% sidtype "HealthService" unrestricted
```

> [!IMPORTANT]
> Durch die Angabe von `--%` wird PowerShell mitgeteilt, dass der Rest des Befehls nicht analysiert werden muss. Dies ist bei älteren Befehlen und Anwendungen nützlich.

### <a name="b-query-a-service-sid"></a>B. Abfragen einer Dienst-SID

Führen Sie den folgenden Befehl in PowerShell aus, um eine Dienst-SID zu überprüfen oder wenn Sie sicherstellen möchten, dass eine Dienst-SID vorhanden ist:

```PowerShell
sc.exe --% qsidtype "HealthService"
```

> [!IMPORTANT]
> Durch die Angabe von `--%` wird PowerShell mitgeteilt, dass der Rest des Befehls nicht analysiert werden muss. Dies ist bei älteren Befehlen und Anwendungen nützlich.

### <a name="c-add-a-newly-created-service-sid-as-a-login"></a>C. Hinzufügen einer neu erstellten Dienst-SID als Anmeldename

Im folgenden Beispiel wird ein Anmeldename für den Integritätsdienst von System Center Operations Manager mithilfe von T-SQL erstellt:

```SQL
CREATE LOGIN [NT SERVICE\HealthService] FROM WINDOWS
GO
```

### <a name="d-add-an-existing-service-sid-as-a-login"></a>D: Hinzufügen einer vorhandenen Dienst-SID als Anmeldename

Im folgenden Beispiel wird ein Anmeldename für den Clusterdienst mithilfe von T-SQL erstellt. Indem Sie dem Clusterdienst Berechtigungen erteilen, ist es nicht mehr erforderlich, dem Systemkonto übermäßige Berechtigungen zu erteilen.

```SQL
CREATE LOGIN [NT SERVICE\ClusSvc] FROM WINDOWS
GO
```

### <a name="e-grant-permissions-to-a-service-sid"></a>E. Erteilen von Berechtigungen für eine Dienst-SID

Im folgenden Beispiel werden dem Clusterdienst die für das Verwalten von Verfügbarkeitsgruppen erforderlichen Berechtigungen erteilt:

```SQL
GRANT ALTER ANY AVAILABILITY GROUP TO [NT SERVICE\ClusSvc]
GO

GRANT CONNECT SQL TO [NT SERVICE\ClusSvc]
GO

GRANT VIEW SERVER STATE TO [NT SERVICE\ClusSvc]
GO
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Struktur der Dienst-SID finden Sie unter [SERVICE_SID_INFO structure (Struktur von SERVICE_SID_INFO)](/windows/win32/api/winsvc/ns-winsvc-service_sid_info).

Hier finden Sie Informationen zu weiteren verfügbaren Optionen beim [Erstellen eines Anmeldenamens](/sql/t-sql/statements/create-login-transact-sql).

Informationen zur Verwendung von rollenbasierter Sicherheit mit Dienst-SIDs finden Sie unter [Erstellen von Rollen](/sql/t-sql/statements/create-role-transact-sql) in SQL Server.

Hier finden Sie Informationen zu den unterschiedlichen Methoden für das [Erteilen von Berechtigungen](/sql/t-sql/statements/grant-transact-sql) für Dienst-SIDs in SQL Server.
