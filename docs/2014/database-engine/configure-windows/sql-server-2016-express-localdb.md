---
title: SQL Server 2014 Express localdb | Microsoft-Dokumentation
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
ms.openlocfilehash: f3c43604604580c5924be4daf4d473407564d247
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934881"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` ist ein Ausführungs Modus von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , der speziell für Programmentwickler konzipiert ist. `LocalDB`die Installation kopiert einen minimalen Satz von Dateien, die erforderlich sind, um das zu starten [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Nachdem `LocalDB` installiert wurde, initiieren Entwickler eine Verbindung mithilfe einer speziellen Verbindungs Zeichenfolge. Wenn eine Verbindung hergestellt wird, wird die erforderliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Infrastruktur automatisch erstellt und gestartet. Sie ermöglicht der Anwendung, die Datenbank zu verwenden, und zwar ohne komplexe oder zeitraubende Konfigurationstasks. Mit Developer Tools können Entwickler [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] bereitstellen, womit sie [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code schreiben und testen können, und zwar ohne dabei eine vollständige Serverinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwalten zu müssen. Eine Instanz von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] `LocalDB` wird mit dem- `SqlLocalDB.exe` Hilfsprogramm verwaltet. [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB`sollte anstelle der [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] benutzerinstanzfunktion verwendet werden, die veraltet ist.  
  
