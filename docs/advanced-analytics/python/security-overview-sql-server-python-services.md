---
title: Übersicht über die Sicherheit für Python in SQL Server-Machine Learning | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a33701283635327fcaac4a9629cb02044b30dda8
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890056"
---
# <a name="security-overview-for-python-in-sql-server-machine-learning"></a>Übersicht über die Sicherheit für Python in SQL Server-Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Thema wird beschrieben, die Sicherheitsarchitektur, die zum Herstellen der Verbindung die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Datenbank-Engine und Python-Komponenten. Beispiele für den Sicherheitsprozess werden für zwei gängige Szenarien bereitgestellt: die Ausführung von Python in SQL Server mithilfe einer gespeicherten Prozedur, und die Ausführung von Python mit SQL Server als dem entfernten computekontext.

## <a name="security-overview"></a>Übersicht über die Sicherheit

Ein [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Anmeldung oder Windows-Benutzerkonto ist erforderlich, um die Python-Skript in SQL Server ausführen. Diese *Sicherheitsprinzipale* verwaltet werden, auf der Instanz- und Datenbankebene, und identifizieren Sie Benutzer, die über die Berechtigung zum Verbinden mit der Datenbank, zu lesen und Schreiben von Daten oder Datenbankobjekte wie Tabellen oder gespeicherte Prozeduren erstellen. Darüber hinaus müssen Benutzer, die Python-Skript ausführen, über die Berechtigung zum Ausführen externer Skripts auf Datenbankebene verfügen.

Selbst Benutzer, die in einem externen Tool Python verwenden müssen, ein Anmeldename oder ein Konto in der Datenbank zugeordnet werden, wenn der Benutzer zum Ausführen von Python Code in der Datenbank, oder den Zugriff auf Datenbankobjekte und Daten muss. Gibt an, ob das Python-Skript, das aus einem Data Science-Remoteclient gesendet wird, oder Schritte bei der Verwendung einer gespeicherten T-SQL-Prozedur, sind die gleichen Berechtigungen erforderlich.

Nehmen wir beispielsweise an, dass Sie erstellt haben, ein Python-Skript, das auf Ihrem Laptop ausgeführt wird, und Sie diesen Code ausführen möchten [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Sie müssen sicherstellen, dass die folgenden Bedingungen erfüllt sind:

+ Die Datenbank lässt Remoteverbindungen zu.
+ Die SQL-Anmeldung oder das Windows-Konto, die Sie für den Datenbankzugriff verwendet wurde die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] auf Instanzebene.
+ Der SQL-Anmeldung oder dem Windows-Benutzer muss die Berechtigung zum Ausführen externer Skripts erteilt werden. Diese Berechtigung kann in der Regel nur von einem Datenbankadministrator hinzugefügt werden.
+ Die SQL-Anmeldung oder der Windows-Benutzer muss als Benutzer mit entsprechenden Berechtigungen in jeder Datenbank hinzugefügt werden, bei denen das Python-Skript für diese Vorgänge ausführt:
    + Abrufen von Daten
    + Schreiben oder Aktualisieren von Daten
    + Neue Objekte wie Tabellen oder gespeicherte Prozeduren erstellen

Nach der Anmeldung oder der Windows-Benutzerkonto bereitgestellt und die erforderlichen Berechtigungen zugewiesen wurde, können Sie die Python-Code ausführen, auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] mithilfe von bereitgestellten Datenquellenobjekte der **Revoscalepy** -Bibliothek, oder durch Aufrufen einer gespeicherten Prozedur, die Python-Skript enthält.

Jedes Mal, wenn ein Python-Skript gestartet wird [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], die Sicherheit der Datenbank-Engine Ruft den Sicherheitskontext des Benutzers, der der Auftrag gestartet, und verwaltet die Zuordnungen des Benutzers oder der Anmeldung zu sicherungsfähigen Objekten ab.

Aus diesem Grund müssen alle Python-Skripts, die von einem Remoteclient aus initiiert werden die Anmeldenamen oder Benutzer Informationen als Teil der Verbindungszeichenfolge angeben.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interaktion von [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] -Sicherheit und Launchpad-Sicherheit

