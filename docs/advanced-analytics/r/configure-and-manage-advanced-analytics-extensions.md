---
title: Erweiterte Konfiguration für SQL Server Machine Learning Services | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8384773f6db4c0ced2fc68e52cd78100c98c52fd
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392082"
---
# <a name="advanced-configuration-options-for-sql-server-machine-learning-services"></a>Erweiterte Konfigurationsoptionen für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Änderungen, die Sie zum Ändern der Konfiguration der Runtime externen Skripts und andere Dienste im Zusammenhang mit Machine Learning in SQL Server nach der Installation vornehmen können.

**Gilt für:** SQL Server 2016 R Services, SqlServer 2017 Machine Learning-Dienste

##  <a name="bkmk_Provisioning"></a> Stellen Sie zusätzlicher Benutzer Konten für Machine learning

Externes Skript verarbeitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Kontext von lokalen Benutzerkonten mit einer mit geringen Rechten ausgeführt. Diese Prozesse in einzelnen Konten mit niedrigen Berechtigungen ausgeführt, hat die folgenden Vorteile:

+ Berechtigungen von dem externen Skript-Laufzeitprozessen auf reduziert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer
+ Ermöglicht eine Isolation zwischen Sitzungen, die von einer externen Runtime wie R oder Python.

Als Teil der Installation einer neuen Windows *benutzerkontenpool* erstellt wird, enthält die lokalen Benutzerkonten zum Ausführen von externen laufzeitprozesse, wie R oder Python erforderlich sind. Sie können die Anzahl der Benutzer ändern, um Machine Learning-Aufgaben unterstützen. 

Darüber hinaus muss der Datenbankadministrator Geben Sie dieser Gruppe die Berechtigung, die mit jeder Instanz herstellen, in denen Machine Learning aktiviert wurde. Weitere Informationen finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

Auf protext sensible Ressourcen auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie können eine Zugriffssteuerungsliste (ACL) für diese Gruppe definieren. Angeben von Ressourcen, denen die Gruppe Zugriff auf verweigert wird, können Sie den Zugriff durch externe Prozesse wie das R- oder Python-Laufzeiten verhindern.

+ Der Benutzerkontenpool ist mit einer bestimmten Instanz verknüpft. Ein separater Pool von workerkonten ist für jede Instanz erforderlich, auf dem Machine Learning aktiviert wurde. Konten können nicht zwischen Instanzen freigegeben werden.

+ Benutzerkontonamen im Pool weisen das Format „SQLInstanzname*nn*“ auf. Beispielsweise wenn Sie die Standardinstanz für Machine learning verwenden, unterstützt der benutzerkontenpool Kontonamen wie MSSQLSERVER01, MSSQLSERVER02 usw.

+ Die Größe des Benutzerkontenpools ist statisch und der Standardwert ist 20. Die Anzahl der externen-laufzeitsitzungen, die gleichzeitig gestartet werden kann, wird durch die Größe dieses benutzerkontenpools beschränkt. Um diese Beschränkung zu ändern, sollte ein Administrator SQL Server-Konfigurations-Manager verwenden.

Weitere Informationen zum Ändern des benutzerkontenpools finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

##  <a name="bkmk_ManagingMemory"></a> Verwalten von externen Skriptprozesse belegter Arbeitsspeicher

Standardmäßig sind die externen Skript-Laufzeiten für Machine Learning auf nicht mehr als 20 % des gesamten Arbeitsspeichers beschränkt. Es hängt von Ihrem System, aber im Allgemeinen möglicherweise dieses Limit nicht schwerwiegenden Machine Learning-Aufgaben wie das Trainieren eines Modells oder das Vorhersagen von vielen Zeilen mit Daten. 

Administratoren kann dieses Limit erhöhen, um Machine Learning zu unterstützen. Wenn Sie dies tun, müssen Sie möglicherweise reduzieren die reservierten Umfang an Arbeitsspeicher für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder für andere Dienste. Sie sollten auch berücksichtigen, mit dem Resource Governor um einen externen Ressourcenpool bzw.-Pools, zu definieren, damit Sie bestimmte Ressourcenpools für R oder Python-Projekte zuordnen können.

Weitere Informationen finden Sie unter [Ressourcenkontrolle für Machine Learning](../../advanced-analytics/r/resource-governance-for-r-services.md).


## <a name="bkmk_Launchpad"></a>Ändern des Launchpad-Dienstkontos

