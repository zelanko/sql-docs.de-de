---
title: SQL Server Express LocalDB | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/17/2019
ms.prod: sql
ms.prod_service: high-availability
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
manager: jroth
ms.openlocfilehash: e4375d7b0ce19c5bb0f44a0be3b55e7b105b5a4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67145420"
---
# <a name="sql-server-express-localdb"></a>SQL Server Express LocalDB

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Microsoft SQL Server 2016 Express LocalDB ist ein Feature von [SQL Server Express](../../sql-server/editions-and-components-of-sql-server-2016.md) speziell für Entwickler. Es ist in SQL Server Express mit Advanced Services verfügbar.

Bei der Installation von LocalDB wird ein minimalen Satz von Dateien kopiert, der für den Start von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] erforderlich ist. Sobald LocalDB installiert ist, können Sie mithilfe einer speziellen Verbindungszeichenfolge eine Verbindung herstellen. Wenn eine Verbindung hergestellt wird, wird die erforderliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Infrastruktur automatisch erstellt und gestartet. Sie ermöglicht der Anwendung, die Datenbank zu verwenden, und zwar ohne komplexe Konfigurationstasks. Mit Developer Tools können Entwickler [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] bereitstellen, womit sie [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code schreiben und testen können, und zwar ohne dabei eine vollständige Serverinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwalten zu müssen. 

## <a name="try-it-out"></a>Probieren Sie es aus. 

- Um SQL Server Express LocalDB herunterzuladen und zu installieren, navigieren Sie zur Seite **[Downloads für SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads)** . LocalDB ist eine Funktion, die Sie während der Installation auswählen. Sie ist verfügbar, wenn Sie die Medien herunterladen. Wenn Sie die Medien herunterladen, wählen Sie **Express Advanced** oder das LocalDB-Paket aus. Im **Visual Studio-Installer** können Sie SQL Server Express LocalDB als Teil der Workload **.NET-Desktopentwicklung** oder als einzelne Komponente installieren.

 >[!TIP]
 > Sie können LocalDB auch als Teil von Visual Studio installieren. Wählen Sie während der Installation von Visual Studio die Workload **.NET-Desktopentwicklung** aus, in der SQL Server Express LocalDB enthalten ist.

- Sie haben ein Azure-Konto? [Machen Sie sich mit den ersten Schritten vertraut](https://azure.microsoft.com/services/virtual-machines/sql-server/), und starten Sie einen virtuellen Computer, auf dem [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bereits installiert ist.

## <a name="install-localdb"></a>Installieren von LocalDB

Installieren Sie LocalDB über den Installations-Assistenten oder mithilfe des Programms „SqlLocalDB.msi“. LocalDB ist eine Option bei der Installation von [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]. 
 
Wählen Sie während der Installation auf der Seite **Featureauswahl/Freigegebene Features**  „LocalDB“ aus. Es darf nur eine Installation der LocalDB-Binärdateien für eine Hauptversion von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] vorhanden sein. Mehrere [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Prozesse können gestartet werden und verwenden dann die gleichen Binärdateien. Für eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], die als LocalDB gestartet wurde, gelten die gleichen Einschränkungen wie für [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].

Eine Instanz von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] LocalDB wird mit dem Hilfsprogramm `SqlLocalDB.exe` verwaltet. [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] LocalDB sollte anstelle des veralteten [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]-Benutzerinstanzfeatures verwendet werden.

## <a name="description"></a>und Beschreibung

