---
description: 'Referenz für SQL Server Express LocalDB: Instanz-APIs'
title: SQL Server Express localdb-Instanz-API-Referenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 892ccbc66070e7ef0d198daba60698502ee3bd0f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541189"
---
# <a name="sql-server-express-localdb-reference---instance-apis"></a>Referenz für SQL Server Express LocalDB: Instanz-APIs
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In der herkömmlichen, dienstbasierten SQL Server-Welt sind einzelne auf einem einzelnen Computer installierte SQL Server-Instanzen physisch getrennt. Das heißt, jede Instanz muss separat installiert und entfernt werden, verfügt über einen separaten Satz Binärdateien und wird unter einem separaten Dienstprozess ausgeführt. Der SQL Server-Instanzname wird verwendet, um anzugeben, mit welcher SQL Server-Instanz der Benutzer eine Verbinden herstellen möchte.  
  
 Die SQL Server Express localdb-Instanz-API verwendet ein vereinfachtes "Light"-instanzmodell. Obwohl einzelne LocalDB-Instanzen auf dem Datenträger und in der Registrierung getrennt sind, verwenden sie denselben Satz freigegebener LocalDB-Binärdateien. Darüber hinaus verwendet LocalDB keine Dienste. LocalDB-Instanzen werden bei Bedarf durch LocalDB-Instanz-API-Aufrufe gestartet. In LocalDB wird der Instanzname verwendet, um anzugeben, mit welcher LocalDB-Instanz der Benutzer arbeiten will.  
  
 Eine localdb-Instanz ist immer im Besitz eines einzelnen Benutzers und ist nur über den Kontext dieses Benutzers sichtbar und zugänglich, es sei denn, die instanzfreigabe ist aktiviert.  
  
 Obwohl LocalDB-Instanzen den herkömmlichen SQL Server-Instanzen technisch nicht entsprechen, ist ihre vorgesehene Verwendung ähnlich. Sie werden als *Instanzen* bezeichnet, um diese Ähnlichkeit hervorzuheben und Sie intuitiver für SQL Server Benutzer zu machen.  
  
 LocalDB unterstützt zwei Arten von Instanzen: automatische Instanzen (AI) und benannte Instanzen (BI). Der Bezeichner für eine LocalDB-Instanz ist der Instanzname.  
  
## <a name="automatic-localdb-instances"></a>Automatische LocalDB-Instanzen  
 Automatische localdb-Instanzen sind "Public". Sie werden für den Benutzer automatisch erstellt und verwaltet und können von jeder beliebigen Anwendung verwendet werden. Eine automatische localdb-Instanz ist für jede Version von localdb vorhanden, die auf dem Computer des Benutzers installiert ist.  
  
 Automatische LocalDB-Instanzen stellen die nahtlose Instanzverwaltung bereit. Der Benutzer muss die Instanz nicht erstellen. Dies ermöglicht Benutzern die einfache Installation von Anwendungen und Migration auf andere Computer. Wenn auf dem Zielcomputer die angegebene Version von LocalDB installiert ist, ist die automatische LocalDB-Instanz für diese Version auch auf diesem Computer verfügbar.  
  
### <a name="automatic-instance-management"></a>Automatische Instanzverwaltung  
 Ein Benutzer muss keine automatische LocalDB-Instanz erstellen. Die-Instanz wird bei der erstmaligen Verwendung der-Instanz verzögert erstellt, vorausgesetzt, dass die angegebene Version von localdb auf dem Computer des Benutzers verfügbar ist. Aus Sicht des Benutzers ist die automatische Instanz immer vorhanden, wenn die localdb-Binärdateien vorhanden sind.  
  
 Andere Instanzverwaltungsvorgänge, z. B. Löschen, Freigabe und Freigabe aufheben, funktionieren auch für automatische Instanzen. Beim Löschen einer automatischen Instanz wird die Instanz effektiv zurückgesetzt, wodurch sie beim nächsten Startvorgang neu erstellt wird. Das Löschen einer automatischen Instanz ist möglicherweise erforderlich, wenn die Systemdatenbanken beschädigt sind.  
  
