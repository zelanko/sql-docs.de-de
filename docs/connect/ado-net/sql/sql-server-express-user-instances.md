---
title: SQL Server Express-Benutzerinstanzen
description: Beschreibung der Unterstützung für SQL Server Express-Benutzerinstanzen.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 91b00848fb42c64f1c180019a7618bf649488bd9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896242"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express-Benutzerinstanzen

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server Express Edition (SQL Server Express) unterstützt das Feature „Benutzerinstanz“, das die Verwendung des Microsoft SqlClient-Datenanbieters für SQL Server voraussetzt. Eine Benutzerinstanz ist eine separate Instanz der SQL Server Express-Datenbank-Engine, die von einer übergeordneten Instanz generiert wird. Benutzerinstanzen ermöglichen Benutzern, die keine Administratoren auf ihren lokalen Computern sind, eine Verbindung mit SQL Server Express-Datenbanken herzustellen. Jede Instanz wird im Sicherheitskontext des jeweiligen Benutzers auf instanz- und benutzerbezogener Basis ausgeführt.  
  
## <a name="user-instance-capabilities"></a>Möglichkeiten von Benutzerinstanzen  
Benutzerinstanzen sind nützlich für Benutzer, die Windows unter einem Benutzerkonto mit den geringsten Rechten ausführen, da jeder Benutzer über SQL Server-Systemadministratorrechte (`sysadmin`) für die auf seinem Computer ausgeführte Instanz verfügt, ohne dass er auch als Windows-Administrator fungieren muss. Software, die auf einer Benutzerinstanz mit eingeschränkten Berechtigungen ausgeführt wird, kann keine systemweiten Änderungen vornehmen, da die Instanz von SQL Server Express unter dem nicht zum Administrator gehörigen Windows-Konto des Benutzers und nicht als Dienst ausgeführt wird. Jede Benutzerinstanz ist von ihrer übergeordneten Instanz sowie von allen anderen Benutzerinstanzen, die auf demselben Computer ausgeführt werden, isoliert. Datenbanken, die in einer Benutzerinstanz ausgeführt werden, werden nur im Einzelbenutzermodus geöffnet. Es ist nicht möglich, dass mehrere Benutzer eine Verbindung mit Datenbanken herstellen, die in einer Benutzerinstanz ausgeführt werden. Replikation und verteilte Abfragen sind für Benutzerinstanzen ebenfalls deaktiviert.  
  
Weitere Informationen dazu finden Sie im Abschnitt zu den Benutzerinstanzen in der SQL Server-Onlinedokumentation.  
  
> [!NOTE]
>  Für Benutzer, die bereits Administratoren auf ihren eigenen Computern sind, oder für Szenarien mit mehreren Datenbankbenutzern werden keine Benutzerinstanzen benötigt.  
  
## <a name="enabling-user-instances"></a>Aktivieren von Benutzerinstanzen  
Um Benutzerinstanzen zu generieren, muss eine übergeordnete Instanz von SQL Server Express ausgeführt werden. Benutzerinstanzen werden bei der Installation von SQL Server Express standardmäßig aktiviert. Sie können aber auch von einem Systemadministrator durch Ausführen der gespeicherten Systemprozedur **sp_configure** auf der übergeordneten Instanz explizit aktiviert oder deaktiviert werden.  
  