Das LocalDB-Setupprogramm installiert mithilfe von `SqlLocalDB.msi` die notwendigen Dateien auf dem Computer. Nach der Installation ist LocalDB eine Instanz von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken erstellt und geöffnet werden können. Die Systemdatenbankdateien für die Datenbank werden im lokalen AppData-Pfad des Benutzers gespeichert, der normalerweise verborgen ist. Beispiel: `C:\Users\<user>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\`. Benutzerdatenbankdateien werden an dem vom Benutzer angegebenen Speicherort gespeichert, in der Regel im Ordner `C:\Users\<user>\Documents\`.

Weitere Informationen zur Einbindung von LocalDB in eine Anwendung finden Sie unter [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [Übersicht über lokale Daten](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/ms233817(v=vs.110)), [Erstellen einer Datenbank und Hinzufügen von Tabellen in Visual Studio](/visualstudio/data-tools/create-a-sql-database-by-using-a-designer).

Weitere Informationen zur LocalDB-API finden Sie in der [Referenz zu SQL Server Express LocalDB](../../relational-databases/sql-server-express-localdb-reference.md).

Das Hilfsprogramm `SqlLocalDb` kann neue Instanzen von LocalDB erstellen, eine Instanz von LocalDB starten und beenden und enthält Optionen zur Verwaltung von LocalDB. Weitere Informationen zum Hilfsprogramm `SqlLocalDb` finden Sie im Artikel zum [Hilfsprogramm SqlLocalDB](../../tools/sqllocaldb-utility.md).

Die Instanzsortierung für LocalDB ist auf `SQL_Latin1_General_CP1_CI_AS` festgelegt und kann nicht geändert werden. Auf Datenbankebene, Spaltenebene und Ausdrucksebene werden Sortierungen normal unterstützt. Eigenständige Datenbanken basieren auf den Metadaten- und `tempdb`-Sortierungsregeln unter [Enthaltene Datenbanksortierungen](../../relational-databases/databases/contained-database-collations.md).

### <a name="restrictions"></a>Restrictions

- LocalDB kann nicht als Abonnent für die Mergereplikation hinzugefügt werden.

- FILESTREAM wird von LocalDB nicht unterstützt.

- LocalDB lässt für Service Broker nur lokale Warteschlangen zu.

- Eine Instanz von LocalDB im Besitz der integrierten Konten, wie z.B. `NT AUTHORITY\SYSTEM`, kann aufgrund der Windows-Dateisystemumleitung Verwaltbarkeitsprobleme aufweisen. Verwenden Sie stattdessen als Besitzer ein normales Windows-Benutzerkonto.

### <a name="automatic-and-named-instances"></a>Automatische und benannte Instanzen

LocalDB unterstützt zwei Arten von Instanzen: Automatische Instanzen und benannte Instanzen.

- Automatische Instanzen von LocalDB sind öffentlich. Sie werden erstellt und automatisch für den Benutzer verwaltet. Sie können von allen Anwendungen verwendet werden. Eine automatische Instanz von LocalDB ist für jede Version von LocalDB vorhanden, die auf dem Computer des Benutzers installiert ist. Automatische Instanzen von LocalDB ermöglichen eine nahtlose Instanzverwaltung. Es ist nicht nötig, eine Instanz zu stellen, da es auch so funktioniert. Dieses Feature ermöglicht einfache Anwendungsinstallationen und eine Migration auf einen anderen Computer. Wenn auf dem Zielcomputer die angegebene Version von LocalDB installiert ist, ist die automatische Instanz von LocalDB für diese Version auch auf dem Zielcomputer verfügbar. Automatische Instanzen von LocalDB haben ein besonderes Muster für den Instanznamen, der zu einem reservierten Namespace gehört. Automatische Instanzen verhindern Namenskonflikte mit benannten LocalDB-Instanzen. Der Name der automatischen Instanz ist **MSSQLLocalDB**.

- Benannte Instanzen von LocalDB sind privat. Diese gehören einer Einzelanwendung, die für das Erstellen und Verwalten der Instanz zuständig ist. Benannte Instanzen sind zum Teil von anderen Instanzen isoliert und können durch die Reduzierung von Ressourcenkonflikten, die mit anderen Datenbankbenutzern auftreten können, die Leistung verbessern. Der Benutzer muss benannte Instanzen explizit über die LocalDB-Verwaltungs-API oder implizit für eine verwaltete Anwendung (auch wenn die verwaltete Anwendung auch bei Bedarf die API verwenden kann) über die Datei „app.config“ erstellen. Jede benannte Instanz von LocalDB verfügt über eine zugeordnete Version von LocalDB, die auf einen angegebenen Satz von LocalDB-Binärdateien verweist. Ein Instanzname von LocalDB hat den Datentyp **sysname** und kann bis zu 128 Zeichen aufweisen. (Dies unterscheidet sich von regulären benannten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Namen auf reguläre NetBIOS-Namen von 16 ASCII-Zeichen beschränken.) Der Name einer Instanz von LocalDB kann alle Unicode-Zeichen enthalten, die für den Dateinamen gültig sind. Eine benannte Instanz, die einen automatischen Instanznamen verwendet, wird eine automatische Instanz.

Unterschiedliche Benutzer eines Computers können über Instanzen mit dem gleichen Namen verfügen. Jede Instanz ist ein anderer Prozess, der als ein anderer Benutzer ausgeführt wird.

## <a name="shared-instances-of-localdb"></a>Freigegebene Instanzen von LocalDB

Von LocalDBwird das Freigeben von Instanzen unterstützt, um Szenarien zu unterstützen, in denen mehrere Benutzer eines Computer sich mit einer einzelnen Instanz von LocalDB verbinden müssen. Ein Instanzbesitzer kann anderen Benutzern auf dem Computer ermöglichen, eine Verbindung mit der Instanz herzustellen. Sowohl automatische als auch benannte Instanzen von LocalDB können freigegeben werden. Zum Freigeben einer Instanz von LocalDB müssen Benutzer einen freigegebenen Namen (Alias) dafür auswählen. Da der freigegebene Name für Benutzer des Computers sichtbar ist, muss dieser freigegebene Name auf dem Computer eindeutig sein. Der freigegebene Name für eine Instanz von LocalDB verfügt über das gleiche Format wie die benannte Instanz von LocalDB.

Nur ein Administrator auf dem Computer kann eine freigegebene Instanz von LocalDB erstellen. Die Freigabe einer freigegebenen Instanz von LocalDB kann von einem Administrator oder dem Besitzer der freigegebenen Instanz von LocalDB entfernt werden. Verwenden Sie zum Freigeben oder Aufheben der Freigabe einer Instanz von LocalDB die Methoden `LocalDBShareInstance` und `LocalDBUnShareInstance` der LocalDB-API oder die Optionen zum Freigeben oder Aufheben einer Freigabe des Hilfsprogramms `SqlLocalDb`.

## <a name="start-localdb-and-connect-to-localdb"></a>Starten von LocalDB und Herstellen einer Verbindung mit LocalDB

### <a name="connect-to-the-automatic-instance"></a>Herstellen einer Verbindung mit der automatischen Instanz

Die einfachste Möglichkeit zur Verwendung von LocalDB besteht darin, mit der Verbindungszeichenfolge `Server=(localdb)\MSSQLLocalDB;Integrated Security=true` eine Verbindung mit der automatischen Instanz herzustellen, deren Besitzer der aktuelle Benutzer ist. Um mithilfe des Dateinamens eine Verbindung mit einer bestimmten Datenbank herzustellen, verwenden Sie eine ähnliche Verbindungszeichenfolge wie `Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf`.

>[!NOTE]
>Wenn ein Benutzer zum ersten Mal auf einem Computer versucht, eine Verbindung mit LocalDB herzustellen, muss die automatische Instanz sowohl erstellt als auch gestartet werden. Die zusätzliche Zeit, die für das Erstellen der Instanz benötigt wird, kann dazu führen, dass der Verbindungsversuch abgebrochen und eine Timeoutmeldung ausgegeben wird. Warten Sie in diesem Fall einige Sekunden, bis der Erstellungsvorgang vollständig abgeschlossen ist, und stellen Sie dann erneut eine Verbindung her.

### <a name="create-and-connect-to-a-named-instance"></a>Erstellen einer benannten Instanz und Herstellen einer Verbindung

Zusätzlich zur automatischen Instanz unterstützt LocalDB auch benannte Instanzen. Mit dem Programm „SqlLocalDB.exe“ können Sie eine benannte Instanz von LocalDB erstellen, starten und beenden. Weitere Informationen zu SqlLocalDB.exe finden Sie unter [SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md).

```console
REM Create an instance of LocalDB
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" create LocalDBApp1
REM Start the instance of LocalDB
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" start LocalDBApp1
REM Gather information about the instance of LocalDB
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" info LocalDBApp1
```

 Die letzte Zeile oben gibt Informationen ähnlich der folgenden zurück.

|||
|-|-|
|Name|`LocalDBApp1`|
|Versionsoptionen|\<aktuelle Version>|
|Freigegebener Name|""|
|Besitzer|„\<Ihr Windows-Benutzerkonto>“|
|Automatisch erstellen|Nein|
|Status|Ausführen|
|Letzte Startzeit|\<Datum und Uhrzeit>|
|Instanz-Pipename|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|

>[!NOTE]
>Wenn Ihre Anwendung eine Version vor .NET 4.0.2 verwendet, müssen Sie eine direkte Verbindung mit der Named Pipe von LocalDB herstellen. Der Wert des Pipenamens der Instanz ist die Named Pipe, auf die die Instanz von LocalDB lauscht. Der Teil des Pipenamens der Instanz nach LOCALDB# ändert sich jedes Mal, wenn die Instanz von LocalDB gestartet wird. Sie stellen eine Verbindung mit der Instanz von LocalDB mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] her, indem Sie den Pipenamen der Instanz im Feld **Servername** des Dialogfelds **Verbindung herstellen mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]** eingeben. In Ihrem benutzerdefinierten Programm können Sie mit einer Verbindungszeichenfolge ähnlich `SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");` eine Verbindung mit der Instanz von LocalDB herstellen.

