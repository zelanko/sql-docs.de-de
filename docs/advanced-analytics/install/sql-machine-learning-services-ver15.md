---
title: Unterschiede in der SQLServer 2019 – SQL Server Machine Learning-Dienste
description: Erfahren Sie Neuigkeiten für R und Python SQL Server Machine Learning-Erweiterungen in der Vorschauversion von SQL Server-2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 43d427129cae773fc17a0d73f57a26144b7cd09f
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454516"
---
# <a name="differences-in-sql-server-machine-learning-services-installation-in-sql-server-2019"></a>Unterschiede bei der Installation von SQL Server Machine Learning Services in SQL Server-2019  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Auf Windows ändert Setup für SQL Server-2019 der Isolationsmechanismus für externe Prozesse. Diese Änderung ersetzt die lokalen Konten mit [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation), eine Isolation-Technologie für Clientanwendungen, die unter Windows. 

Es gibt keine bestimmte Aktion-Elemente für den Administrator aufgrund der Änderung. Auf einem neuen oder aktualisierten Server, alle externen Skripts und Code, der ausgeführt wird, von [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) führen Sie das neue Isolationsmodell automatisch. 

Zusammengefasst werden, sind die wichtigsten Unterschiede in dieser Version:

+ Lokale Benutzerkonten unter **eingeschränkten SQL-Benutzergruppe (SQLRUserGroup)** nicht mehr erstellt oder zum Ausführen von externer Prozessen verwendet werden. AppContainers ersetzen Sie sie.
+ **SQLRUserGroup** Mitgliedschaft hat sich geändert. Anstatt mehrere lokale Benutzerkonten besteht aus Mitgliedschaft nur das SQL Server Launchpad-Dienstkonto. R und Python-Prozesse werden nun die Launchpad Dienstidentität über AppContainers isoliert.

Obwohl das Modell der Isolation geändert wurde, bleibt die Installationsparameter-Assistent und über die Befehlszeile in SQL Server-2019. Hilfe zur Installation finden Sie unter [Installieren von SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md).

## <a name="about-appcontainer-isolation"></a>Zur AppContainer-isolation

In früheren Versionen **SQLRUserGroup** enthalten einen Pool von lokalen Windows-Benutzerkonten (MSSQLSERVER00-MSSQLSERVER20) zum Isolieren und Ausführen von externen Prozessen verwendet. Wenn ein externer Prozess erforderlich war, wäre SQL Server Launchpad-Dienst eine verfügbare berücksichtigen und verwenden, um ein Prozess ausgeführt werden. 

In SQL Server-2019 erstellt Setup nicht mehr lokale Konten. Isolation erfolgt stattdessen über [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Zur Laufzeit bei eingebetteten Skripts oder Code in einer gespeicherten Prozedur oder Abfrage erkannt wird, ruft der SQL Server Launchpad mit einer Anforderung für ein Startprogramm spezifisch. Launchpad Ruft die entsprechenden Common Language Runtime-Umgebung in einem Prozess unter seiner Identität und instanziiert einen AppContainer enthält. Diese Änderung ist nützlich, da lokale Konto und Kennwort-Verwaltung nicht mehr benötigt wird. Für Installationen, in denen lokale Benutzerkonten gelten, verboten sind, bedeutet auch, Entfernung der Abhängigkeit Konto Lokaler Benutzer, dass Sie jetzt dieses Feature verwenden können.

Gemäß der Implementierung von SQL Server sind AppContainers einen internen Mechanismus. Während Sie physische Beweise des AppContainers im Monitor "Prozess" nicht angezeigt werden, finden Sie sie in Firewallregeln für ausgehenden Datenverkehr von Setup um zu verhindern, dass Prozesse Aufrufe Netzwerk erstellt wurde.

## <a name="firewall-rules-created-by-setup"></a>Firewall-Regeln, die von Setup erstellt wurde

SQL Server deaktiviert standardmäßig die ausgehende Verbindungen durch Erstellen von Firewallregeln. In der Vergangenheit basieren auf den lokalen Benutzerkonten eingerichtet, in denen eine ausgehende Regel für hat diese Regeln **SQLRUserGroup** , der Netzwerkzugriff Membern verweigert (jedes workerkonto wurde als lokale Prinzip unterliegen der Rule_ aufgeführt. 

Im Rahmen der Umstieg auf AppContainers, es gibt neue Firewallregeln, die auf Grundlage der AppContainer-SIDs: eine für jede der 20 AppContainers von SQL Server-Setup erstellt. Benennungskonventionen für Name der Firewallregel sind **in SQL Server-Instanz MSSQLSERVER Blockieren des Netzwerkzugriffs für AppContainer-00**, wobei 00 die Anzahl von App-Container (00-20, in der Standardeinstellung ist), und MSSQLSERVER der Name des SQL ist- Server-Instanz. 

> [!Note]
> Wenn Netzwerkaufrufe erforderlich sind, können Sie ausgehenden Regeln in der Windows-Firewall deaktivieren.

## <a name="program-file-permissions"></a>Programm-Dateiberechtigungen

Wie bei früheren Versionen der **SQLRUserGroup** ermöglichen Lese- und Ausführungsberechtigungen für ausführbare Dateien in der SQL Server weiterhin **Binn**, **R_SERVICES**, und  **PYTHON_SERVICES** Verzeichnisse. In dieser Version das einzige Mitglied **SQLRUserGroup** ist das SQL Server Launchpad-Dienstkonto.  Wenn Launchpad-Dienst eine ausführungsumgebung für R oder Python gestartet wird, wird der Prozess als LaunchPad-Dienst ausgeführt.

## <a name="implied-authentication"></a>Implizite Authentifizierung

Wie zuvor zusätzliche Konfiguration für noch erforderlich ist *implizite Authentifizierung* in Fällen, in denen Skripts oder Code für die Verbindung wieder nach SQL Server verwenden vertrauenswürdige Authentifizierung zum Abrufen von Daten oder Ressourcen. Die folgende zusätzliche Konfiguration umfasst das Erstellen eines datenbankanmeldenamens für **SQLRUserGroup**, dessen einzige Member ist jetzt die einzelnen SQL Server Launchpad-Dienstkonto anstelle mehrerer Konten. Weitere Informationen zu diesem Task finden Sie unter [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../security/create-a-login-for-sqlrusergroup.md).


## <a name="symbolic-link-created-by-setup"></a>Symbolische Verknüpfung, die von Setup erstellt wurde

Eine symbolische Verknüpfung wird erstellt, um die aktuelle Standardeinstellung **R_SERVICES** und **PYTHON_SERVICES** als Teil des SQL Server-Setup. Wenn Sie nicht diesen Link erstellen möchten, ist eine Alternative, der Hierarchie, zu dem Ordner "alle Anwendungspakete" Leseberechtigung gewähren.


## <a name="see-also"></a>Siehe auch

+ [Installieren von SQL Server Machine Learning-Dienste auf Windows](sql-machine-learning-services-windows-install.md)

+ [Installieren von SQL Server 2019-Machine-Learning-Dienste unter Linux](../../linux/sql-server-linux-setup-machine-learning.md)
