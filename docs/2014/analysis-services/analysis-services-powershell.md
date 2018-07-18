---
title: Analysis Services-PowerShell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7fe6625cf512586c5f5e42bb4d5d4f601db41a70
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265686"
---
# <a name="analysis-services-powershell"></a>Analysis Services PowerShell
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] schließt einen SQLAS-Anbieter (Analysis Services PowerShell) und Cmdlets ein, damit Sie mithilfe von Windows PowerShell durch Analysis Services-Objekte navigieren und diese verwalten und abfragen können.  
  
 Analysis Services PowerShell besteht aus folgenden Komponenten:  
  
-   `SQLAS`-Anbieter zum Navigieren der AMO-Hierarchie (Analysis Management Object).  
  
-   `Invoke-ASCmd`-Cmdlet zum Ausführen von MDX, DMX oder XMLA-Skripts.  
  
-   Taskbezogene Cmdlets für Routinevorgänge wie Verarbeitung, Rollenverwaltung, Partitionsverwaltung, Sicherung und Wiederherstellung.  
  
## <a name="in-this-article"></a>Inhalt dieses Artikels  
 [Erforderliche Komponenten](#bkmk_prereq)  
  
 [Unterstützte Versionen und Modi von Analysis Services](#bkmk_vers)  
  
 [Authentifizierungsanforderungen und Sicherheitsüberlegungen](#bkmk_auth)  
  
 [Analysis Services-PowerShell-Tasks](#bkmk_tasks)  

Weitere Informationen über Syntax und Beispiele finden Sie unter [Analysis Services PowerShell Reference](/sql/analysis-services/powershell/analysis-services-powershell-reference).

##  <a name="bkmk_prereq"></a> Erforderliche Komponenten  
 Windows PowerShell 2.0 muss installiert sein. Es ist standardmäßig auf neueren Versionen der Windows-Betriebssysteme installiert. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)

<!-- ff637750.aspx above is linked to by:  (http://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 Sie müssen eine SQL Server-Funktion installieren, die das SQL Server PowerShell (SQLPS)-Modul und Clientbibliotheken enthält. Die einfachste Möglichkeit hierzu ist das Installieren von SQL Server Management Studio, das die PowerShell-Funktion und Clientbibliotheken automatisch beinhaltet. Das SQLPS-Modul (SQL Server PowerShell) enthält alle PowerShell-Anbieter und Cmdlets für alle SQL Server-Funktionen, einschließlich des SQLASCmdlets-Moduls und des SQLAS-Anbieters, der zum Navigieren durch die Analysis Services-Objekthierarchie verwendet wird.  
  
 Sie importieren müssen die **SQLPS** Modul vor der Verwendung der `SQLAS` -Anbieter und Cmdlets. Der SQLAS-Anbieter ist eine Erweiterung von der `SQLServer` Anbieter. Es gibt mehrere Möglichkeiten, das SQLPS-Modul zu importieren. Weitere Informationen finden Sie unter [Importieren des SQLPS-Moduls](../../2014/database-engine/import-the-sqlps-module.md).  
  
 Remotezugriff auf eine Analysis Services-Instanz erfordert, dass Sie Remoteverwaltung und Dateifreigabe aktivieren. Weitere Informationen finden Sie unter [Aktivieren der Remoteverwaltung](#bkmk_remote) in diesem Thema.  
  
##  <a name="bkmk_vers"></a> Unterstützte Versionen und Modi von Analysis Services  
 Derzeit wird Analysis Services PowerShell in einer beliebigen Edition von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services unterstützt, die unter Windows Server 2008 R2, Windows Server 2008 SP1 oder Windows 7 ausgeführt wird.  
  
 In der folgenden Tabelle wird die Verfügbarkeit von Analysis Services PowerShell in unterschiedlichen Kontexten angezeigt.  
  
|Kontext|Verfügbarkeit der PowerShell-Funktion|  
|-------------|-------------------------------------|  
|Mehrdimensionale Instanzen und Datenbanken|Unterstützt für lokale und Remoteverwaltung.<br /><br /> Merge-Partition erfordert eine lokale Verbindung.|  
|Tabellarische Instanzen und Datenbanken|Unterstützt für lokale und Remoteverwaltung.<br /><br /> Weitere Informationen finden Sie einen August 2011-Blog zum Thema [Verwalten von tabellarischen Modellen mit PowerShell](http://go.microsoft.com/fwlink/?linkID=227685).|  
|PowerPivot für SharePoint-Instanzen und Datenbanken|Eingeschränkte Unterstützung. Sie können Instanz- und Datenbankinformationen mithilfe von HTTP-Verbindungen und dem SQLAS-Anbieter anzeigen.<br /><br /> Die Verwendung der Cmdlets wird jedoch nicht unterstützt. Verwenden Sie Analysis Services PowerShell nicht, um die PowerPivot-Datenbank im Arbeitsspeicher zu sichern und wiederherzustellen, Rollen hinzuzufügen oder zu entfernen, Daten zu verarbeiten oder beliebige XMLA-Skripts auszuführen.<br /><br /> Zu Konfigurationszwecken verfügt PowerPivot für SharePoint über integrierte PowerShell-Unterstützung, die getrennt bereitgestellt wird. Weitere Informationen finden Sie unter [PowerShell-Referenz für PowerPivot für SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).|  
|Systemeigene Verbindungen zu lokalen Cubes<br /><br /> “Data Source=c:\backup\test.cub”|Wird nicht unterstützt.|  
|HTTP-Verbindungen zu BI-Semantikmodell-Verbindungsdateien (.bism) in SharePoint<br /><br /> "Data Source =http://server/shared_docs/name.bism"|Wird nicht unterstützt.|  
|Eingebettete Verbindungen zu PowerPivot-Datenbanken<br /><br /> “Data Source=$Embedded$”|Wird nicht unterstützt.|  
|Lokaler Serverkontext in gespeicherten Prozeduren für Analysis Services<br /><br /> “Data Source=*”|Wird nicht unterstützt.|  
  
##  <a name="bkmk_auth"></a> Authentifizierungsanforderungen und Sicherheitsüberlegungen  
 Beim Herstellen einer Verbindung mit Analysis Services müssen Sie die Verbindung mithilfe einer Windows-Benutzeridentität herstellen. In den meisten Fällen wird eine Verbindung mithilfe der integrierten Sicherheit von Windows hergestellt. Dabei wird anhand der Identität des aktuellen Benutzers der Sicherheitskontext festgelegt, unter dem Servervorgänge ausgeführt werden. Es werden jedoch zusätzliche Authentifizierungsmethoden verfügbar, wenn Sie den HTTP-Zugriff auf Analysis Services konfigurieren. In diesem Abschnitt wird erklärt, wie anhand des Typs der Verbindung festgelegt wird, welche Authentifizierungsoptionen Sie verwenden können.  
  
 Verbindungen zu Analysis Services werden entweder als systemeigene Verbindungen oder HTTP-Verbindungen eingerichtet. Eine systemeigene Verbindung ist eine direkte Verbindung von einer Clientanwendung zum Server. In einer PowerShell-Sitzung verwendet der PowerShell-Client den OLE DB-Anbieter für Analysis Services, um eine direkte Verbindung mit einer Analysis Services-Instanz herzustellen. Eine systemeigene Verbindung wird immer mithilfe der integrierten Sicherheit von Windows hergestellt, wobei Analysis Services PowerShell als aktueller Benutzer ausgeführt wird. Für Analysis Services wird kein Identitätswechsel unterstützt. Wenn Sie einen Vorgang als ein bestimmter Benutzer ausführen möchten, müssen Sie die PowerShell-Sitzung als dieser Benutzer starten.  
  
 HTTP-Verbindungen werden indirekt über IIS hergestellt, sodass zusätzliche Authentifizierungsmöglichkeiten möglich sind, z. B. die Standardauthentifizierung, um eine Verbindung mit einer Analysis Services-Instanz herzustellen. Da IIS den Identitätswechsel unterstützt, können Sie eine Verbindungszeichenfolge mit Anmeldeinformationen angeben, die IIS beim Herstellen einer Verbindung für den Identitätswechsel verwendet. Zum Angeben von Anmeldeinformationen können Sie den –Credential-Parameter verwenden.  
  
 **Mit den – Credential-Parameter in PowerShell**  
  
 Der –Credential-Parameter verwendet ein PSCredential-Objekt, mit dem ein Benutzername und ein Kennwort angegeben werden. In Analysis Services PowerShell ist der –Credential-Parameter für Cmdlets verfügbar, die eine Verbindungsanforderung an Analysis Services senden. Dies ist anders als bei Cmdlets, die innerhalb des Kontexts einer vorhandenen Verbindung ausgeführt werden. Cmdlets, die eine Verbindungsanforderung senden, sind z. B. Invoke-ASCmd, Backup-ASDatabase und Restore-ASDatabase. Für diese Cmdlets kann der –Credential-Parameter verwendet werden, sofern die folgenden Bedingungen erfüllt sind:  
  
1.  Der Server ist für HTTP-Zugriff konfiguriert. Dies bedeutet, dass IIS die Verbindung behandelt, den Benutzernamen und das Kennwort liest und beim Herstellen einer Verbindung mit Analysis Services einen Identitätswechsel mit dieser Benutzeridentität durchführt. Weitere Informationen finden Sie unter [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
2.  Das virtuelle IIS-Verzeichnis, das für Analysis Services-HTTP-Zugriff erstellt wurde, ist für die Standardauthentifizierung konfiguriert.  
  
3.  Der Benutzername und das Kennwort, die über das Objekt mit den Anmeldeinformationen bereitgestellt werden, können zu einer Windows-Benutzeridentität aufgelöst werden. Analysis Services verwendet diese Identität als aktuellen Benutzer. Falls der Benutzer kein Windows-Benutzer ist oder nicht über ausreichende Berechtigungen zum Durchführen des angeforderten Vorgangs verfügt, tritt für die Anforderung ein Fehler auf.  
  
 Zum Erstellen eines Objekts mit Anmeldeinformationen können Sie das Get-Credential-Cmdlet verwenden, um die Anmeldeinformationen des Operators zu erfassen. Anschließend können Sie das Objekt mit den Anmeldeinformationen für einen Befehl verwenden, der eine Verbindung mit Analysis Services herstellt. Ein möglicher Ansatz wird im folgenden Beispiel veranschaulicht. In diesem Beispiel wird die Verbindung zu einer lokalen Instanz hergestellt, die für den HTTP-Zugriff konfiguriert ist.  
  
```  
PS SQLSERVER:\SQLAS\HTTP_DS> $cred = Get-credential adventureworks\dbadmin  
PS SQLSERVER:\SQLAS\HTTP_DS> Invoke-ASCmd –Inputfile:”c:\discoverconnections.xmla” –Credential:$cred  
```  
  
 Bei Verwendung der Standardauthentifizierung sollten Sie immer HTTPS mit SSL verwenden, damit Benutzernamen und Kennwörter über eine verschlüsselte Verbindung gesendet werden wird. Weitere Informationen finden Sie unter [Konfigurieren von Secure Sockets Layer in IIS 7.0](http://go.microsoft.com/fwlink/?linkID=184299) und [Configure Basic Authentication (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=230776).  
  
 Bedenken Sie, dass Anmeldeinformationen, Abfragen und Befehle, die Sie in PowerShell angeben, unverändert an die Transportschicht übergeben werden. Das Einschließen von vertraulichem Inhalt in die Skripts erhöht das Risiko von Angriffen durch Skripteinschleusung.  
  
 **Angeben eines Kennworts als Microsoft.Secure.String-Objekt**  
  
 Für einige Vorgänge, z. B. die Sicherung und Wiederherstellung, werden Verschlüsselungsoptionen unterstützt, die aktiviert werden, wenn Sie im Befehl ein Kennwort angeben. Das Angeben des Kennworts weist Analysis Services an, die Sicherungsdatei zu verschlüsseln bzw. zu entschlüsseln. In Analysis Services wird dieses Kennwort als sicheres Zeichenfolgenobjekt instanziiert. Im folgenden Beispiel wird veranschaulicht, wie zur Laufzeit ein Kennwort aus dem Operator erfasst wird.  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd = read-host -AsSecureString -Prompt "Password"  
Password: ****  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd -is [System.IDisposable]   
True  
```  
  
 Sie können eine verschlüsselte Datenbankdatei jetzt sichern oder wiederherstellen, indem Sie die Variable $pwd an den Kennwortparameter übergeben. Um ein vollständiges Beispiel anzuzeigen, die diese Darstellung mit anderen Cmdlets kombiniert werden, finden Sie unter [Backup-ASDatabase Cmdlet](/sql/analysis-services/powershell/backup-asdatabase-cmdlet) und [Restore-ASDatabase Cmdlet](/sql/analysis-services/powershell/restore-asdatabase-cmdlet).
  
 Anschließend entfernen Sie sowohl das Kennwort als auch die Variable aus der Sitzung.  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default> Remove-Variable -Name pwd  
```  
  
##  <a name="bkmk_tasks"></a> Analysis Services-PowerShell-Tasks  
 Sie können Analysis Services PowerShell von der Windows PowerShell-Verwaltungsshell oder einer Windows-Eingabeaufforderung ausführen. Das Ausführen der Analysis Services PowerShell in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird nicht unterstützt.  
  
 In diesem Abschnitt werden häufige Tasks für die Verwendung von Analysis Services PowerShell beschrieben.  
  
-   [Laden des Analysis Services-Anbieter und Cmdlets](#bkmk_load)  
  
-   [Aktivieren der Remoteverwaltung](#bkmk_remote)  
  
-   [Herstellen einer Verbindung mit eine Analysis Services-Objekt](#bkmk_connect)  
  
-   [Verwalten des Diensts](#bkmk_admin)  
  
-   [Hier erhalten Sie Hilfe für Analysis Services PowerShell](#bkmk_help)  
  
###  <a name="bkmk_load"></a> Laden des Analysis Services-Anbieter und Cmdlets  
 Der Analysis Services-Anbieter ist eine Erweiterung des SQL Server-Stammanbieters, der verfügbar wird, wenn Sie das SQLPS-Modul importieren. Analysis Services-Cmdlets werden gleichzeitig geladen; Sie können sie auch separat laden, wenn Sie sie ohne den Anbieter verwenden möchten.  
  
-   Führen Sie das Import-module-Cmdlet aus, um SQLPS zu laden, das die ganze Analysis Services PowerShell-Funktionalität umfasst. Wenn Sie das Modul nicht importieren können, können Sie die Ausführungsrichtlinie vorübergehend zu "uneingeschränkt" ändern, um das Modul zu laden. Weitere Informationen finden Sie unter [Importieren des SQLPS-Moduls](../../2014/database-engine/import-the-sqlps-module.md).  
  
    ```  
    Import-module “sqlps”  
    ```  
  
     Verwenden Sie alternativ `import-module “sqlps” –disablenamechecking`, um die Warnung zu nicht genehmigten ausführlichen Namen zu unterdrücken.  
  
-   Wenn Sie nur die taskspezifischen Analysis Services-Cmdlets ohne den Analysis Services-Anbieter oder das Invoke-ASCmd-Cmdlet laden möchten, können Sie das SQLASCmdlets-Modul als unabhängigen Vorgang laden.  
  
    ```  
    Import-module “sqlascmdlets”  
    ```  
  
###  <a name="bkmk_remote"></a> Aktivieren der Remoteverwaltung  
 Bevor Sie Analysis Services PowerShell mit einer Remote-Analysis Services-Instanz verwenden können, müssen Sie zuerst die Remoteverwaltung und die Dateifreigabe aktivieren. Der folgende Fehler gibt ein Firewallkonfigurationsproblem an: "Der RPC-Server ist nicht verfügbar. (Ausnahme von HRESULT: 0x800706BA)”.  
  
1.  Überprüfen Sie, ob sowohl lokale als auch Remotecomputer über die [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]-Versionen der Client- und Servertools verfügen.  
  
2.  Öffnen Sie auf dem Remoteserver, der eine Analysis Services-Instanz hostet, TCP-Port 2383 in Windows-Firewall. Wenn Sie Analysis Services als benannte Instanz installiert haben oder einen benutzerdefinierten Port verwenden, ist die Portnummer anders. Weitere Informationen finden Sie unter [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
3.  Überprüfen Sie auf dem Remoteserver, dass die folgenden Dienste gestartet sind: Remoteprozeduraufrufdienst, (RPC) TCP/IP-NetBIOS Helper-Dienst, Windows-Verwaltungsinstrumentation (WMI)-Dienst, Windows-Remoteverwaltung (WS-Verwaltung)-Dienst.  
  
4.  Starten Sie auf dem Remoteserver das Snap-In Gruppenrichtlinienobjekt-Editor (gpedit.msc).  
  
5.  Öffnen Sie "Computerkonfiguration" > "Administrative Vorlagen" > "Netzwerk" > "Netzwerkverbindungen" >"Windows-Firewall" und dann "Domänenprofil".  
  
6.  Doppelklicken Sie auf **Windows-Firewall: eingehende Remoteverwaltungsausnahme zulassen**Option **aktiviert**, und klicken Sie dann auf **OK**.  
  
7.  Doppelklicken Sie auf **Windows-Firewall: Eingehende Datei- und Druckerfreigabe Ausnahme zulassen**Option **aktiviert**, und klicken Sie dann auf **OK**.  
  
8.  Verwenden Sie die folgenden Cmdlets auf dem lokalen Computer, die den Clienttools, um zu überprüfen, ob Remoteverwaltung, und Ersetzen Sie dabei den tatsächlichen Servernamen für die *Remote-Servername* Platzhalter. Lassen Sie den Instanznamen weg, wenn Analysis Services als Standardinstanz installiert ist. Damit der Befehl funktioniert, müssen Sie zuvor das SQLPS-Modul importiert haben.  
  
    ```  
    PS SQLSERVER:\> cd sqlas  
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 In einigen Fällen können zusätzliche Konfigurationsschritte erforderlich sein. Möglicherweise müssen Sie Folgendes am Remoteserver eingeben, bevor Sie von einem anderen Computer Befehle an ihn ausgeben können:  
  
```  
Enable-psremoting  
```  
  
  
###  <a name="bkmk_connect"></a> Herstellen einer Verbindung mit eine Analysis Services-Objekt  
 Der Analysis Services PowerShell-Anbieter unterstützt die Navigation der Analysis Services-Objekthierarchie und legt den Kontext zum Ausführen von Befehlen fest. Der Anbieter ist eine Erweiterung des SQLSERVER-Stammanbieters, die über das SQLPS-Modul verfügbar ist. Nachdem Sie das SQLPS-Modul geladen haben, können Sie im Pfad navigieren.  
  
 Sie können eine Verbindung mit einer lokalen oder Remote-Instanz herstellen. Einige Cmdlets können jedoch nur auf einer lokalen Instanz (merge-partition) ausgeführt werden. Sie können eine systemeigene Verbindung oder eine HTTP-Verbindung für Analysis Services-Server verwenden, die Sie für HTTP-Zugriff konfiguriert haben. Die folgenden Abbildungen zeigen den Navigationspfad für systemeigene und HTTP-Verbindungen an. Die folgenden Abbildungen zeigen den Navigationspfad für systemeigene und HTTP-Verbindungen an.  
  
 **Systemeigene Verbindungen zu Analysis Services**  
  
 ![Systemeigene Verbindung mit Analysis Services](media/ssas-powershell-nativeconnection.gif "systemeigene Verbindung mit Analysis Services")  
  
 Das folgende Beispiel zeigt, wie eine systemeigene Verbindung verwendet wird, um durch die Objekthierarchie zu navigieren. Vom Anbieter aus können Sie `dir` ausgeben, um Instanzinformationen anzuzeigen. Sie können Objekte dieser Instanz mithilfe von `cd` anzeigen.  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 Sie sollten die folgenden Auflistungen sehen: Assemblys, Datenbanken, Rollen und Ablaufverfolgungen. Wenn Sie weiterhin `cd` und `dir` verwenden, können Sie den Inhalt der einzelnen Auflistungen anzeigen.  
  
 **HTTP-Verbindungen mit Analysis Services**  
  
 ![HTTP-Verbindung mit Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP-Verbindung mit Analysis Services")  
  
 HTTP-Verbindungen sind nützlich, wenn Sie Ihren Server für den HTTP-Zugriff mithilfe der Anweisungen in diesem Thema konfiguriert: [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
 Sofern eine Server-URL des http://localhost/olap/msmdpump.dll, eine Verbindung kann wie folgt aussehen:  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName “http://localhost/olap/msmdpump.dll”  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 Sie sollten die folgenden Auflistungen sehen: Assemblys, Datenbanken, Rollen und Ablaufverfolgungen. Wenn Sie den Inhalt dieser Auflistungen nicht anzeigen können, prüfen Sie die Authentifizierungseinstellungen im virtuellen OLAP-Verzeichnis. Stellen Sie sicher, dass der anonyme Zugriff deaktiviert ist. Wenn Sie Windows-Authentifizierung verwenden, stellen Sie sicher, dass das Windows-Benutzerkonto über Administratorberechtigungen für die Analysis Services-Instanz verfügt.  
  
###  <a name="bkmk_admin"></a> Verwalten des Diensts  
 Überprüfen Sie, ob der Dienst ausgeführt wird. Gibt Status, Namen und Anzeigenamen für SQL Server-Dienste zurück, einschließlich Analysis Services (MSSQLServerOLAPService) und Datenbank-Engine.  
  
```  
Get-service mssql*  
```  
  
 Gibt Eigenschaften zu einem Prozess zurück, einschließlich Prozess-ID, Handleanzahl und Speicherauslastung:  
  
```  
Get-process msmdsrv  
```  
  
 Startet den Dienst neu, wenn Sie das folgende Cmdlet über die Administratorshell ausgeben:  
  
```  
Restart-service mssqlserverolapservice  
```  
  
###  <a name="bkmk_help"></a> Hier erhalten Sie Hilfe für Analysis Services PowerShell  
 Verwenden Sie ein beliebiges der folgenden Cmdlets, um Cmdlet-Verfügbarkeit zu überprüfen und weitere Informationen zu Diensten, Prozessen und Objekten abzurufen.  
  
1.  `Get-help` gibt die integrierte Hilfe für ein Analysis Services-Cmdlet zurück, einschließlich Beispielen:  
  
    ```  
    Get-help invoke-ascmd -examples  
    ```  
  
2.  `Get-command` gibt eine Liste der elf Analysis Services PowerShell-Cmdlets zurück:  
  
    ```  
    get-command –module SQLASCmdlets  
    ```  
  
3.  `Get-member` gibt Eigenschaften oder Methoden eines Dienstes oder eines Prozesses zurück.  
  
    ```  
    Get-service mssqlserverolapservice | get-member –type Property  
    ```  
  
    ```  
    Get-service mssqlserverolapservice | get-member –type Method  
    ```  
  
    ```  
    Get-process msmdsrv | get-member –type Property  
    ```  
  
4.  `Get-member` kann verwendet werden, um Eigenschaften oder Methoden eines Objekts (z. B. AMO-Methoden auf dem Serverobjekt) zurückzugeben, wobei der SQLAS-Anbieter zum Angeben der Serverinstanz verwendet wird.  
  
    ```  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | get-member –type Method  
    ```  
  
5.  `Get-PSdrive` gibt eine Liste der Anbieter zurück, die derzeit installiert sind. Wenn Sie das SQLPS-Modul importiert haben, sehen Sie den `SQLServer`-Anbieter in der Liste (SQLAS ist Teil des SQLServer-Anbieters und wird nie getrennt in der Liste angezeigt):  
  
    ```  
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md)   
 [Verwalten von tabellarischen Modellen mit PowerShell (Blog)](http://go.microsoft.com/fwlink/?linkID=227685)   
 [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