### <a name="automatic-instance-naming-rules"></a>Benennungsregeln für automatische Instanzen  
 Automatische LocalDB-Instanzen haben ein besonderes Muster für den Instanznamen, der zu einem reservierten Namespace gehört. Dies ist zur Verhinderung von Namenskonflikten mit benannten LocalDB-Instanzen erforderlich.  
  
 Der Name der automatischen Instanz ist die Versionsnummer der localdb-Baseline, der ein einzelnes "v"-Zeichen vorangestellt ist. Dies sieht wie folgt aus: "v" und zwei Zahlen mit einem Zeitraum zwischen Ihnen. beispielsweise v 11.0 oder v 12.  
  
 Beispiele für ungültige automatische Instanznamen sind:  
  
-   11,0 ("v"-Zeichen am Anfang fehlt)  
  
-   v11 (Punkt und zweite Zahl der Versionsnummer fehlt)  
  
-   v11. (zweiten Zahl der Versionsnummer fehlt)  
  
-   v11.0.1.2 (Versionsnummer besteht aus mehr als zwei Teilen)  
  
## <a name="named-localdb-instances"></a>Benannte LocalDB-Instanzen  
 Benannte localdb-Instanzen sind "private". eine Instanz ist im Besitz einer einzelnen Anwendung, die für das Erstellen und Verwalten der Instanz zuständig ist. Benannte LocalDB-Instanzen bieten Isolierung und verbessern die Leistung.  
  
### <a name="named-instance-creation"></a>Erstellen einer benannten Instanz  
 Der Benutzer muss benannte Instanzen explizit über die LocalDB-Verwaltungs-API oder implizit für eine verwaltete Anwendung über die Datei app.config erstellen. Eine verwaltete Anwendung verwendet möglicherweise auch die API.  
  
 Jede benannte Instanz verfügt über eine zugeordnete LocalDB-Version. Das heißt, sie verweist auf einen angegebenen Satz LocalDB-Binärdateien. Die Version für die benannte Instanz wird während des Instanzerstellungsprozesses festgelegt.  
  