Wenn ein Python-Skript ausgeführt wird, im Rahmen der [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Computer, die [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Dienst Ruft ein verfügbares workerkonto (ein lokales Benutzerkonto) aus einem Pool von workerkonten für externe Prozesse ab und verwendet dieses workerkonto, Führen Sie die zugehörigen Aufgaben.

Nehmen wir beispielsweise an, dass Sie Ihren Windows-Domänenanmeldeinformationen ein Python-Skript starten. SQL Server ruft Ihre Anmeldeinformationen ab und ordnet die Aufgabe auf eine verfügbare Launchpad-workerkonto, z. B. *SQLRUser01*.

> [!NOTE]
> Der Name der Gruppe von workerkonten ist identisch, unabhängig davon, ob Sie R- oder Python verwenden. Allerdings wird eine separate Gruppe für jede Instanz erstellt, in dem Sie alle externen Sprache aktivieren.

Nach der Zuordnung zu einem Workerkonto erstellt [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ein Benutzertoken, das zum Starten von Prozessen verwendet wird. 

Wenn alle [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Vorgänge abgeschlossen sind, wird das Benutzerworkerkonto als frei markiert und an den Pool zurückgegeben.

Weitere Informationen zum Dienst finden Sie unter [Erweiterungsframework](../concepts/extensibility-framework.md).

### <a name="implied-authentication"></a>Implizite Authentifizierung

**Implizite Authentifizierung** ist der Begriff für den Prozess, unter dem SQL Server erhält der Benutzer die, Anmeldeinformationen und führt dann alle externen Skript-Aufgaben für den Benutzer, sofern der Benutzer hat die richtigen Berechtigungen in der Datenbank. Implizite Authentifizierung ist besonders wichtig, wenn das Python-Skript einen ODBC-Aufruf außerhalb der SQL Server-Datenbank vornehmen muss. Der Code kann z. B. eine kürzere Liste von Faktoren aus einer Tabelle oder einer anderen Quelle abgerufen werden.

Für solche Loopback-Aufrufe erfolgreich ausgeführt werden kann muss die Gruppe, die die workerkonten, SQLRUserGroup enthält "Lokal anmelden zulassen" berechtigt. Klicken Sie in der Standardeinstellung dieses Recht allen neuen lokalen Benutzern erteilt, aber in einigen Organisationen möglicherweise strengere Gruppenrichtlinien erzwungen werden.

![Implizite Authentifizierung für R](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>Sicherheit von workerkonten

Die Zuordnung eines externen Windows-Benutzer oder eine gültige SQL-Anmeldung zu einem workerkonto gilt nur für die Lebensdauer des SQL Prozedur gespeicherten, die das Python-Skript ausführt.

Parallele Abfragen von derselben Anmeldung werden demselben Benutzerworkerkonto zugeordnet.

Die Verzeichnisse, die für die Prozesse verwendet werden vom verwaltet die [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], und Verzeichnisse zugreifen. Für Python führt PythonLauncher diese Aufgabe. Jedes einzelnen workerkonto ist beschränkt, in einem eigenen Ordner und Dateien in Ordnern über eine eigene kann nicht zugegriffen werden kann. Allerdings kann das workerkonto lesen, schreiben oder löschen die untergeordneten Elemente in der Sitzung Arbeitsordner an, der erstellt wurde.

Weitere Informationen dazu, wie Sie die Anzahl der workerkonten, Kontonamen oder Kennwörter ändern können, finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Sicherheitsisolation für mehrere externe Skripts

Der Isolationsmechanismus basiert auf physischen Benutzerkonten. Da Satellitenprozesse für eine bestimmte Sprachlaufzeit gestartet werden, verwendet jede Satellitenaufgabe das von [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] angegebene Workerkonto. Wenn für eine Aufgabe mehrere Satelliten erforderlich sind, wie z.B. bei parallelen Abfragen, wird ein einziges Workerkonto für alle zusammenhängenden Aufgaben verwendet.

Kein Workerkonto kann Dateien finden oder bearbeiten, die von anderen Workerkonten verwendet werden.

Wenn Sie Administrator auf dem Computer sind, können Sie die Verzeichnisse anzeigen, die für jeden Prozess erstellt wurden. Jedes Verzeichnis wird durch die Sitzungs-GUID identifiziert.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Architektur](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