## <a name="installing-localdb"></a>Installieren von LocalDB  
 Die primäre Methode für die Installation von `LocalDB` ist die Verwendung des-SqlLocalDB.msi Programms. `LocalDB`ist eine Option bei der Installation einer beliebigen SKU von [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] . Wählen Sie `LocalDB` während der Installation von auf der Seite **Funktionsauswahl** aus [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] . Es kann nur eine Installation der `LocalDB` Binärdateien für jede Hauptversion vorhanden sein [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Mehrere [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Prozesse können gestartet werden und verwenden dann die gleichen Binärdateien. Eine Instanz von, die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] als gestartet `LocalDB` wurde, unterliegt denselben Einschränkungen wie[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Das `LocalDB` Setup Programm verwendet das SqlLocalDB.msi Programm, um die erforderlichen Dateien auf dem Computer zu installieren. Nach der Installation `LocalDB` ist eine Instanz von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , mit der Datenbanken erstellt und geöffnet werden können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Die Systemdatenbankdateien für die Datenbank werden im lokalen AppData-Pfad des Benutzers gespeichert. Dieser Pfad ist normalerweise verborgen. Beispiel: **C:\Users\\<Benutzer\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\**. Benutzerdatenbankdateien werden an dem vom Benutzer angegebenen Speicherort gespeichert, in der Regel im Ordner **C:\Users\\<Benutzer\>\Documents\\**.  
  
 Weitere Informationen zum einschließen `LocalDB` in eine Anwendung finden Sie in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dokumentation [lokale Daten Übersicht](https://msdn.microsoft.com/library/ms233817\(VS.110\).aspx), Exemplarische Vorgehensweise [: Erstellen einer SQL Server localdb-Datenbank](https://msdn.microsoft.com/library/ms233763\(VS.110\).aspx)und Exemplarische Vorgehensweise [: Herstellen einer Verbindung mit Daten in einer SQL Server localdb-Datenbank (Windows Forms)](https://msdn.microsoft.com/library/ms171890\(VS.110\).aspx).  
  
 Weitere Informationen zur `LocalDB` API finden Sie unter [SQL Server Express localdb-Instanz-API-Referenz](https://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx) und [localdbstartinstance-Funktion](https://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx).  
  
 Das Hilfsprogramm sqllocaldb kann neue Instanzen von erstellen `LocalDB` , eine Instanz von starten und Beenden `LocalDB` und enthält Optionen, die Sie bei der Verwaltung von unterstützen `LocalDB` .  Weitere Informationen zum Hilfsprogramm von SqlLocalDb finden Sie unter [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md).  
  
 Die instanzsortierung für `LocalDB` ist auf SQL_Latin1_General_CP1_CI_AS festgelegt und kann nicht geändert werden. Auf Datenbankebene, Spaltenebene und Ausdrucksebene werden Sortierungen normal unterstützt. Eigenständige Datenbanken basieren auf den Metadaten- und tempdb-Sortierungsregeln unter [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md).  
  
### <a name="restrictions"></a>Beschränkungen  
 `LocalDB`kann kein mergereplikationsabonnent sein.  
  
 `LocalDB`FILESTREAM wird von nicht unterstützt.  
  
 `LocalDB`ermöglicht nur lokale Warteschlangen für Service Broker.  
  
 Eine Instanz von `LocalDB` , die im Besitz der integrierten Konten wie NT-Autorität \ System ist, kann aufgrund der Windows-Datei System Umleitung verwaltbarkeitsprobleme aufweisen. Verwenden Sie stattdessen ein normales Windows-Konto als Besitzer.  
  
### <a name="automatic-and-named-instances"></a>Automatisch und benannte Instanzen  
 `LocalDB`unterstützt zwei Arten von Instanzen: automatische Instanzen und benannte Instanzen.  
  
-   Automatische Instanzen von `LocalDB` sind öffentlich. Sie werden erstellt und automatisch für den Benutzer verwaltet. Sie können von allen Anwendungen verwendet werden. Eine automatische Instanz von ist `LocalDB` für jede Version von vorhanden, `LocalDB` die auf dem Computer des Benutzers installiert ist. Automatische Instanzen von `LocalDB` stellen eine nahtlose Instanzverwaltung bereit. Es ist nicht nötig, eine Instanz zu stellen, da es auch so funktioniert. Dies ermöglicht einfache Anwendungsinstallationen und eine Migration zu einem anderen Computer. Wenn auf dem Zielcomputer die angegebene Version von `LocalDB` installiert ist, ist die automatische Instanz von `LocalDB` für diese Version auch auf dem Zielcomputer verfügbar. Automatische Instanzen von `LocalDB` haben ein spezielles Muster für den Instanznamen, der zu einem reservierten Namespace gehört. Dies verhindert Namenskonflikte mit benannten Instanzen von `LocalDB` . Der Name der automatischen Instanz ist **MSSQLLocalDB**.  
  
-   Benannte Instanzen von `LocalDB` sind privat. Diese gehören einer Einzelanwendung, die für das Erstellen und Verwalten der Instanz zuständig ist. Benannte Instanzen sind zum Teil von anderen Instanzen isoliert und können durch die Reduzierung von Ressourcenkonflikten, die mit anderen Datenbankbenutzern auftreten können, die Leistung verbessern. Benannte Instanzen müssen explizit vom Benutzer über die `LocalDB` Verwaltungs-API oder implizit über die app.config Datei für eine verwaltete Anwendung erstellt werden (obwohl die verwaltete Anwendung ggf. auch die API verwenden kann). Jede benannte Instanz von `LocalDB` verfügt über eine zugeordnete `LocalDB` Version, die auf den jeweiligen Satz von `LocalDB` Binärdateien zeigt. Der Instanzname eines `LocalDB` ist vom `sysname` Datentyp und kann bis zu 128 Zeichen enthalten. (Dies unterscheidet sich von regulären benannten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die Namen auf reguläre NetBIOS-Namen von 16 ASCII-Zeichen beschränken.) Der Name einer Instanz von `LocalDB` kann beliebige Unicode-Zeichen enthalten, die in einem Dateinamen zulässig sind.  Eine benannte Instanz, die einen automatischen Instanznamen verwendet, wird eine automatische Instanz.  
  
 Unterschiedliche Benutzer eines Computers können über Instanzen mit dem gleichen Namen verfügen. Jede Instanz ist ein anderer Prozess, der als ein anderer Benutzer ausgeführt wird.  
  
## <a name="shared-instances-of-localdb"></a>Freigegebene Instanzen von LocalDB  
 Zur Unterstützung von Szenarien, in denen mehrere Benutzer des Computers eine Verbindung mit einer einzelnen Instanz von herstellen müssen `LocalDB` , `LocalDB` unterstützt die-instanzfreigabe. Ein Instanzbesitzer kann auswählen, anderen Benutzern auf dem Computer zu ermöglichen, eine Verbindung mit seiner Instanz herzustellen. Sowohl automatische als auch benannte Instanzen von `LocalDB` können freigegeben werden. Zum Freigeben einer Instanz von `LocalDB` müssen Benutzer einen freigegebenen Namen (Alias) dafür auswählen. Da der freigegebene Name für Benutzer des Computers sichtbar ist, muss dieser freigegebene Name auf dem Computer eindeutig sein. Der freigegebene Name für eine Instanz von `LocalDB` hat das gleiche Format wie die benannte Instanz von `LocalDB` .  
  
 Nur ein Administrator auf dem Computer kann eine freigegebene Instanz von erstellen `LocalDB` . Eine freigegebene Instanz von `LocalDB` kann von einem Administrator oder dem Besitzer der freigegebenen Instanz von freigegeben werden `LocalDB` . Verwenden Sie zum Freigeben und Aufheben der Freigabe einer Instanz von `LocalDB` die `LocalDBShareInstance` -Methode und die- `LocalDBUnShareInstance` Methode der- `LocalDB` API oder die Freigabe-und aufgehoben-Optionen des Hilfsprogramms sqllocaldb.  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>Starten von LocalDB und Herstellen einer Verbindung zu LocalDB  
  
### <a name="connecting-to-the-automatic-instance"></a>Herstellen einer Verbindung zur automatischen Instanz  
 Die einfachste Möglichkeit, zu verwenden, besteht darin, mit der `LocalDB` Verbindungs Zeichenfolge **"Server = (localdb) \mssqllocaldb; Integrated Security = true"** eine Verbindung mit der automatischen Instanz herzustellen, die sich im Besitz des aktuellen Benutzers befindet. Verwenden Sie eine Verbindungszeichenfolge ähnlich **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"**, um eine Verbindung mit einer bestimmten Datenbank mit dem Dateinamen herzustellen.  
  
> [!NOTE]  
>  Wenn ein Benutzer auf einem Computer zum ersten Mal versucht, eine Verbindung mit herzustellen `LocalDB` , muss die automatische Instanz sowohl erstellt als auch gestartet werden. Die zusätzliche Zeit, die für das Erstellen der Instanz benötigt wird, kann dazu führen, dass der Verbindungsversuch abgebrochen und eine Timeoutmeldung ausgegeben wird. Warten Sie in diesem Fall einige Sekunden, bis der Erstellungsvorgang vollständig abgeschlossen ist, und stellen Sie dann erneut eine Verbindung her.  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>Erstellen einer benannten Instanz und Herstellen einer Verbindung  
 Zusätzlich zur automatischen Instanz `LocalDB` unterstützt auch benannte Instanzen. Verwenden Sie das SqlLocalDB.exe Programm, um eine benannte Instanz von zu erstellen, zu starten und zu beenden `LocalDB` . Weitere Informationen zu SqlLocalDB.exe finden Sie unter [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md).  
  
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
|Version|\<Current Version>|  
|Freigegebener Name|""|  
|Besitzer|"\<Your Windows User>"|  
|Automatisch erstellen|Nein|  
|State|„Wird ausgeführt“|  
|Letzte Startzeit|\<Date and Time>|  
|Instanz-Pipename|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  Wenn Ihre Anwendung eine Version von .net vor 4.0.2 verwendet, müssen Sie eine direkte Verbindung mit dem Named Pipe der herstellen `LocalDB` . Der Name des instanzpipenamens ist der Named Pipe, der von der Instanz von überwacht `LocalDB` wird. Der Teil des instanzpipenamens nach localdb # ändert sich jedes Mal, wenn die Instanz von `LocalDB` gestartet wird. Um mithilfe von eine Verbindung mit der Instanz von herzustellen `LocalDB` [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , geben Sie im Dialogfeld **verbinden [!INCLUDE[ssDE](../../includes/ssde-md.md)] mit** den Namen der instanzpipe im Feld **Server Name** ein. In Ihrem benutzerdefinierten Programm können Sie `LocalDB` mithilfe einer Verbindungs Zeichenfolge, die folgendem ähnelt, eine Verbindung zur Instanz von herstellen.`SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>Herstellen einer Verbindung mit einer freigegebenen Instanz von LocalDB  
 Zum Herstellen einer Verbindung mit einer freigegebenen Instanz von `LocalDB` fügen Sie die Verbindungs Zeichenfolge hinzu ** \\ ** , um auf den Namespace zu verweisen, der für freigegebene Instanzen reserviert ist. Verwenden Sie beispielsweise `LocalDB` `AppData` eine Verbindungs Zeichenfolge wie `(localdb)\.\AppData` als Teil der Verbindungs Zeichenfolge, um eine Verbindung mit einer freigegebenen Instanz von mit dem Namen herzustellen. Ein Benutzer, der eine Verbindung mit einer freigegebenen Instanz von herstellt, deren Besitzer `LocalDB` er ist, muss über eine Windows-Authentifizierung oder eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung verfügen.  
  
## <a name="troubleshooting"></a>Problembehandlung  
 Informationen zur Problembehandlung `LocalDB` finden Sie unter [Problembehandlung SQL Server 2012 Express localdb](https://social.technet.microsoft.com/wiki/contents/articles/4609.aspx).  
  
## <a name="permissions"></a>Berechtigungen  
 Eine Instanz von ist eine Instanz, die [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` von einem Benutzer zur Verwendung erstellt wurde. Jeder Benutzer auf dem Computer kann eine Datenbank mithilfe einer Instanz von erstellen `LocalDB` , Dateien unter seinem Benutzerprofil speichern und den Prozess unter Ihren Anmelde Informationen ausführen. Standardmäßig ist der Zugriff auf die-Instanz `LocalDB` auf den Besitzer beschränkt. Die in enthaltenen Daten `LocalDB` werden durch den Dateisystem Zugriff auf die Datenbankdateien geschützt. Wenn Benutzerdaten Bank Dateien an einem freigegebenen Speicherort gespeichert werden, kann die Datenbank von jedem Benutzer mit Dateisystem Zugriff auf diesen Speicherort geöffnet werden, indem eine Instanz von verwendet wird, `LocalDB` die Sie besitzen. Wenn die Datenbankdateien sich an einem geschützten Speicherort befinden, z. B. dem Datenordner des Benutzers, können nur dieser Benutzer und Administratoren mit Zugriffsrechten für diesen Ordner die Datenbank öffnen. Die `LocalDB` Dateien können jeweils nur von einer Instanz von geöffnet werden `LocalDB` .  
  
> [!NOTE]  
>  `LocalDB`wird immer im Sicherheitskontext des Benutzers ausgeführt. Das heißt, `LocalDB` niemals mit Anmelde Informationen aus der lokalen Administrator Gruppe. Dies bedeutet, dass auf alle Datenbankdateien `LocalDB` , die von einer-Instanz verwendet werden, über das Windows-Konto des besitzenden Benutzers zugegriffen werden muss, ohne dass die Mitgliedschaft in der lokalen Administrator Gruppe  
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md)  
  
  
