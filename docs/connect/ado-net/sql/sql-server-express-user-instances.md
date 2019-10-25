---
title: SQL Server Express-Benutzerinstanzen
description: Beschreibt die Unterstützung für SQL Server Express Benutzer Instanzen.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 3b3ac1e395cc1240693ca0dc27324766964e0cfa
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452011"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express-Benutzerinstanzen

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Microsoft SQL Server Express Edition (SQL Server Express) unterstützt die benutzerinstanzfunktion, die nur verfügbar ist, wenn die Microsoft SqlClient-Datenanbieter für SQL Server verwendet wird. Eine Benutzer Instanz ist eine separate Instanz des SQL Server Express Datenbank-Engine, die von einer übergeordneten Instanz generiert wird. Mit Benutzer Instanzen können Benutzer, die keine Administratoren auf Ihren lokalen Computern sind, SQL Server Express Datenbanken anfügen und eine Verbindung mit Ihnen herstellen. Jede Instanz wird im Sicherheitskontext des einzelnen Benutzers ausgeführt, und zwar auf einer einzelnen Instanz pro Benutzer.  
  
## <a name="user-instance-capabilities"></a>Benutzerinstanzfunktionen  
Benutzer Instanzen sind für Benutzer, die unter einem Benutzerkonto mit geringsten Rechten ausgeführt werden, hilfreich, da jeder Benutzer über SQL Server Systemadministrator Berechtigungen (`sysadmin`) für die Instanz verfügt, die auf dem Computer ausgeführt wird, ohne dass Windows ausgeführt werden muss. auch Administrator. Software, die auf einer Benutzer Instanz mit eingeschränkten Berechtigungen ausgeführt wird, kann keine systemweiten Änderungen vornehmen, da die Instanz von SQL Server Express unter dem Windows-Konto des Benutzers ohne Administratorrechte und nicht als Dienst ausgeführt wird. Jede Benutzerinstanz ist von ihrer übergeordneten Instanz sowie von allen anderen Benutzerinstanzen, die auf demselben Computer ausgeführt werden, isoliert. Datenbanken, die auf einer Benutzer Instanz ausgeführt werden, werden nur im Einzelbenutzermodus geöffnet, und es ist nicht möglich, dass mehrere Benutzer eine Verbindung mit Datenbanken herstellen, die auf einer Benutzer Instanz ausgeführt werden. Die Replikation und verteilte Abfragen sind für Benutzer Instanzen ebenfalls deaktiviert.  
  
Weitere Informationen dazu finden Sie im Abschnitt zu den Benutzerinstanzen in der SQL Server-Onlinedokumentation.  
  
> [!NOTE]
>  Benutzer Instanzen sind nicht für Benutzer erforderlich, die bereits als Administratoren auf Ihren eigenen Computern angemeldet sind, oder für Szenarien mit mehreren Datenbankbenutzern.  
  
## <a name="enabling-user-instances"></a>Aktivieren von Benutzer Instanzen  
Zum Generieren von Benutzer Instanzen muss eine übergeordnete Instanz von SQL Server Express ausgeführt werden. Benutzerinstanzen werden bei der Installation von SQL Server Express standardmäßig aktiviert. Sie können aber auch von einem Systemadministrator durch Ausführen der gespeicherten Systemprozedur **sp_configure** auf der übergeordneten Instanz explizit aktiviert oder deaktiviert werden.  
  
