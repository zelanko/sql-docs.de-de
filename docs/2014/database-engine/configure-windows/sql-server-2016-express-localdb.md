---
title: SQL Server 2014 Express LocalDB | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- user instances
- LocalDB, described
- local database runtime
- file database
- LocalDB
ms.assetid: 5a641a46-7cfb-4d7b-a90d-6e4625719d74
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 224facf54b0cde09f97010be472e3cc28754e94b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62756989"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` ist ein Ausführungsmodus von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] für Programmentwickler vorgesehen. `LocalDB` -Installation kopiert einen minimalen Satz von Dateien zum Starten der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Einmal `LocalDB` ist installiert, Entwickler eine Verbindung mit einer speziellen Verbindungszeichenfolge initiieren. Wenn eine Verbindung hergestellt wird, wird die erforderliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Infrastruktur automatisch erstellt und gestartet. Sie ermöglicht der Anwendung, die Datenbank zu verwenden, und zwar ohne komplexe oder zeitraubende Konfigurationstasks. Mit Developer Tools können Entwickler [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] bereitstellen, womit sie [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code schreiben und testen können, und zwar ohne dabei eine vollständige Serverinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwalten zu müssen. Eine Instanz von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] `LocalDB` verwaltet wird, mithilfe der `SqlLocalDB.exe` Hilfsprogramm. [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB` sollte verwendet werden, anstelle von der [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] -benutzerinstanzfeatures veraltet ist.  
  