### <a name="named-instance-naming-rules"></a>Benennungsregeln für benannte Instanzen  
 Ein localdb-Instanzname kann bis zu 128 Zeichen enthalten (der Grenzwert wird vom **vom Datentyp sysname** -Datentyp vorgegeben). Dies ist ein bedeutender Unterschied im Vergleich zu herkömmlichen SQL Server-Instanznamen, die auf NetBIOS-Namen mit 16 ASCII-Zeichen beschränkt sind. Der Grund für diesen Unterschied besteht darin, dass localdb Datenbanken als Dateien behandelt und daher eine dateibasierte Semantik impliziert, sodass Benutzer bei der Auswahl von Instanznamen intuitiv mehr Freiheit haben.  
  
 Ein LocalDB-Instanzname kann alle Unicode-Zeichen enthalten, die innerhalb der Dateinamenkomponente gültig sind. Ungültige Zeichen in einer Dateinamen Komponente enthalten in der Regel die folgenden Zeichen: ASCII/Unicode-Zeichen 1 bis 31 sowie Anführungszeichen ("), kleiner als ( \<), greater than (> ), Pipe (|), Rücktaste (\b), Tabulator (\t), Doppelpunkt (:), Sternchen (*), Fragezeichen (?), umgekehrter Schrägstrich ( \\ ) und Schrägstrich (/). Beachten Sie, dass das NULL-Zeichen (\0) zugelassen wird, da es zur Zeichenfolgenbeendigung verwendet wird. Alles nach dem ersten NULL-Zeichen wird ignoriert.  
  
> [!NOTE]  
>  Die Liste der ungültigen Zeichen hängt möglicherweise vom Betriebssystem ab und kann sich in zukünftigen Versionen ändern.  
  
 Voranstehende und nachfolgende Leerstellen in Instanznamen werden ignoriert und abgeschnitten.  
  
 Um Benennungs Konflikte zu vermeiden, dürfen benannte localdb-Instanzen keinen Namen haben, der dem Benennungs Muster für automatische Instanzen folgt, wie zuvor in "Automatische instanzbenennungs Regeln" beschrieben. Wenn Sie versuchen, eine benannte Instanz mit einem Namen zu erstellen, der dem automatischen instanzbenennungs Muster folgt, wird eine Standard Instanz erstellt.  
  
## <a name="sql-server-express-localdb-reference-topics"></a>SQL Server Express LocalDB-Referenzthemen  
 [SQL Server Express LocalDB-Header und Versionsinformationen](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
 Stellt Headerdateiinformationen und Registrierungsschlüssel zum Suchen der LocalDB-Instanz-API bereit.  
  
 [Verwaltungstool für die Befehlszeile: SqlLocalDB.exe](../../relational-databases/express-localdb-instance-apis/command-line-management-tool-sqllocaldb-exe.md)  
 Beschreibt SqlLocalDB.exe, ein Tool zum Verwalten von LocalDB-Instanzen über die Befehlszeile.  
  
 [LocalDBCreateInstance-Funktion](../../relational-databases/express-localdb-instance-apis/localdbcreateinstance-function.md)  
 Beschreibt die Funktion zum Erstellen einer neuen LocalDB-Instanz.  
  
 [LocalDBDeleteInstance-Funktion](../../relational-databases/express-localdb-instance-apis/localdbdeleteinstance-function.md)  
 Beschreibt die Funktion zum Entfernen einer LocalDB-Instanz.  
  
 [LocalDBFormatMessage-Funktion](../../relational-databases/express-localdb-instance-apis/localdbformatmessage-function.md)  
 Beschreibt die Funktion zum Zurückgeben der lokalisierten Beschreibung für einen LocalDB-Fehler.  
  
 [LocalDBGetInstanceInfo-Funktion](../../relational-databases/express-localdb-instance-apis/localdbgetinstanceinfo-function.md)  
 Beschreibt die Funktion zum Abrufen von Informationen für eine LocalDB-Instanz, wie z. B., ob sie vorhanden ist, Versionsinformationen, ob sie ausgeführt wird usw.  
  
 [LocalDBGetInstances-Funktion](../../relational-databases/express-localdb-instance-apis/localdbgetinstances-function.md)  
 Beschreibt die Funktion zum Zurückgeben aller LocalDB-Instanzen mit Versionsangabe.  
  
 [LocalDBGetVersionInfo-Funktion](../../relational-databases/express-localdb-instance-apis/localdbgetversioninfo-function.md)  
 Beschreibt die Funktion zum Zurückgeben von Informationen für eine angegebene LocalDB-Version.  
  
 [LocalDBGetVersions-Funktion](../../relational-databases/express-localdb-instance-apis/localdbgetversions-function.md)  
 Beschreibt die Funktion zum Zurückgeben aller LocalDB-Versionen, die auf einem Computer verfügbar sind.  
  
 [LocalDBShareInstance-Funktion](../../relational-databases/express-localdb-instance-apis/localdbshareinstance-function.md)  
 Beschreibt die Funktion zum Freigeben einer angegebenen LocalDB-Instanz.  
  
 [LocalDBStartInstance-Funktion](../../relational-databases/express-localdb-instance-apis/localdbstartinstance-function.md)  
 Beschreibt die Funktion zum Starten einer angegebenen LocalDB-Instanz.  
  
 [LocalDBStartTracing-Funktion](../../relational-databases/express-localdb-instance-apis/localdbstarttracing-function.md)  
 Beschreibt die Funktion zum Aktivieren der API-Ablaufverfolgung für einen Benutzer.  
  
 [LocalDBStopInstance-Funktion](../../relational-databases/express-localdb-instance-apis/localdbstopinstance-function.md)  
 Beschreibt die Funktion zum Anhalten der Ausführung einer angegebenen LocalDB-Instanz.  
  
 [LocalDBStopTracing-Funktion](../../relational-databases/express-localdb-instance-apis/localdbstoptracing-function.md)  
 Beschreibt die Funktion zum Deaktivieren der API-Ablaufverfolgung für einen Benutzer.  
  
 [LocalDBUnshareInstance-Funktion](../../relational-databases/express-localdb-instance-apis/localdbunshareinstance-function.md)  
 Beschreibt die Funktion zum Anhalten der Freigabe einer angegebenen LocalDB-Instanz.  
  
  
