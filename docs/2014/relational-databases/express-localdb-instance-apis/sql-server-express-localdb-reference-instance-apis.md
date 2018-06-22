---
title: SQL Server Express LocalDB Instanz-API-Referenz | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ebafb4bf20d84d2a570af7225e26c09e9089825e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049022"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a>SQL Server Express LocalDB-Instanz-API-Verweis
  In der herkömmlichen, dienstbasierten SQL Server-Welt sind einzelne auf einem einzelnen Computer installierte SQL Server-Instanzen physisch getrennt. Das heißt, jede Instanz muss separat installiert und entfernt werden, verfügt über einen separaten Satz Binärdateien und wird unter einem separaten Dienstprozess ausgeführt. Der SQL Server-Instanzname wird verwendet, um anzugeben, mit welcher SQL Server-Instanz der Benutzer eine Verbinden herstellen möchte.  
  
 Die SQL Server Express LocalDB-Instanz-API verwendet ein vereinfachtes "leichtes" Instanzmodell. Obwohl einzelne LocalDB-Instanzen auf dem Datenträger und in der Registrierung getrennt sind, verwenden sie denselben Satz freigegebener LocalDB-Binärdateien. Darüber hinaus verwendet LocalDB keine Dienste. LocalDB-Instanzen werden bei Bedarf durch LocalDB-Instanz-API-Aufrufe gestartet. In LocalDB wird der Instanzname verwendet, um anzugeben, mit welcher LocalDB-Instanz der Benutzer arbeiten will.  
  
 Eine LocalDB-Instanz gehört immer einem einzelnen Benutzer und ist nur im Kontext dieses Benutzers sichtbar und aufrufbar, es sei denn, die Instanzfreigabe wird aktiviert.  
  
 Obwohl LocalDB-Instanzen den herkömmlichen SQL Server-Instanzen technisch nicht entsprechen, ist ihre vorgesehene Verwendung ähnlich. Sie werden aufgerufen, *Instanzen* um diese Ähnlichkeit hervorzuheben und zu SQL Server-Benutzern eine intuitivere werden machen.  
  
 LocalDB unterstützt zwei Arten von Instanzen: automatische Instanzen (AI) und benannte Instanzen (BI). Der Bezeichner für eine LocalDB-Instanz ist der Instanzname.  
  
## <a name="automatic-localdb-instances"></a>Automatische LocalDB-Instanzen  
 Automatische LocalDB-Instanzen sind "öffentlich"; werden erstellt und automatisch für den Benutzer verwaltet. Sie können von allen Anwendungen verwendet werden. Eine automatische LocalDB-Instanz ist für jede Version von LocalDB vorhanden, die auf dem Computer des Benutzers installiert ist.  
  
 Automatische LocalDB-Instanzen stellen die nahtlose Instanzverwaltung bereit. Der Benutzer muss die Instanz nicht erstellen. Dies ermöglicht Benutzern die einfache Installation von Anwendungen und Migration auf andere Computer. Wenn auf dem Zielcomputer die angegebene Version von LocalDB installiert ist, ist die automatische LocalDB-Instanz für diese Version auch auf diesem Computer verfügbar.  
  
### <a name="automatic-instance-management"></a>Automatische Instanzverwaltung  
 Ein Benutzer muss keine automatische LocalDB-Instanz erstellen. Die Instanz wird bei ihrer ersten Verwendung verzögert erstellt, vorausgesetzt, dass die angegebene Version von LocalDB auf dem Computer des Benutzers verfügbar ist. Aus der Sicht des Benutzers ist die automatische Instanz immer vorhanden, wenn die LocalDB-Binärdateien vorhanden sind.  
  
 Andere Instanzverwaltungsvorgänge, z. B. Löschen, Freigabe und Freigabe aufheben, funktionieren auch für automatische Instanzen. Beim Löschen einer automatischen Instanz wird die Instanz effektiv zurückgesetzt, wodurch sie beim nächsten Startvorgang neu erstellt wird. Das Löschen einer automatischen Instanz ist möglicherweise erforderlich, wenn die Systemdatenbanken beschädigt sind.  
  