Eine Separate [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Dienst erstellt und für jede Instanz, die auf dem Sie die Machine learning-Dienste konfiguriert haben.

Launchpad ist standardmäßig so konfiguriert, dass es mit dem Konto „NT Service\MSSQLLaunchpad“ ausgeführt wird, das mit allen erforderlichen Berechtigungen für das Ausführen von R-Skript bereitgestellt wird. Aber wenn Sie dieses Konto ändern, das Launchpad möglicherweise nicht gestartet oder SQL Server-Instanz zuzugreifen, in dem externe Skripts ausgeführt werden soll.

Wenn Sie das Dienstkonto ändern, achten Sie darauf, dass Sie die Anwendung **Local Security Policy** (Lokale Sicherheitsrichtlinie) verwenden und die Berechtigungen in jedem Dienstkonto aktualisieren, sodass sie folgende Berechtigungen enthalten:

+ Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)
+ Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)
+ Anmelden als Dienst (SeServiceLogonRight)
+ Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)

Weitere Informationen zu erforderlichen Berechtigungen für das Ausführen von SQL Server-Diensten finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

##  <a name="bkmk_ChangingConfig"></a> Ändern der erweiterten Dienstoptionen

In frühen Versionen von SQL Server 2016 R Services, können Sie einige Eigenschaften des Diensts ändern, indem Sie die Bearbeitung der [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Konfigurationsdatei. 

Allerdings wird diese Datei nicht mehr zum Ändern von Konfigurationen. Es wird empfohlen, dass Sie SQL Server-Konfigurations-Manager, um die Auswirkungen von Änderungen an der Dienstkonfiguration, wie z. B. das Dienstkonto und die Anzahl von Benutzern verwenden.

**So ändern Sie den Launchpad-Konfiguration**

1. Öffnen Sie den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md). 
2. Mit der rechten Maustaste in SQL Server Launchpad, und wählen Sie **Eigenschaften**.

    + Um das Dienstkonto zu ändern, klicken Sie auf die **anmelden** Registerkarte.

    + Um die Anzahl von Benutzern zu erhöhen, klicken Sie auf die **erweitert** Registerkarte.


**So ändern Sie die Einstellungen zum Debuggen**

Einige Eigenschaften können nur geändert werden, mithilfe Launchpads-Konfigurationsdatei, die sich in selteneren Fällen, z. B. Debuggen hilfreich sein kann. Die Konfigurationsdatei wird erstellt, während der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einrichten und in der Standardeinstellung als nur-Text-Datei am folgenden Speicherort gespeichert: `<instance path>\binn\rlauncher.config`

Sie müssen Administrator auf dem Computer sein, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, um diese Datei ändern zu können. Für die Bearbeitung der Datei wird empfohlen, dass Sie eine Sicherungskopie erstellen, bevor Sie Änderungen speichern.

Die folgende Tabelle enthält die erweiterten Einstellungen für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], mit den zulässigen Werten. 

|**Einstellungsname**|**Typ**|**Beschreibung**|
|----|----|----|
|AUFTRAG\_BEREINIGUNG\_ON\_BEENDEN|Integer |Dies ist eine interne Einstellung – ändern Sie diesen Wert nicht. </br></br>Gibt an, ob es sich bei der temporären Arbeitsordner erstellt für jede externe Common Language Runtime-Sitzung bereinigt werden soll, nachdem die Sitzung abgeschlossen ist. Diese Einstellung ist beim Debuggen nützlich. </br></br>Unterstützte Werte sind **0** (deaktiviert) oder **1** (aktiviert). </br></br>Der Standardwert ist 1, die Bedeutung von Protokolldateien beim Beenden entfernt.|
|ABLAUFVERFOLGUNG\_EBENE|Integer |Konfiguriert den Ausführlichkeitsgrad der Ablaufverfolgung von MSSQLLAUNCHPAD zu Debugzwecken an. Dies wirkt sich die Ablaufverfolgungsdateien im Pfad durch die Einstellung LOG_DIRECTORY angegeben. </br></br>Unterstützte Werte sind: **1** (Fehler), **2** (Leistung), **3** (Warnung), **4** (Informationen). </br></br>Der Standardwert ist 1, d. h. nur Ausgabe von Warnungen.|

Alle Einstellungen haben die Form eines Schlüssel-Wert-Paars, bei dem jede Einstellung in einer separaten Zeile enthalten ist. Klicken Sie z. B., um das Level der Ablaufverfolgung zu ändern, hinzufügen die Zeile `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Siehe auch

[Überlegungen zur Sicherheit](security-considerations-for-the-r-runtime-in-sql-server.md)