## <a name="installing-localdb"></a>Installieren von LocalDB  
 Die primäre Methode für die Installation von `LocalDB` mithilfe des SqlLocalDB.msi-Programms. `LocalDB` ist eine Option aus, bei der Installation von beliebigen SKU von [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]. Wählen Sie `LocalDB` auf die **Funktionsauswahl** Seite während der Installation des [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Es darf nur eine Installation von der `LocalDB` Binärdateien für jede Hauptversion [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Version. Mehrere [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Prozesse können gestartet werden und verwenden dann die gleichen Binärdateien. Eine Instanz von der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] begann als die `LocalDB` gelten dieselben Einschränkungen wie [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Die `LocalDB` Setupprogramm des SqlLocalDB.msi-Programms verwendet, um die notwendigen Dateien auf dem Computer zu installieren. Nach der Installation `LocalDB` ist eine Instanz der [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , erstellen und öffnen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken. Die Systemdatenbankdateien für die Datenbank werden im lokalen AppData-Pfad des Benutzers gespeichert. Dieser Pfad ist normalerweise verborgen. Beispiel: **C:\Users\\<Benutzer\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\** . Benutzerdatenbankdateien werden an dem vom Benutzer angegebenen Speicherort gespeichert, in der Regel im Ordner **C:\Users\\<Benutzer\>\Documents\\** .  
  
 Weitere Informationen, einschließlich `LocalDB` in einer Anwendung finden Sie unter den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dokumentation [Übersicht über lokale Daten](https://msdn.microsoft.com/library/ms233817\(VS.110\).aspx), [Exemplarische Vorgehensweise: Erstellen einer SQL Server-LocalDB-Datenbank](https://msdn.microsoft.com/library/ms233763\(VS.110\).aspx), und [Exemplarische Vorgehensweise: Verbinden mit Daten in einer SQL Server-LocalDB-Datenbank (Windows Forms)](https://msdn.microsoft.com/library/ms171890\(VS.110\).aspx).  
  
 Weitere Informationen zu den `LocalDB` -API finden Sie unter [SQL Server Express LocalDB Instanz-API-Referenz](https://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx) und [LocalDBStartInstance-Funktion](https://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx).  
  
 Das Hilfsprogramm SqlLocalDb kann neue Instanzen erstellen `LocalDB`, starten und Beenden einer Instanz von `LocalDB`, und enthält Optionen zur Verwaltung von `LocalDB`.  Weitere Informationen zum Hilfsprogramm von SqlLocalDb finden Sie unter [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md).  
  
 Die instanzsortierung für `LocalDB` wird auf SQL_Latin1_General_CP1_CI_AS festgelegt und kann nicht geändert werden. Auf Datenbankebene, Spaltenebene und Ausdrucksebene werden Sortierungen normal unterstützt. Eigenständige Datenbanken basieren auf den Metadaten- und tempdb-Sortierungsregeln unter [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md).  
  
### <a name="restrictions"></a>Restrictions  
 `LocalDB` ein Mergeabonnenten für die Replikation nicht möglich.  
  
 `LocalDB` FILESTREAM wird nicht unterstützt werden.  
  
 `LocalDB` lässt nur lokale Warteschlangen für Service Broker an.  
  
 Eine Instanz von `LocalDB` mit den integrierten Konten gehört, wie z. B. NT AUTHORITY\SYSTEM, kann aufgrund der Windows-dateisystemumleitung verwaltbarkeitsprobleme aufweisen Verwenden Sie stattdessen ein normales Windows-Konto als Besitzer an.  
  
### <a name="automatic-and-named-instances"></a>Automatisch und benannte Instanzen  
 `LocalDB` unterstützt zwei Arten von Instanzen: Automatische Instanzen und benannte Instanzen.  
  
-   Automatische Instanzen von `LocalDB` sind öffentlich. Sie werden erstellt und automatisch für den Benutzer verwaltet. Sie können von allen Anwendungen verwendet werden. Eine automatische Instanz von `LocalDB` vorhanden ist, für jede Version von `LocalDB` auf dem Computer des Benutzers installiert. Automatische Instanzen von `LocalDB` stellen die nahtlose instanzverwaltung bereit. Es ist nicht nötig, eine Instanz zu stellen, da es auch so funktioniert. Dies ermöglicht einfache Anwendungsinstallationen und eine Migration zu einem anderen Computer. Wenn auf dem Zielcomputer die angegebene Version von `LocalDB` installiert ist, ist die automatische Instanz von `LocalDB` für diese Version auch auf dem Zielcomputer verfügbar. Automatische Instanzen von `LocalDB` haben ein besonderes Muster für den Instanznamen, die zu einem reservierten Namespace gehört. Dies verhindert Namenskonflikte mit benannten Instanzen von `LocalDB`. Der Name der automatischen Instanz ist **MSSQLLocalDB**.  
  
-   Benannte Instanzen von `LocalDB` sind privat. Diese gehören einer Einzelanwendung, die für das Erstellen und Verwalten der Instanz zuständig ist. Benannte Instanzen sind zum Teil von anderen Instanzen isoliert und können durch die Reduzierung von Ressourcenkonflikten, die mit anderen Datenbankbenutzern auftreten können, die Leistung verbessern. Benannte Instanzen müssen explizit erstellt werden, vom Benutzer über die `LocalDB` Verwaltungs-API oder implizit über die "App.config"-Datei für eine verwaltete Anwendung (obwohl es sich um eine verwaltete Anwendung auch die-API verwenden kann, falls gewünscht). Jede benannte Instanz von `LocalDB` verfügt über eine zugeordnete `LocalDB` Version, die auf den entsprechenden Berechtigungssatz verweist `LocalDB` Binärdateien. Der Instanzname von einer `LocalDB` ist `sysname` Daten-Datentyp und kann bis zu 128 Zeichen aufweisen. (Dies unterscheidet sich von regulären benannten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Namen auf reguläre NetBIOS-Namen von 16 ASCII-Zeichen beschränken.) Der Name einer Instanz von `LocalDB` darf keine Unicode-Zeichen, die Dateinamen gültig sind.  Eine benannte Instanz, die einen automatischen Instanznamen verwendet, wird eine automatische Instanz.  
  
 Unterschiedliche Benutzer eines Computers können über Instanzen mit dem gleichen Namen verfügen. Jede Instanz ist ein anderer Prozess, der als ein anderer Benutzer ausgeführt wird.  
  
## <a name="shared-instances-of-localdb"></a>Freigegebene Instanzen von LocalDB  
 Zur Unterstützung von Szenarien, in denen mehrere Benutzer des Computers zur Verbindung mit einer einzelnen Instanz von müssen `LocalDB`, `LocalDB` Freigeben von Instanzen unterstützt. Ein Instanzbesitzer kann auswählen, anderen Benutzern auf dem Computer zu ermöglichen, eine Verbindung mit seiner Instanz herzustellen. Sowohl automatische als auch benannte Instanzen von `LocalDB` freigegeben werden können. Zum Freigeben einer Instanz von `LocalDB` müssen Benutzer einen freigegebenen Namen (Alias) dafür auswählen. Da der freigegebene Name für Benutzer des Computers sichtbar ist, muss dieser freigegebene Name auf dem Computer eindeutig sein. Der freigegebene Name für eine Instanz von `LocalDB` hat das gleiche Format wie die benannte Instanz von `LocalDB`.  
  
 Nur ein Administrator auf dem Computer, eine freigegebene Instanz von erstellen kann `LocalDB`. Eine freigegebene Instanz von `LocalDB` kann von einem Administrator oder vom Besitzer der freigegebenen Instanz von aufgehoben sein `LocalDB`. Freigeben und ohne Freigabe eine Instanz von `LocalDB`, verwenden Sie die `LocalDBShareInstance` und `LocalDBUnShareInstance` Methoden der `LocalDB` -API oder die Freigabe und den Optionen des SqlLocalDb-Hilfsprogramms.  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>Starten von LocalDB und Herstellen einer Verbindung zu LocalDB  
  
### <a name="connecting-to-the-automatic-instance"></a>Herstellen einer Verbindung zur automatischen Instanz  
 Die einfachste Möglichkeit zur Verwendung `LocalDB` ist für die Verbindung mit der automatischen Instanz, die im Besitz des aktuellen Benutzers mithilfe der Verbindungszeichenfolge **"Server = \MSSQLLocalDB;Integrated Security = True"** . Verwenden Sie eine Verbindungszeichenfolge ähnlich **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"** , um eine Verbindung mit einer bestimmten Datenbank mit dem Dateinamen herzustellen.  
  
> [!NOTE]  
>  Zum ersten Mal ein Benutzer auf einem Computer versucht, für die Verbindung `LocalDB`, die automatische Instanz muss sowohl erstellt und gestartet werden. Die zusätzliche Zeit, die für das Erstellen der Instanz benötigt wird, kann dazu führen, dass der Verbindungsversuch abgebrochen und eine Timeoutmeldung ausgegeben wird. Warten Sie in diesem Fall einige Sekunden, bis der Erstellungsvorgang vollständig abgeschlossen ist, und stellen Sie dann erneut eine Verbindung her.  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>Erstellen einer benannten Instanz und Herstellen einer Verbindung  
 Zusätzlich zur automatischen Instanz `LocalDB` auch unterstützt benannte Instanzen. Verwenden Sie das Programm SqlLocalDB.exe zu erstellen, starten und Beenden einer benannten Instanz von `LocalDB`. Weitere Informationen zu SqlLocalDB.exe finden Sie unter [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md).  
  
```ms-dos  
REM Create an instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" create LocalDBApp1  
REM Start the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" start LocalDBApp1  
REM Gather information about the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" info LocalDBApp1  
```  
  
 Die letzte Zeile oben gibt Informationen ähnlich der folgenden zurück.  
  
|||  
|-|-|  
|Name|"LocalDBApp1"|  
|Version|\<aktuelle Version>|  
|Freigegebener Name|""|  
|Besitzer|„\<Ihr Windows-Benutzerkonto>“|  
|Automatisch erstellen|Nein|  
|Status|Ausführen|  
|Letzte Startzeit|\<Datum und Uhrzeit>|  
|Instanz-Pipename|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  Wenn Ihre Anwendung eine Version von .NET vor 4.0.2 verwendet. Sie müssen eine Verbindung herstellen direkt an der named Pipe, der die `LocalDB`. Die Instanz-Pipe-Name-Wert ist die named pipe, die die Instanz von `LocalDB` wird lauscht. Der Teil des instanzpipenamens nach LOCALDB # zum Ändern der einzelnen wird Start der Instanz von `LocalDB` gestartet wird. Für die Verbindung mit der Instanz von `LocalDB` mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], geben Sie die Namen der instanzpipe im der **Servernamen** im Feld der **Herstellen einer Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]**  Dialogfeld. Von Ihrem benutzerdefinierten Programm können Sie Verbindung zur Instanz von herstellen `LocalDB` mithilfe einer Verbindungszeichenfolge ähnlich wie `SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>Herstellen einer Verbindung mit einer freigegebenen Instanz von LocalDB  
 Verbindung mit einer freigegebenen Instanz von `LocalDB` hinzufügen **.\\**  (Punkt + umgekehrter Schrägstrich) auf die Verbindungszeichenfolge auf den für die freigegebenen Instanzen reservierten Namespace zu verweisen. Beispielsweise, um die Verbindung mit einer freigegebenen Instanz von `LocalDB` mit dem Namen `AppData` verwenden Sie z. B. eine Verbindungszeichenfolge `(localdb)\.\AppData` als Teil der Verbindungszeichenfolge angegeben. Ein Benutzer, die Verbindung mit einer freigegebenen Instanz von `LocalDB` , dass sie nicht besitzen, müssen eine Windows-Authentifizierung oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldenamen für die Authentifizierung.  
  
## <a name="troubleshooting"></a>Problembehandlung  
 Weitere Informationen zur Problembehandlung `LocalDB`, finden Sie unter [Problembehandlung bei SQL Server 2012 Express LocalDB](https://social.technet.microsoft.com/wiki/contents/articles/4609.aspx).  
  
## <a name="permissions"></a>Berechtigungen  
 Eine Instanz von [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` ist eine von einem Benutzer zur eigenen Verwendung erstellte Instanz. Jeder Benutzer auf dem Computer zu erstellen eine Datenbank mit einer Instanz von `LocalDB`, Dateien unter seinem Benutzerprofil speichern und den Vorgang mit ihren Anmeldeinformationen ausgeführt. In der Standardeinstellung der Zugriff auf die Instanz von `LocalDB` ist auf den Besitzer beschränkt. Die Daten in die `LocalDB` per Dateisystemzugriff auf die Datenbankdateien geschützt ist. Wenn Datenbankdateien an einem freigegebenen Speicherort gespeichert sind, kann die Datenbank von jedem Benutzer mit Dateisystemzugriff auf diesen Speicherort geöffnet werden, mithilfe einer Instanz von `LocalDB` , die sie besitzen. Wenn die Datenbankdateien sich an einem geschützten Speicherort befinden, z. B. dem Datenordner des Benutzers, können nur dieser Benutzer und Administratoren mit Zugriffsrechten für diesen Ordner die Datenbank öffnen. Die `LocalDB` Dateien können nur geöffnet werden, um eine Instanz des `LocalDB` zu einem Zeitpunkt.  
  
> [!NOTE]  
>  `LocalDB` wird immer unter dem Sicherheitskontext des Benutzers. d. h. `LocalDB` nie mit den Anmeldeinformationen der lokalen Administratorgruppe ausgeführt. Dies bedeutet, dass alle Datenbankdateien, die ein, die eine `LocalDB` Instanz über der zuständige Benutzer Windows-Konto ohne Berücksichtigung der Mitgliedschaft in der lokalen Gruppe Administratoren möglich sein muss.  
  
## <a name="see-also"></a>Siehe auch  
 [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md)  
  
  