```sql
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
Das Netzwerkprotokoll für Benutzerinstanzen muss Named Pipes (lokal) sein. Eine Benutzerinstanz kann nicht in einer Remote-Instanz von SQL Server gestartet werden, und SQL Server-Anmeldungen sind nicht zulässig.  
  
## <a name="connecting-to-a-user-instance"></a>Herstellen einer Verbindung mit einer Benutzerinstanz  
Mit den Schlüsselwörtern `User Instance` und `AttachDBFilename`<xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A> kann eine <xref:Microsoft.Data.SqlClient.SqlConnection> eine Verbindung mit einer Benutzerinstanz herstellen. Benutzerinstanzen werden auch von den Eigenschaften <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder>`UserInstance` und `AttachDBFilename` unterstützt.  
  
Beachten Sie Folgendes zum nachstehend gezeigten Beispiel einer Verbindungszeichenfolge:  
  
- Das Schlüsselwort `Data Source` bezieht sich auf die übergeordnete Instanz von SQL Server Express, die die Benutzerinstanz generiert. Die Standardinstanz ist „.\sqlexpress“.  
  
- `Integrated Security` ist auf `true` festgelegt. Um sich mit einer Benutzerinstanz zu verbinden, ist die Windows-Authentifizierung erforderlich. SQL Server-Anmeldungen werden nicht unterstützt.  
  
- `User Instance` ist auf `true` festgelegt, wodurch eine Benutzerinstanz aufgerufen wird. (Standardwert: `false`.)  
  
- Das Schlüsselwort `AttachDbFileName` für Verbindungszeichenfolgen wird zum Anfügen der primären Datenbankdatei (.mdf) verwendet, die den vollständigen Pfadnamen enthalten muss. `AttachDbFileName` entspricht außerdem den Schlüsseln „extended properties“ und „initial file name“ in einer <xref:Microsoft.Data.SqlClient.SqlConnection>-Verbindungszeichenfolge.  
  
- Die Ersetzungszeichenfolge `|DataDirectory|` zwischen senkrechten Strichen bezieht sich auf das Datenverzeichnis der Anwendung, die die Verbindung öffnet. Sie stellt einen relativen Pfad dar, der den Speicherort der MDF- und LDF-Datenbank und der Protokolldateien angibt. Wenn Sie diese Dateien an einem anderen Speicherort ablegen möchten, müssen Sie den vollständigen Pfad zu den Dateien angeben.  
  
```console
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Sie können auch die Eigenschaften <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder><xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> und <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> verwenden, um zur Laufzeit eine Verbindungszeichenfolge zu erstellen.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Verwenden der Ersetzungszeichenfolge &#124;DataDirectory&#124;  
`DataDirectory` wird in Verbindung mit `AttachDbFileName` verwendet, um einen relativen Pfad zu einer Datendatei anzugeben. Damit wird Entwicklern ermöglicht, Verbindungszeichenfolgen zu erstellen, die auf einem relativen Pfad zur Datenquelle basieren. Es muss kein vollständiger Pfad angegeben werden.  
  
Der physische Speicherort, auf den `DataDirectory` zeigt, hängt von der Art der Anwendung ab. In diesem Beispiel befindet sich die anzufügende Datei „Northwind.mdf“ im Ordner „\app_data“ der Anwendung.  
  