### <a name="connect-to-a-shared-instance-of-localdb"></a>Herstellen einer Verbindung mit einer freigegebenen Instanz von LocalDB

Fügen Sie zum Herstellen einer Verbindung mit einer freigegebenen Instanz von LocalDB der Verbindungszeichenfolge `\.\` (umgekehrter Schrägstrich + Punkt + umgekehrter Schrägstrich) hinzu, auf den für die freigegebenen Instanzen reservierten Namespace zu verweisen. Verwenden Sie beispielsweise eine Verbindungszeichenfolge wie `AppData` als Teil der Verbindungszeichenfolge, um eine Verbindung mit einer freigegeben Instanz von LocalDB namens `(localdb)\.\AppData` herzustellen. Benutzer, die eine Verbindung mit einer freigegebenen Instanz von LocalDB herstellen, die sie nicht besitzen, müssen über eine Windows-Authentifizierung oder über einen Anmeldenamen für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung verfügen.

## <a name="troubleshooting"></a>Problembehandlung

Informationen zur Problembehandlung für LocalDB finden Sie unter [Problembehandlung für SQL Server 2012 Express LocalDB](https://social.technet.microsoft.com/wiki/contents/articles/4609.aspx).

## <a name="permissions"></a>Berechtigungen

Eine Instanz von [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] LocalDB ist eine von einem Benutzer zur eigenen Verwendung erstellte Instanz. Jeder Benutzer auf dem Computer kann eine Datenbank mithilfe einer LocalDB-Instanz erstellen, Dateien unter seinem Benutzerprofil speichern und die gemäß den Anmeldeinformationen erlaubten Prozesse ausführen. Der Zugriff auf die LocalDB-Instanz ist standardmäßig auf ihren Besitzer beschränkt. Die in LocalDB enthaltenen Daten sind per Dateisystemzugriff auf die Datenbankdateien geschützt. Wenn die Datenbankdateien eines Benutzers an einem freigegebenen Speicherort gespeichert werden, kann die Datenbank von jedem Benutzer mit Dateisystemzugriff auf diesen Speicherort geöffnet werden, und zwar über die jeweils eigene Instanz von LocalDB. Wenn die Datenbankdateien sich an einem geschützten Speicherort befinden, z. B. dem Datenordner des Benutzers, können nur dieser Benutzer und Administratoren mit Zugriffsrechten für diesen Ordner die Datenbank öffnen. Die LocalDB-Dateien können jeweils nur von einer LocalDB-Instanz geöffnet werden.

>[!NOTE]
>LocalDB wird immer im Sicherheitskontext des Benutzers ausgeführt, d.h., LocalDB wird nie mit den Anmeldeinformationen der lokalen Gruppe „Administratoren“ ausgeführt. Das bedeutet, dass der Zugriff auf alle von einer LocalDB-Instanz verwendeten Datenbankdateien über das eigene Windows-Konto des Benutzers möglich sein muss, unabhängig von der Mitgliedschaft in der lokalen Gruppe „Administratoren“.

## <a name="see-also"></a>Weitere Informationen

[SqlLocalDB-Hilfsprogramm](../../tools/sqllocaldb-utility.md)
