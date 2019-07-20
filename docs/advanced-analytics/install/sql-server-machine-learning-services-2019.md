---
title: Unterschiede in SQL Server 2019
description: Erfahren Sie mehr über die Neuerungen für R-und python-SQL Server Machine Learning-Erweiterungen in der SQL Server 2019-Vorschauversion.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8996d47c58841f668813c8ff344683150e456fb3
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344996"
---
# <a name="differences-in-sql-server-machine-learning-services-installation-in-sql-server-2019"></a>Unterschiede bei der Installation von SQL Server Machine Learning Services in SQL Server 2019  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Unter Windows ändert SQL Server 2019-Setup den Isolations Mechanismus für externe Prozesse. Diese Änderung ersetzt lokale workerkonten durch [appcontainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation), eine Isolations Technologie für Client Anwendungen, die unter Windows ausgeführt werden. 

Aufgrund der Änderung sind keine bestimmten Aktions Elemente für den Administrator vorhanden. Auf einem neuen oder aktualisierten Server folgen alle externen Skripts und Code, die von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ausgeführt werden, automatisch dem neuen Isolations Modell. 

Zusammengefasst sind die wichtigsten Unterschiede in dieser Version:

+ Lokale Benutzerkonten unter der **eingeschränkten SQL-Benutzergruppe (sqlrusergroup)** werden nicht mehr erstellt oder zum Ausführen externer Prozesse verwendet. Diese werden durch appcontainers ersetzt.
+ Die **sqlrusergroup** -Mitgliedschaft wurde geändert. Anstelle mehrerer lokaler Benutzerkonten besteht die Mitgliedschaft nur aus dem SQL Server-Launchpad-Dienst Konto. R-und python-Prozesse werden nun unter der Launchpad-Dienst Identität ausgeführt, isoliert durch appcontainers.

Obwohl sich das Isolations Modell geändert hat, bleiben der Installations-Assistent und die Befehlszeilenparameter in SQL Server 2019 unverändert. Hilfe zur Installation finden Sie unter [Install SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md).

## <a name="about-appcontainer-isolation"></a>Informationen zur appcontainer-Isolation

In früheren Versionen enthielt **sqlrusergroup** einen Pool von lokalen Windows-Benutzerkonten (MSSQLSERVER00-MSSQLSERVER20), die zum isolieren und Ausführen externer Prozesse verwendet werden. Wenn ein externer Prozess erforderlich war, hat SQL Server-Launchpad Dienst ein verfügbares Konto, das zum Ausführen eines Prozesses verwendet wird. 

In SQL Server 2019 werden lokale workerkonten nicht mehr von Setup erstellt. Stattdessen wird die Isolation durch [appcontainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)erreicht. Wenn ein eingebettetes Skript oder Code in einer gespeicherten Prozedur oder Abfrage erkannt wird, ruft SQL Server zur Laufzeit Launchpad mit einer Anforderung für ein Erweiterungs spezifisches Start Programm auf. Launchpad Ruft die entsprechende Laufzeitumgebung in einem Prozess unter seiner Identität auf und instanziiert einen appcontainer, um ihn zu enthalten. Diese Änderung ist von Vorteil, da die Verwaltung lokaler Konten und Kenn Wörter nicht mehr erforderlich ist. Außerdem können Sie bei Installationen, bei denen lokale Benutzerkonten nicht zulässig sind, diese Funktion jetzt verwenden.

Gemäß der Implementierung durch SQL Server sind appcontainers ein interner Mechanismus. Obwohl im Prozess Monitor keine physischen Beweise von appcontainers angezeigt werden, können Sie diese in ausgehenden Firewallregeln finden, die vom-Setup erstellt wurden, um zu verhindern, dass Prozesse Netzwerk Aufrufe durchführen.

## <a name="firewall-rules-created-by-setup"></a>Von Setup erstellte Firewallregeln

Standardmäßig deaktiviert SQL Server ausgehende Verbindungen durch Erstellen von Firewallregeln. In der Vergangenheit basieren diese Regeln auf lokalen Benutzerkonten, in denen Setup eine ausgehende Regel für **sqlrusergroup** erstellt hat, die den Netzwerk Zugriff auf die Mitglieder verweigert hat (jedes Workerkonto war als lokales Prinzip für die rule_ aufgeführt. 

Im Rahmen der Umstellung auf appcontainers gibt es neue Firewallregeln, die auf appcontainer-SIDs basieren: eine für jeden der 20 appcontainers, die durch SQL Server-Setup erstellt wurden. Benennungs Konventionen für den Namen der Firewallregel sind das **Blockieren des Netzwerk Zugriffs für appcontainer-00 in SQL Server Instanz MSSQLSERVER**, wobei 00 die Nummer von appcontainer (standardmäßig 00-20) und MSSQLSERVER der Name der SQL Server Instanz ist. 

> [!Note]
> Wenn Netzwerk Aufrufe erforderlich sind, können Sie die ausgehenden Regeln in der Windows-Firewall deaktivieren.

## <a name="program-file-permissions"></a>Programmdatei Berechtigungen

Wie bei früheren Releases stellt **sqlrusergroup** weiterhin Lese-und Ausführungs Berechtigungen für ausführbare Dateien in den SQL Server **Binn**-, **R_SERVICES**-und **PYTHON_SERVICES** -Verzeichnissen bereit. In dieser Version ist das einzige Mitglied von **sqlrusergroup** das SQL Server-Launchpad Dienst Konto.  Wenn der Launchpad-Dienst eine R-oder python-Ausführungsumgebung startet, wird der Prozess als Launchpad-Dienst ausgeführt.

## <a name="implied-authentication"></a>Implizite Authentifizierung

Wie zuvor ist noch eine weitere Konfiguration für die *implizite Authentifizierung* erforderlich, wenn Skripts oder Code eine Verbindung mit SQL Server mithilfe der vertrauenswürdigen Authentifizierung zum Abrufen von Daten oder Ressourcen herstellen müssen. Die zusätzliche Konfiguration umfasst das Erstellen einer Daten Bank Anmeldung für " **sqlrusergroup**", deren einziges Mitglied jetzt das einzelne SQL Server-Launchpad Dienst Konto anstelle mehrerer workerkonten ist. Weitere Informationen zu diesem Task finden Sie unter [Hinzufügen von sqlrusergroup als Datenbankbenutzer](../security/create-a-login-for-sqlrusergroup.md).


## <a name="symbolic-link-created-by-setup"></a>Symbolische Verknüpfung erstellt durch Setup

Eine symbolische Verknüpfung wird mit dem aktuellen Standard **R_SERVICES** und **PYTHON_SERVICES** als Teil der SQL Server-Installation erstellt. Wenn Sie diesen Link nicht erstellen möchten, besteht eine Alternative darin, der Hierarchie, die zum Ordner führt, die Leseberechtigung "alle Anwendungspakete" zu erteilen.


## <a name="see-also"></a>Siehe auch

+ [Installieren von SQL Server Machine Learning Services unter Windows](sql-machine-learning-services-windows-install.md)

+ [Installieren von SQL Server 2019 Machine Learning Services unter Linux](../../linux/sql-server-linux-setup-machine-learning.md)