```console
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
Wenn `DataDirectory` verwendet wird, kann der resultierende Dateipfad in der Verzeichnisstruktur nicht höher sein als das Verzeichnis, auf das die Ersetzungszeichenfolge zeigt. Wenn beispielsweise c:\AppDirectory\app_data das vollständig erweiterte `DataDirectory` ist, funktioniert die oben gezeigte Beispielverbindungszeichenfolge, weil sie sich unterhalb von c:\AppDirectory befindet. Wenn aber versucht wird, `DataDirectory` als `|DataDirectory|\..\data` anzugeben, wird ein Fehler ausgelöst, weil „\data“ kein Unterverzeichnis von „\AppDirectory“ ist.  
  
Wenn die Verbindungszeichenfolge eine falsch formatierte Ersetzungszeichenfolge hat, wird eine <xref:System.ArgumentException> ausgelöst.  
  
> [!NOTE]
>  <xref:Microsoft.Data.SqlClient> löst die Ersetzungszeichenfolgen in vollständige Pfade für das Dateisystem des lokalen Computers auf. Daher werden Remoteserver-, HTTP- und UNC-Pfadnamen nicht unterstützt. Beim Öffnen der Verbindung wird eine Ausnahme ausgelöst, wenn sich der Server nicht auf dem lokalen Computer befindet.  
  
Beim Öffnen von <xref:Microsoft.Data.SqlClient.SqlConnection> erfolgt eine Umleitung von der standardmäßigen SQL Server Express-Instanz zu einer zur Laufzeit gestarteten Instanz, die unter dem Konto des Aufrufers ausgeführt wird.  
  
> [!NOTE]
>  Es kann nötig sein, den Wert <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> zu erhöhen, da das Laden von Benutzerinstanzen länger als bei normalen Instanzen dauern kann.  
  
Das folgende Codefragment öffnet eine neue `SqlConnection`, zeigt die Verbindungszeichenfolge im Konsolenfenster an und schließt dann die Verbindung beim Verlassen des `using`-Codeblocks.  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
>  Benutzerinstanzen werden im CLR-Code (Common Language Runtime), der innerhalb von SQL Server ausgeführt wird, nicht unterstützt. Eine <xref:System.InvalidOperationException> wird ausgelöst, wenn `Open` für eine <xref:Microsoft.Data.SqlClient.SqlConnection> aufgerufen wird, die `User Instance=true` in der Verbindungszeichenfolge enthält.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Lebensdauer einer Benutzerinstanzverbindung  
Im Gegensatz zu SQL Server-Versionen, die als Dienst ausgeführt werden, müssen SQL Server Express-Instanzen nicht manuell gestartet und beendet werden. Jedes Mal, wenn sich ein Benutzer anmeldet und sich mit einer Benutzerinstanz verbindet, wird die Benutzerinstanz gestartet, falls sie nicht bereits ausgeführt wird. Bei Datenbanken von Benutzerinstanzen ist die Option `AutoClose` so festgelegt, dass die Datenbank nach einem Zeitraum der Inaktivität automatisch heruntergefahren wird. Der gestartete Prozess „sqlservr.exe“ wird nach dem Schließen der letzten Verbindung mit der Instanz mit einem Zeitlimit weiter ausgeführt, sodass er nicht neu gestartet werden muss, wenn vor Ablauf des Zeitlimits eine weitere Verbindung geöffnet wird. Die Benutzerinstanz wird automatisch heruntergefahren, wenn vor Ablauf dieses Zeitlimits keine neue Verbindung geöffnet wird. Ein Systemadministrator für die übergeordnete Instanz kann mit **sp_configure** die **user instance timeout**-Option (Timeout für Benutzerinstanz) ändern und so die Dauer des Timeoutzeitraums für die jeweilige Benutzerinstanz festlegen. Der Standardwert ist 60 Sekunden.  
  
> [!NOTE]
>  Wenn `Min Pool Size` in der Verbindungszeichenfolge mit einem Wert größer als 0 verwendet wird, behält die Verbindungspoolfunktion stets einige wenige geöffnete Verbindungen bei, und die Benutzerinstanz wird nicht automatisch heruntergefahren.  
  
## <a name="how-user-instances-work"></a>Funktionsweise von Benutzerinstanzen  
Wenn eine Benutzerinstanz zum ersten Mal für einen Benutzer generiert wird, werden die Systemdatenbanken **master** und **msdb** zur exklusiven Verwendung durch die Benutzerinstanz aus dem Ordner „Template Data“ in einen Pfad im Verzeichnis des lokalen Anwendungsdatenrepository des Benutzers kopiert. Dieser Pfad ist in der Regel `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Beim Starten einer Benutzerinstanz werden außerdem die **tempdb**-, Protokoll- und Ablaufverfolgungsdateien in dieses Verzeichnis geschrieben. Für die Instanz wird ein Name generiert, der für jeden Benutzer garantiert eindeutig ist.  
  
Standardmäßig werden allen Mitgliedern der Windows-Gruppe „VORDEFINIERT\Benutzer“ Berechtigungen zum Herstellen einer Verbindung in der lokalen Instanz sowie Lese- und Ausführungsberechtigungen für die SQL Server-Binärdateien gewährt. Sobald die Anmeldeinformationen des aufrufenden Benutzers, der die Benutzerinstanz hostet, überprüft wurden, wird dieser Benutzer zum `sysadmin` in dieser Instanz. Für Benutzerinstanzen ist nur der gemeinsame genutzte Speicherbereich aktiviert, was bedeutet, dass nur Vorgänge auf dem lokalen Rechner möglich sind.  
  