```sql
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
Das Netzwerkprotokoll für Benutzer Instanzen muss lokale Named Pipes sein. Eine Benutzer Instanz kann nicht auf einer Remote Instanz von SQL Server gestartet werden, und SQL Server Anmeldungen sind nicht zulässig.  
  
## <a name="connecting-to-a-user-instance"></a>Herstellen einer Verbindung mit einer Benutzerinstanz  
Mit den Schlüsselwörtern `User Instance` und `AttachDBFilename`<xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A> kann eine <xref:Microsoft.Data.SqlClient.SqlConnection> eine Verbindung mit einer Benutzerinstanz herstellen. Benutzer Instanzen werden auch von den Eigenschaften `UserInstance` und `AttachDBFilename` von <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder> unterstützt.  
  
Beachten Sie Folgendes bezüglich der Beispiel Verbindungs Zeichenfolge, die unten dargestellt ist:  
  
- Das `Data Source`-Schlüsselwort verweist auf die übergeordnete Instanz von SQL Server Express, die die Benutzer Instanz erzeugt. Die Standard Instanz ist .\sqlexpress.  
  
- `Integrated Security` ist auf `true` festgelegt. Zum Herstellen einer Verbindung mit einer Benutzer Instanz ist die Windows-Authentifizierung erforderlich. SQL Server Anmeldungen werden nicht unterstützt.  
  
- Der `User Instance` ist auf `true` festgelegt, wodurch eine Benutzer Instanz aufgerufen wird. (Der Standardwert ist `false`.)  
  
- Das Schlüsselwort für die `AttachDbFileName` Verbindungs Zeichenfolge wird verwendet, um die primäre Datenbankdatei (. mdf) anzufügen, die den vollständigen Pfadnamen enthalten muss. `AttachDbFileName` entspricht auch den Schlüsseln "Extended Properties" und "Initial File Name" in einer <xref:Microsoft.Data.SqlClient.SqlConnection>-Verbindungs Zeichenfolge.  
  
- Die in die Pipe-Symbole eingeschlossene `|DataDirectory|` Ersetzungs Zeichenfolge bezieht sich auf das Datenverzeichnis der Anwendung, die die Verbindung öffnet, und stellt einen relativen Pfad bereit, der den Speicherort der MDF-und LDF-Datenbank sowie der Protokolldateien angibt. Wenn Sie diese Dateien an anderer Stelle suchen möchten, müssen Sie den vollständigen Pfad zu den Dateien angeben.  
  
```console
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Sie können <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder> die Eigenschaften <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> und <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> auch verwenden, um zur Laufzeit eine Verbindungs Zeichenfolge zu erstellen.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Verwenden der &#124;DataDirectory&#124; -Ersetzungs Zeichenfolge  
`DataDirectory` wird in Verbindung mit `AttachDbFileName` verwendet, um einen relativen Pfad zu einer Datendatei anzugeben. Damit wird Entwicklern ermöglicht, Verbindungszeichenfolgen zu erstellen, die auf einem relativen Pfad zur Datenquelle basieren. Es muss kein vollständiger Pfad angegeben werden.  
  
Der physische Speicherort, auf den `DataDirectory` verweist, richtet sich nach dem Anwendungstyp. In diesem Beispiel befindet sich die Datei Northwind. mdf, die angefügt werden soll, im Ordner \app_data der Anwendung.  
  
