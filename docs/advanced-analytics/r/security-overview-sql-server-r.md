---
title: Sicherheit für SQL Server-Machine Learning und R | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c04670464d23f0951a957df945a2e81b817ae134
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889186"
---
# <a name="security-for-sql-server-machine-learning-and-r"></a>Sicherheit für SQL Server-Machine Learning und R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, die Sicherheitsarchitektur, die zum Herstellen der Verbindung die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Datenbank-Engine und zugehörige Komponenten mit der R-Laufzeit. Beispiele für den Sicherheitsprozess werden für diesen verbreiteten Szenarien zum Verwenden von R in einer unternehmensumgebung bereitgestellt:

+ Ausführen von RevoScaleR-Funktionen in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] aus einem Data Science-Client
+ Ausführen von R direkt aus [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] mithilfe von gespeicherten Prozeduren

## <a name="security-overview"></a>Übersicht über die Sicherheit

Ein [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Anmeldung oder Windows-Benutzerkonto ist erforderlich, um die Ausführung von R-Skripts, die SQL Server-Daten verwenden, oder, die mit SQL Server als Compute Context ausgeführt. Diese Anforderung gilt für beide [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] und SQL Server 2017 [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)].

Gibt das Konto Anmeldenamen oder Benutzer an die *Sicherheitsprinzipal*, die möglicherweise mehrere Ebenen des Zugriffs, je nach den Anforderungen der R-Skript:

+ Berechtigung zum Zugriff auf die Datenbank, in dem der R aktiviert ist
+ Berechtigungen zum Lesen von Daten aus gesicherten Objekten wie Tabellen
+ Die Möglichkeit zum Schreiben neuer Daten in eine Tabelle, z. B. ein Modell oder Bewertungsergebnisse
+ Die Möglichkeit zum Erstellen neuer Objekte, z. B. Tabellen, gespeicherte Prozeduren, die R-Skript verwenden oder benutzerdefinierte Funktionen, verwenden von R-Auftrag
+ Das Recht, neue Pakete zu installieren, auf dem SQL Server-Computer, oder Verwenden von R-Pakete, die für eine Gruppe von Benutzern bereitgestellt. 