Benutzern müssen sowohl Lese- als auch Schreibberechtigungen für die in der Verbindungszeichenfolge angegebenen MDF- und LDF-Dateien erteilt werden.  
  
> [!NOTE]
>  Die MDF- und LDF-Dateien stellen die Datenbank- bzw. Protokolldateien dar. Diese beiden Dateien sind ein zusammengehöriger Satz, weshalb bei Sicherungs- und Wiederherstellungsvorgängen Vorsicht geboten ist. Die Datenbankdatei enthält Informationen über die genaue Version der Protokolldatei. Die Datenbank wird nicht geöffnet, wenn sie mit der falschen Protokolldatei gekoppelt ist.  
  
Um Datenbeschädigungen zu vermeiden, wird eine Datenbank in der Benutzerinstanz mit exklusivem Zugriff geöffnet. Wenn zwei verschiedene Benutzerinstanzen dieselbe Datenbank auf demselben Computer gemeinsam nutzen, muss der Benutzer der ersten Instanz die Datenbank schließen, bevor sie in einer zweiten Instanz geöffnet werden kann.  
  
## <a name="user-instance-scenarios"></a>Szenarien für Benutzerinstanzen  
Benutzerinstanzen bieten Entwicklern von Datenbankanwendungen einen SQL Server-Datenspeicher, der nicht davon abhängt, dass Entwickler über Administratorkonten auf ihren Entwicklungscomputern verfügen. Benutzerinstanzen basieren auf dem Access-/Jet-Modell, bei dem die Datenbankanwendung einfach eine Verbindung mit einer Datei herstellt. Der Benutzer verfügt automatisch über die uneingeschränkten Berechtigungen für alle Datenbankobjekte, ohne dass ein Systemadministrator zum Erteilen von Berechtigungen eingreifen muss. Es ist für Situationen gedacht, in denen der Benutzer ein Benutzerkonto mit den geringsten Rechten nutzt und keine administrativen Rechte auf dem Server oder dem lokalen Rechner hat, jedoch Datenbankobjekte und -anwendungen erstellen muss. Benutzerinstanzen ermöglichen Benutzern, Instanzen zur Laufzeit zu erstellen, die im eigenen Sicherheitskontext und nicht im Sicherheitskontext eines Systemdiensts mit mehr Rechten ausgeführt werden.  
  
> [!IMPORTANT]
>  Benutzerinstanzen dürfen nur in Szenarien zum Einsatz kommen, in denen alle Anwendungen, die sie verwenden, vollständig vertrauenswürdig sind.  
  
Szenarien für Benutzerinstanzen sind u. a.:  
  
- Einzelbenutzeranwendungen, bei denen das Freigeben von Daten nicht erforderlich ist.  
  
- ClickOnce-Bereitstellung. Auf Computern, auf denen .NET Framework 2.0 (oder höher) oder .NET Core 1.0 (oder höher) und SQL Server Express bereits installiert sind, kann das im Rahmen einer ClickOnce-Aktion heruntergeladene Installationspaket installiert und von Benutzern ohne Administratorberechtigung verwendet werden. Beachten Sie, dass ein Administrator SQL Server Express installieren muss, wenn dies Teil des Setups ist. Weitere Informationen finden Sie unter [ClickOnce-Bereitstellung für Windows Forms](https://docs.microsoft.com/dotnet/framework/winforms/clickonce-deployment-for-windows-forms).
  
- Dediziertes ASP.NET-Hosting mithilfe der Windows-Authentifizierung. Eine einzelne SQL Server Express-Instanz kann in einem Intranet gehostet werden. Die Anwendung stellt die Verbindung über das Windows-Konto ASPNET und nicht per Identitätswechsel her. Benutzerinstanzen dürfen nicht in Szenarien mit Drittanbietern oder freigegebenem Hosting verwendet werden, bei denen alle Anwendungen dieselbe Benutzerinstanz gemeinsam nutzen und nicht mehr voneinander isoliert bleiben.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