```console
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
Wenn `DataDirectory` verwendet wird, kann der resultierende Dateipfad in der Verzeichnisstruktur nicht höher sein als das Verzeichnis, auf das durch die Ersetzungs Zeichenfolge verwiesen wird. Wenn beispielsweise die vollständig erweiterte `DataDirectory` C:\AppDirectory\app_data ist, funktioniert die oben gezeigte Beispiel Verbindungs Zeichenfolge, da Sie unter "c:\appdirector" liegt. Wenn aber versucht wird, `DataDirectory` als `|DataDirectory|\..\data` anzugeben, wird ein Fehler ausgelöst, weil „\data“ kein Unterverzeichnis von „\AppDirectory“ ist.  
  
Wenn die Verbindungs Zeichenfolge eine nicht ordnungsgemäß formatierte Ersetzungs Zeichenfolge aufweist, wird eine <xref:System.ArgumentException> ausgelöst.  
  
> [!NOTE]
>  <xref:Microsoft.Data.SqlClient> löst die Ersetzungs Zeichenfolgen in vollständige Pfade für das lokale Dateisystem des Computers auf. Daher werden Remote Server-, http-und UNC-Pfadnamen nicht unterstützt. Eine Ausnahme wird ausgelöst, wenn die Verbindung geöffnet wird, wenn sich der Server nicht auf dem lokalen Computer befindet.  
  
Wenn das <xref:Microsoft.Data.SqlClient.SqlConnection> geöffnet ist, wird es von der standardmäßigen SQL Server Express Instanz an eine von der Laufzeit initiierte Instanz umgeleitet, die unter dem Konto des Aufrufers ausgeführt wird.  
  
> [!NOTE]
>  Möglicherweise ist es erforderlich, den <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> Wert zu erhöhen, da das Laden von Benutzer Instanzen länger dauern kann als reguläre Instanzen.  
  
Das folgende Code Fragment öffnet einen neuen `SqlConnection`, zeigt die Verbindungs Zeichenfolge im Konsolenfenster an und schließt dann die Verbindung, wenn der `using` Codeblock beendet wird.  
  
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
>  Benutzer Instanzen werden in Common Language Runtime (CLR)-Code, der in SQL Server ausgeführt wird, nicht unterstützt. Eine <xref:System.InvalidOperationException> wird ausgelöst, wenn `Open` für eine <xref:Microsoft.Data.SqlClient.SqlConnection> aufgerufen wird, die `User Instance=true` in der Verbindungs Zeichenfolge aufweist.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Lebensdauer einer benutzerinstanzverbindung  
Im Gegensatz zu Versionen von SQL Server, die als Dienst ausgeführt werden, müssen SQL Server Express Instanzen nicht manuell gestartet und beendet werden. Jedes Mal, wenn sich ein Benutzer anmeldet und eine Verbindung mit einer Benutzer Instanz herstellt, wird die Benutzer Instanz gestartet, wenn Sie nicht bereits ausgeführt wird. Für Benutzerinstanzdatenbanken wird die `AutoClose`-Option festgelegt, sodass die Datenbank nach einer gewissen Zeit der Inaktivität automatisch heruntergefahren wird. Der Prozess "sqlservr. exe", der gestartet wird, wird für einen begrenzten Timeout Zeitraum ausgeführt, nachdem die letzte Verbindung mit der Instanz geschlossen wurde. Daher muss er nicht neu gestartet werden, wenn eine andere Verbindung geöffnet ist, bevor das Timeout abgelaufen ist. Die Benutzer Instanz wird automatisch heruntergefahren, wenn keine neue Verbindung geöffnet wird, bevor dieser Timeout Zeitraum abgelaufen ist. Ein Systemadministrator für die übergeordnete Instanz kann mit **sp_configure** die **user instance timeout**-Option (Timeout für Benutzerinstanz) ändern und so die Dauer des Timeoutzeitraums für die jeweilige Benutzerinstanz festlegen. Der Standardwert ist 60 Sekunden.  
  
> [!NOTE]
>  Wenn `Min Pool Size` in der Verbindungs Zeichenfolge mit einem Wert größer als 0 (null) verwendet wird, behält der Verbindungspool immer einige geöffnete Verbindungen bei, und die Benutzer Instanz wird nicht automatisch heruntergefahren.  
  
## <a name="how-user-instances-work"></a>Funktionsweise von Benutzer Instanzen  
Wenn eine Benutzerinstanz zum ersten Mal für einen Benutzer generiert wird, werden die Systemdatenbanken **master** und **msdb** zur exklusiven Verwendung durch die Benutzerinstanz aus dem Ordner „Template Data“ in einen Pfad im Verzeichnis des lokalen Anwendungsdatenrepository des Benutzers kopiert. Dieser Pfad ist in der Regel `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Beim Starten einer Benutzerinstanz werden außerdem die **tempdb**-, Protokoll- und Ablaufverfolgungsdateien in dieses Verzeichnis geschrieben. Für die-Instanz wird ein Name generiert, der garantiert für jeden Benutzer eindeutig ist.  
  
Standardmäßig werden allen Mitgliedern der Windows-Gruppe BUILTIN\Users Berechtigungen zum Herstellen einer Verbindung mit der lokalen Instanz sowie Lese-und Ausführungs Berechtigungen für die SQL Server-Binärdateien erteilt. Nachdem die Anmelde Informationen des aufrufenden Benutzers, der die Benutzer Instanz gehostet, überprüft wurden, wird dieser Benutzer zum `sysadmin` dieser Instanz. Nur Shared Memory ist für Benutzer Instanzen aktiviert, was bedeutet, dass nur Vorgänge auf dem lokalen Computer möglich sind.  
  