Aus diesem Grund jede Person, die R-Code mithilfe von führt [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Kontext muss wie die Ausführung einer Anmeldung in der Datenbank zugeordnet werden. Sicherheit von SQL Server ist es im Allgemeinen am einfachsten erstellen Sie Rollen, um die Sätze von Berechtigungen, verwalten und diesen Rollen Benutzer zuweisen, statt Berechtigungen einzeln festzulegen. 

Als Beispiel wird davon ausgegangen, dass Sie R-Code, der auf Ihrem Laptop ausgeführt wird erstellt, und Sie diesen Code ausführen möchten [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Dies ist möglich, nur dann, wenn diese Bedingungen erfüllt sind:

+ Die Datenbank lässt Remoteverbindungen zu.
+ Eine SQL-Anmeldung mit dem Namen und dem Kennwort, die Sie im R-Code verwendet haben, wurde dem [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] auf Instanzebene hinzugefügt. Wenn Sie stattdessen die integrierte Windows-Authentifizierung verwenden, muss der in der Verbindungszeichenfolge angegebene Windows-Benutzer der Instanz als Benutzer hinzugefügt werden.
+ Die SQL-Anmeldung oder der Windows-Benutzer benötigen die Berechtigung zum Ausführen externer Skripts. Diese Berechtigung kann in der Regel nur von einem Datenbankadministrator hinzugefügt werden.
+ Die SQL-Anmeldung oder der Windows-Benutzer muss als Benutzer mit entsprechenden Berechtigungen in jeder Datenbank hinzugefügt werden, in der der R-Auftrag eine dieser Operationen ausführt:
    + Abrufen von Daten
    + Schreiben oder Aktualisieren von Daten 
    + Neue Objekte wie Tabellen oder gespeicherte Prozeduren erstellen

Nach der Anmeldung oder der Windows-Benutzerkonto bereitgestellt und die erforderlichen Berechtigungen zugewiesen wurde, können Sie R-Code ausführen, auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] mithilfe eines R-Datenquellenobjekts oder durch Aufrufen einer gespeicherten Prozedur. R wird jedes Mal, wenn vom gestartet [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], die Sicherheit der Datenbank-Engine Ruft den Sicherheitskontext des Benutzers, der die R-Auftrag gestartet wurde oder die gespeicherte Prozedur ausgeführt und verwaltet die Zuordnungen des Benutzers oder der Anmeldung zu sicherungsfähigen Objekten ab. 

Daher müssen alle R-Aufträge, die von einem Remoteclient aus initiiert werden die Anmeldenamen oder Benutzer als Teil der Verbindungszeichenfolge angeben.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interaktion von [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] -Sicherheit und Launchpad-Sicherheit

Wenn ein R-Skript im Kontext des [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Computers ausgeführt wird, ruft der [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]-Dienst ein verfügbares Workerkonto (ein lokales Benutzerkonto) aus einem Pool von Workerkonten für externe Prozesse ab und verwendet dieses Workerkonto für die verknüpften Aufgaben. 

Wenn Sie beispielsweise unter Ihren Windows-Domänenanmeldeinformationen einen R-Auftrag starten, wird Ihr Konto möglicherweise dem Launchpad-Workerkonto *SQLRUser01* zugeordnet.

Nach der Zuordnung zu einem Workerkonto erstellt [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ein Benutzertoken, das zum Starten von Prozessen verwendet wird. 

Wenn alle [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Vorgänge abgeschlossen sind, wird das Benutzerworkerkonto als frei markiert und an den Pool zurückgegeben.

Weitere Informationen zum Dienst finden Sie unter [Erweiterungsframework](../concepts/extensibility-framework.md). 

### <a name="implied-authentication"></a>Implizite Authentifizierung

**Implizite Authentifizierung** ist der Begriff für den Prozess, unter dem SQL Server erhält der Benutzer die, Anmeldeinformationen und führt dann alle externen Skript-Aufgaben für den Benutzer, sofern der Benutzer hat die richtigen Berechtigungen in der Datenbank. Implizite Authentifizierung ist besonders wichtig, wenn das R-Skript einen ODBC-Aufruf außerhalb der SQL Server-Datenbank vornehmen muss. Der Code kann z. B. eine kürzere Liste von Faktoren aus einer Tabelle oder einer anderen Quelle abgerufen werden.

Für solche Loopback-Aufrufe erfolgreich ausgeführt werden kann muss die Gruppe, die die workerkonten, SQLRUserGroup enthält "Lokal anmelden zulassen" berechtigt. Klicken Sie in der Standardeinstellung dieses Recht allen neuen lokalen Benutzern erteilt, aber in einigen Organisationen möglicherweise strengere Gruppenrichtlinien erzwungen werden.

![Implizite Authentifizierung für R](media/implied-auth-rsql.png)

## <a name="security-of-worker-accounts"></a>Sicherheit von workerkonten

Die Zuordnung eines externen Windows-Benutzer oder eine gültige SQL-Anmeldung zu einem workerkonto gilt nur für die Lebensdauer der SQL-Abfrage, die R-Skript ausgeführt wird.

Parallele Abfragen von derselben Anmeldung werden demselben Benutzerworkerkonto zugeordnet.

Die Verzeichnisse, die für die Prozesse verwendet werden, werden von [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] mit RLauncher verwaltet, und der Zugriff auf die Verzeichnisse ist eingeschränkt. Das Workerkonto kann nicht auf Dateien in Ordnern über dem eigenen zugreifen, kann aber untergeordnete Elemente des Arbeitsordners der Sitzung, der für die SQL-Abfrage mit dem R-Skript erstellt wurde, lesen, schreiben oder löschen.

Weitere Informationen dazu, wie Sie die Anzahl der workerkonten, Kontonamen oder Kennwörter ändern können, finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

## <a name="security-isolation-for-multiple-external-scripts"></a>Sicherheitsisolation für mehrere externe Skripts

Der Isolationsmechanismus basiert auf physischen Benutzerkonten. Da Satellitenprozesse für eine bestimmte Sprachlaufzeit gestartet werden, verwendet jede Satellitenaufgabe das von [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] angegebene Workerkonto. Wenn für eine Aufgabe mehrere Satelliten erforderlich sind, wie z.B. bei parallelen Abfragen, wird ein einziges Workerkonto für alle zusammenhängenden Aufgaben verwendet.

Kein Workerkonto kann Dateien finden oder bearbeiten, die von anderen Workerkonten verwendet werden.
 
Wenn Sie Administrator auf dem Computer sind, können Sie die Verzeichnisse anzeigen, die für jeden Prozess erstellt wurden. Jedes Verzeichnis wird durch die Sitzungs-GUID identifiziert.

## <a name="see-also"></a>Siehe auch

[Übersicht über die Architektur für SQL Server Machine learning](../../advanced-analytics/r/architecture-overview-sql-server-r.md)