### <a name="automatic-instance-naming-rules"></a>Benennungsregeln für automatische Instanzen  
 Automatische LocalDB-Instanzen haben ein besonderes Muster für den Instanznamen, der zu einem reservierten Namespace gehört. Dies ist zur Verhinderung von Namenskonflikten mit benannten LocalDB-Instanzen erforderlich.  
  
 Der Name der automatischen Instanzname ist die Versionsnummer der LocalDB-Baseline mit vorangestelltem "v". Dies sieht wie ein "v" und zwei Zahlen mit einem Punkt dazwischen aus, wie z. B. v11.0 oder V12.00.  
  
 Beispiele für ungültige automatische Instanznamen sind:  
  
-   11.0 ("v" am Anfang fehlt)  
  
-   v11 (Punkt und zweite Zahl der Versionsnummer fehlt)  
  
-   v11. (zweiten Zahl der Versionsnummer fehlt)  
  
-   v11.0.1.2 (Versionsnummer besteht aus mehr als zwei Teilen)  
  
## <a name="named-localdb-instances"></a>Benannte LocalDB-Instanzen  
 Benannte LocalDB-Instanzen sind "privat". Eine Instanz gehört einer Einzelanwendung, die für das Erstellen und Verwalten der Instanz zuständig ist. Benannte LocalDB-Instanzen bieten Isolierung und verbessern die Leistung.  
  
### <a name="named-instance-creation"></a>Erstellen einer benannten Instanz  
 Der Benutzer muss benannte Instanzen explizit über die LocalDB-Verwaltungs-API oder implizit für eine verwaltete Anwendung über die Datei app.config erstellen. Eine verwaltete Anwendung verwendet möglicherweise auch die API.  
  
 Jede benannte Instanz verfügt über eine zugeordnete LocalDB-Version. Das heißt, sie verweist auf einen angegebenen Satz LocalDB-Binärdateien. Die Version für die benannte Instanz wird während des Instanzerstellungsprozesses festgelegt.  
  