Benutzern müssen Lese-und Schreibberechtigungen für die MDF-und LDF-Dateien erteilt werden, die in der Verbindungs Zeichenfolge angegeben sind.  
  
> [!NOTE]
>  Die MDF-und LDF-Dateien stellen die Datenbank bzw. die Protokolldateien dar. Diese beiden Dateien sind übereinstimmende Sätze, daher muss bei Sicherungs-und Wiederherstellungs Vorgängen sorgfältig vorgegangen werden. Die Datenbankdatei enthält Informationen über die genaue Version der Protokolldatei, und die Datenbank wird nicht geöffnet, wenn Sie mit der falschen Protokolldatei gekoppelt ist.  
  
Um Daten Beschädigungen zu vermeiden, wird eine Datenbank in der Benutzer Instanz mit exklusivem Zugriff geöffnet. Wenn zwei verschiedene Benutzer Instanzen dieselbe Datenbank auf demselben Computer gemeinsam nutzen, muss der Benutzer auf der ersten Instanz die Datenbank schließen, bevor er in einer zweiten Instanz geöffnet werden kann.  
  
## <a name="user-instance-scenarios"></a>Benutzerinstanzszenarien  
Benutzer Instanzen bieten Entwicklern von Datenbankanwendungen einen SQL Server Datenspeicher, der nicht von Entwicklern abhängig ist, die über Administrator Konten auf ihren Entwicklungs Computern verfügen. Benutzer Instanzen basieren auf dem Access/Jet-Modell, in dem die Datenbankanwendung einfach eine Verbindung mit einer Datei herstellt, und der Benutzer verfügt automatisch über vollständige Berechtigungen für alle Datenbankobjekte, ohne dass ein Systemadministrator eine Gewährung gewähren muss. Griff. Es ist für Situationen geeignet, in denen der Benutzer mit einem Benutzerkonto mit geringsten Rechten (LUA) ausgeführt wird und nicht über Administratorrechte auf dem Server oder dem lokalen Computer verfügt, sondern Datenbankobjekte und Anwendungen erstellen muss. Benutzer Instanzen ermöglichen es Benutzern, Instanzen zur Laufzeit zu erstellen, die unter dem eigenen Sicherheitskontext des Benutzers ausgeführt werden, und nicht im Sicherheitskontext eines privilegierteren System Diensts.  
  
> [!IMPORTANT]
>  Benutzer Instanzen sollten nur in Szenarios verwendet werden, in denen alle Anwendungen, die Sie verwenden, voll vertrauenswürdig sind.  
  
Benutzerinstanzszenarien umfassen Folgendes:  
  
- Alle Einzelbenutzer Anwendungen, bei denen die Datenfreigabe nicht erforderlich ist.  
  
- ClickOnce-Bereitstellung. Auf Computern, auf denen .NET Framework 2.0 (oder höher) oder .NET Core 1.0 (oder höher) und SQL Server Express bereits installiert sind, kann das im Rahmen einer ClickOnce-Aktion heruntergeladene Installationspaket installiert und von Benutzern ohne Administratorberechtigung verwendet werden. Beachten Sie, dass ein Administrator SQL Server Express installieren muss, wenn dieser Teil des Setups ist. Weitere Informationen finden Sie unter [ClickOnce-Bereitstellung für Windows Forms](https://docs.microsoft.com/dotnet/framework/winforms/clickonce-deployment-for-windows-forms).
  
- Dediziertes ASP.net Hosting mithilfe der Windows-Authentifizierung. Eine einzelne SQL Server Express Instanz kann in einem Intranet gehostet werden. Die Anwendung stellt eine Verbindung mit dem ASPNET-Windows-Konto her, nicht mithilfe des Identitäts Wechsels. Benutzer Instanzen sollten nicht für Drittanbieter-oder freigegebene Hostingszenarien verwendet werden, in denen alle Anwendungen dieselbe Benutzer Instanz gemeinsam verwenden und nicht mehr voneinander isoliert bleiben.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