### <a name="named-instance-naming-rules"></a>Benennungsregeln für benannte Instanzen  
 Ein LocalDB-Instanzname kann bis zu 128 Zeichen aufweisen (die Grenze wird vom `sysname`-Datentyp festgelegt). Dies ist ein bedeutender Unterschied im Vergleich zu herkömmlichen SQL Server-Instanznamen, die auf NetBIOS-Namen mit 16 ASCII-Zeichen beschränkt sind. Die Ursache für diesen Unterschied ist, dass LocalDB Datenbanken als Dateien behandelt und daher dateibasierte Semantik impliziert. Daher ist es für Benutzer intuitiv, mehr Freiheit beim Auswählen der Instanznamen zu besitzen.  
  
 Ein LocalDB-Instanzname kann alle Unicode-Zeichen enthalten, die innerhalb der Dateinamenkomponente gültig sind. Ungültige Zeichen in einer Dateinamenkomponente gehören in der Regel die folgenden Zeichen: ASCII/Unicode-Zeichen 1 bis 31 sowie Anführungszeichen ("), kleiner als (\<), größer als (>), senkrechten Strich (|), Rücktaste (\b), Tabstopp (\t), Doppelpunkt (:), Sternchen (*) Fragezeichen (?), umgekehrter Schrägstrich (\\), und Schrägstrich (/). Beachten Sie, dass das NULL-Zeichen (\0) zugelassen wird, da es zur Zeichenfolgenbeendigung verwendet wird. Alles nach dem ersten NULL-Zeichen wird ignoriert.  
  
> [!NOTE]  
>  Die Liste der ungültigen Zeichen hängt möglicherweise vom Betriebssystem ab und kann sich in zukünftigen Versionen ändern.  
  
 Voranstehende und nachfolgende Leerstellen in Instanznamen werden ignoriert und abgeschnitten.  
  
 Um Namenskonflikte mit dem Namen LocalDB zu vermeiden können nicht Instanzen verfügen über einen Namen, der das Benennungsmuster für automatische Instanzen folgt beschriebenen weiter oben in "Automatische Instanz Naming Regeln." Versuch, eine benannte Instanz mit einem Namen erstellen, die effektiv das Benennungsmuster für automatische Instanzen folgt wird eine Standardinstanz erstellt.  
  
## <a name="sql-server-express-localdb-reference-topics"></a>SQL Server Express LocalDB-Referenzthemen  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](sql-server-express-localdb-header-and-version-information.md)  
 Stellt Headerdateiinformationen und Registrierungsschlüssel zum Suchen der LocalDB-Instanz-API bereit.  
  
 [Verwaltungstool für Befehlszeilen: SqlLocalDB.exe](command-line-management-tool-sqllocaldb-exe.md)  
 Beschreibt SqlLocalDB.exe, ein Tool zum Verwalten von LocalDB-Instanzen über die Befehlszeile.  
  
 [LocalDBCreateInstance-Funktion](localdbcreateinstance-function.md)  
 Beschreibt die Funktion zum Erstellen einer neuen LocalDB-Instanz.  
  
 [LocalDBDeleteInstance-Funktion](localdbdeleteinstance-function.md)  
 Beschreibt die Funktion zum Entfernen einer LocalDB-Instanz.  
  
 [LocalDBFormatMessage-Funktion](localdbformatmessage-function.md)  
 Beschreibt die Funktion zum Zurückgeben der lokalisierten Beschreibung für einen LocalDB-Fehler.  
  
 [LocalDBGetInstanceInfo-Funktion](localdbgetinstanceinfo-function.md)  
 Beschreibt die Funktion zum Abrufen von Informationen für eine LocalDB-Instanz, wie z. B., ob sie vorhanden ist, Versionsinformationen, ob sie ausgeführt wird usw.  
  
 [LocalDBGetInstances-Funktion](localdbgetinstances-function.md)  
 Beschreibt die Funktion zum Zurückgeben aller LocalDB-Instanzen mit Versionsangabe.  
  
 [LocalDBGetVersionInfo-Funktion](localdbgetversioninfo-function.md)  
 Beschreibt die Funktion zum Zurückgeben von Informationen für eine angegebene LocalDB-Version.  
  
 [LocalDBGetVersions-Funktion](localdbgetversions-function.md)  
 Beschreibt die Funktion zum Zurückgeben aller LocalDB-Versionen, die auf einem Computer verfügbar sind.  
  
 [LocalDBShareInstance-Funktion](localdbshareinstance-function.md)  
 Beschreibt die Funktion zum Freigeben einer angegebenen LocalDB-Instanz.  
  
 [LocalDBStartInstance-Funktion](localdbstartinstance-function.md)  
 Beschreibt die Funktion zum Starten einer angegebenen LocalDB-Instanz.  
  
 [LocalDBStartTracing-Funktion](localdbstarttracing-function.md)  
 Beschreibt die Funktion zum Aktivieren der API-Ablaufverfolgung für einen Benutzer.  
  
 [LocalDBStopInstance-Funktion](localdbstopinstance-function.md)  
 Beschreibt die Funktion zum Anhalten der Ausführung einer angegebenen LocalDB-Instanz.  
  
 [LocalDBStopTracing-Funktion](localdbstoptracing-function.md)  
 Beschreibt die Funktion zum Deaktivieren der API-Ablaufverfolgung für einen Benutzer.  
  
 [LocalDBUnshareInstance-Funktion](localdbunshareinstance-function.md)  
 Beschreibt die Funktion zum Anhalten der Freigabe einer angegebenen LocalDB-Instanz.  
  
  