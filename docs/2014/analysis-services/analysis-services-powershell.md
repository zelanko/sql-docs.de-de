---
title: Analysis Services PowerShell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4638d02387426dbf6f0fe63b1ff4bded2f4fc62d
ms.sourcegitcommit: f5807ced6df55dfa78ccf402217551a7a3b44764
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493806"
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
  
 [Analysis Services von PowerShell-Tasks](#bkmk_tasks)  

Weitere Informationen zu Syntax und Beispielen finden Sie unter [Analysis Services PowerShell-Referenz](/sql/analysis-services/powershell/analysis-services-powershell-reference).

##  <a name="bkmk_prereq"></a> Erforderliche Komponenten  
 Windows PowerShell 2.0 muss installiert sein. Es ist standardmäßig auf neueren Versionen der Windows-Betriebssysteme installiert. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell 2,0](https://msdn.microsoft.com/library/ff637750.aspx) .

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 Sie müssen eine SQL Server-Funktion installieren, die das SQL Server PowerShell (SQLPS)-Modul und Clientbibliotheken enthält. Die einfachste Möglichkeit hierzu ist das Installieren von SQL Server Management Studio, das die PowerShell-Funktion und Clientbibliotheken automatisch beinhaltet. Das SQLPS-Modul (SQL Server PowerShell) enthält alle PowerShell-Anbieter und Cmdlets für alle SQL Server-Funktionen, einschließlich des SQLASCmdlets-Moduls und des SQLAS-Anbieters, der zum Navigieren durch die Analysis Services-Objekthierarchie verwendet wird.  
  
 Sie müssen das **sqlps** -Modul importieren, bevor Sie den `SQLAS` Anbieter und die Cmdlets verwenden können. Der sqlas-Anbieter ist eine Erweiterung des `SQLServer` Anbieters. Es gibt mehrere Möglichkeiten, das SQLPS-Modul zu importieren. Weitere Informationen finden Sie unter [Importieren des SQLPS-Moduls](../../2014/database-engine/import-the-sqlps-module.md).  
  
 Remotezugriff auf eine Analysis Services-Instanz erfordert, dass Sie Remoteverwaltung und Dateifreigabe aktivieren. Weitere Informationen finden Sie unter [Aktivieren der Remote Verwaltung](#bkmk_remote) in diesem Thema.  
  
##  <a name="bkmk_vers"></a> Unterstützte Versionen und Modi von Analysis Services  
 Derzeit wird Analysis Services PowerShell in einer beliebigen Edition von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services unterstützt, die unter Windows Server 2008 R2, Windows Server 2008 SP1 oder Windows 7 ausgeführt wird.  
  
 In der folgenden Tabelle wird die Verfügbarkeit von Analysis Services PowerShell in unterschiedlichen Kontexten angezeigt.  
  
|Kontext|Verfügbarkeit der PowerShell-Funktion|  
|-------------|-------------------------------------|  
|Mehrdimensionale Instanzen und Datenbanken|Unterstützt für lokale und Remoteverwaltung.<br /><br /> Merge-Partition erfordert eine lokale Verbindung.|  
|Tabellarische Instanzen und Datenbanken|Unterstützt für lokale und Remoteverwaltung.<br /><br /> Weitere Informationen finden Sie im Blog von August 2011 über das [Verwalten von tabellarischen Modellen mit PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).|  
|PowerPivot für SharePoint-Instanzen und Datenbanken|Eingeschränkte Unterstützung. Sie können Instanz- und Datenbankinformationen mithilfe von HTTP-Verbindungen und dem SQLAS-Anbieter anzeigen.<br /><br /> Die Verwendung der Cmdlets wird jedoch nicht unterstützt. Verwenden Sie Analysis Services PowerShell nicht, um die PowerPivot-Datenbank im Arbeitsspeicher zu sichern und wiederherzustellen, Rollen hinzuzufügen oder zu entfernen, Daten zu verarbeiten oder beliebige XMLA-Skripts auszuführen.<br /><br /> Zu Konfigurationszwecken verfügt PowerPivot für SharePoint über integrierte PowerShell-Unterstützung, die getrennt bereitgestellt wird. Weitere Informationen finden Sie unter [PowerShell-Referenz für PowerPivot für SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).|  
|Systemeigene Verbindungen zu lokalen Cubes<br /><br /> "Data Source = c:\backup\test.Cub"|Nicht unterstützt.|  
|HTTP-Verbindungen zu BI-Semantikmodell-Verbindungsdateien (.bism) in SharePoint<br /><br /> "Data Source =http://server/shared_docs/name.bism "|Nicht unterstützt.|  
|Eingebettete Verbindungen zu PowerPivot-Datenbanken<br /><br /> "Data Source = $Embedded $"|Nicht unterstützt.|  
|Lokaler Serverkontext in gespeicherten Prozeduren für Analysis Services<br /><br /> "Data Source = *"|Nicht unterstützt.|  
  
##  <a name="bkmk_auth"></a>Authentifizierungsanforderungen und Sicherheitsüberlegungen  
 Beim Herstellen einer Verbindung mit Analysis Services müssen Sie die Verbindung mithilfe einer Windows-Benutzeridentität herstellen. In den meisten Fällen wird eine Verbindung mithilfe der integrierten Sicherheit von Windows hergestellt. Dabei wird anhand der Identität des aktuellen Benutzers der Sicherheitskontext festgelegt, unter dem Servervorgänge ausgeführt werden. Es werden jedoch zusätzliche Authentifizierungsmethoden verfügbar, wenn Sie den HTTP-Zugriff auf Analysis Services konfigurieren. In diesem Abschnitt wird erklärt, wie anhand des Typs der Verbindung festgelegt wird, welche Authentifizierungsoptionen Sie verwenden können.  
  
 Verbindungen zu Analysis Services werden entweder als systemeigene Verbindungen oder HTTP-Verbindungen eingerichtet. Eine systemeigene Verbindung ist eine direkte Verbindung von einer Clientanwendung zum Server. In einer PowerShell-Sitzung verwendet der PowerShell-Client den OLE DB-Anbieter für Analysis Services, um eine direkte Verbindung mit einer Analysis Services-Instanz herzustellen. Eine systemeigene Verbindung wird immer mithilfe der integrierten Sicherheit von Windows hergestellt, wobei Analysis Services PowerShell als aktueller Benutzer ausgeführt wird. Für Analysis Services wird kein Identitätswechsel unterstützt. Wenn Sie einen Vorgang als ein bestimmter Benutzer ausführen möchten, müssen Sie die PowerShell-Sitzung als dieser Benutzer starten.  
  
 HTTP-Verbindungen werden indirekt über IIS hergestellt, sodass zusätzliche Authentifizierungsmöglichkeiten möglich sind, z. B. die Standardauthentifizierung, um eine Verbindung mit einer Analysis Services-Instanz herzustellen. Da IIS den Identitätswechsel unterstützt, können Sie eine Verbindungszeichenfolge mit Anmeldeinformationen angeben, die IIS beim Herstellen einer Verbindung für den Identitätswechsel verwendet. Zum Bereitstellen von Anmelde Informationen können Sie den-Credential-Parameter verwenden.  
  
 **Verwenden des Parameters "-Credential" in PowerShell**  
  
 Der-Credential-Parameter nimmt ein PSCredential-Objekt an, das einen Benutzernamen und ein Kennwort angibt. In Analysis Services PowerShell steht der-Credential-Parameter für Cmdlets zur Verfügung, die eine Verbindungsanforderung an Analysis Services stellen, im Gegensatz zu Cmdlets, die im Kontext einer vorhandenen Verbindung ausgeführt werden. Cmdlets, die eine Verbindungsanforderung senden, sind z. B. Invoke-ASCmd, Backup-ASDatabase und Restore-ASDatabase. Für diese Cmdlets kann der-Credential-Parameter verwendet werden, vorausgesetzt, dass die folgenden Kriterien erfüllt sind:  
  
1.  Der Server ist für HTTP-Zugriff konfiguriert. Dies bedeutet, dass IIS die Verbindung behandelt, den Benutzernamen und das Kennwort liest und beim Herstellen einer Verbindung mit Analysis Services einen Identitätswechsel mit dieser Benutzeridentität durchführt. Weitere Informationen finden Sie unter [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
2.  Das virtuelle IIS-Verzeichnis, das für Analysis Services-HTTP-Zugriff erstellt wurde, ist für die Standardauthentifizierung konfiguriert.  
  
3.  Der Benutzername und das Kennwort, die über das Objekt mit den Anmeldeinformationen bereitgestellt werden, können zu einer Windows-Benutzeridentität aufgelöst werden. Analysis Services verwendet diese Identität als aktuellen Benutzer. Falls der Benutzer kein Windows-Benutzer ist oder nicht über ausreichende Berechtigungen zum Durchführen des angeforderten Vorgangs verfügt, tritt für die Anforderung ein Fehler auf.  
  
 Zum Erstellen eines Objekts mit Anmeldeinformationen können Sie das Get-Credential-Cmdlet verwenden, um die Anmeldeinformationen des Operators zu erfassen. Anschließend können Sie das Objekt mit den Anmeldeinformationen für einen Befehl verwenden, der eine Verbindung mit Analysis Services herstellt. Ein möglicher Ansatz wird im folgenden Beispiel veranschaulicht. In diesem Beispiel wird die Verbindung zu einer lokalen Instanz hergestellt, die für den HTTP-Zugriff konfiguriert ist.  
  
```  
PS SQLSERVER:\SQLAS\HTTP_DS> $cred = Get-credential adventureworks\dbadmin  
PS SQLSERVER:\SQLAS\HTTP_DS> Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 Bei Verwendung der Standard Authentifizierung sollten Sie immer HTTPS mit SSL verwenden, damit Benutzername und Kennwort über eine verschlüsselte Verbindung gesendet werden. Weitere Informationen finden Sie unter [Konfigurieren von Secure Sockets Layer in IIS 7,0](https://go.microsoft.com/fwlink/?linkID=184299) und Konfigurieren der Standard [Authentifizierung (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).  
  
 Bedenken Sie, dass Anmeldeinformationen, Abfragen und Befehle, die Sie in PowerShell angeben, unverändert an die Transportschicht übergeben werden. Das Einschließen von vertraulichem Inhalt in die Skripts erhöht das Risiko von Angriffen durch Skripteinschleusung.  
  
 **Angeben eines Kennworts als Microsoft. Secure. String-Objekt**  
  
 Für einige Vorgänge, z. B. die Sicherung und Wiederherstellung, werden Verschlüsselungsoptionen unterstützt, die aktiviert werden, wenn Sie im Befehl ein Kennwort angeben. Das Angeben des Kennworts weist Analysis Services an, die Sicherungsdatei zu verschlüsseln bzw. zu entschlüsseln. In Analysis Services wird dieses Kennwort als sicheres Zeichenfolgenobjekt instanziiert. Im folgenden Beispiel wird veranschaulicht, wie zur Laufzeit ein Kennwort aus dem Operator erfasst wird.  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd = read-host -AsSecureString -Prompt "Password"  
Password: ****  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd -is [System.IDisposable]   
True  
```  
  
 Sie können eine verschlüsselte Datenbankdatei jetzt sichern oder wiederherstellen, indem Sie die Variable $pwd an den Kennwortparameter übergeben. Ein umfassendes Beispiel, das diese Abbildung mit anderen Cmdlets kombiniert, finden Sie unter [Backup-asdatabase-Cmdlet](/powershell/module/sqlserver/backup-asdatabase) und [Restore-asdatabase-Cmdlet](/powershell/module/sqlserver/restore-asdatabase).
  
 Anschließend entfernen Sie sowohl das Kennwort als auch die Variable aus der Sitzung.  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default> Remove-Variable -Name pwd  
```  
  
##  <a name="bkmk_tasks"></a>Analysis Services von PowerShell-Tasks  
 Sie können Analysis Services PowerShell von der Windows PowerShell-Verwaltungsshell oder einer Windows-Eingabeaufforderung ausführen. Das Ausführen der Analysis Services PowerShell in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird nicht unterstützt.  
  
 In diesem Abschnitt werden häufige Tasks für die Verwendung von Analysis Services PowerShell beschrieben.  
  
-   [Laden des Analysis Services Anbieters und der Cmdlets](#bkmk_load)  
  
-   [Aktivieren der Remote Verwaltung](#bkmk_remote)  
  
-   [Herstellen einer Verbindung mit einem Analysis Services Objekt](#bkmk_connect)  
  
-   [Verwalten des Dienstanbieter](#bkmk_admin)  
  
-   [Hilfe zum Analysis Services PowerShell](#bkmk_help)  
  
###  <a name="bkmk_load"></a>Laden des Analysis Services Anbieters und der Cmdlets  
 Der Analysis Services-Anbieter ist eine Erweiterung des SQL Server-Stammanbieters, der verfügbar wird, wenn Sie das SQLPS-Modul importieren. Analysis Services-Cmdlets werden gleichzeitig geladen; Sie können sie auch separat laden, wenn Sie sie ohne den Anbieter verwenden möchten.  
  
-   Führen Sie das Import-module-Cmdlet aus, um SQLPS zu laden, das die ganze Analysis Services PowerShell-Funktionalität umfasst. Wenn Sie das Modul nicht importieren können, können Sie die Ausführungsrichtlinie vorübergehend zu "uneingeschränkt" ändern, um das Modul zu laden. Weitere Informationen finden Sie unter [Importieren des SQLPS-Moduls](../../2014/database-engine/import-the-sqlps-module.md).  
  
    ```  
    Import-module "sqlps"  
    ```  
  
     Verwenden Sie alternativ `import-module "sqlps" -disablenamechecking`, um die Warnung zu nicht genehmigten ausführlichen Namen zu unterdrücken.  
  
-   Wenn Sie nur die taskspezifischen Analysis Services-Cmdlets ohne den Analysis Services-Anbieter oder das Invoke-ASCmd-Cmdlet laden möchten, können Sie das SQLASCmdlets-Modul als unabhängigen Vorgang laden.  
  
    ```  
    Import-module "sqlascmdlets"  
    ```  
  
###  <a name="bkmk_remote"></a>Aktivieren der Remote Verwaltung  
 Bevor Sie Analysis Services PowerShell mit einer Remote-Analysis Services-Instanz verwenden können, müssen Sie zuerst die Remoteverwaltung und die Dateifreigabe aktivieren. Der folgende Fehler zeigt ein Problem mit der Firewall-Konfiguration an: "Der RPC-Server ist nicht verfügbar. (Ausnahme von HRESULT: 0x800706BA)".  
  
1.  Überprüfen Sie, ob sowohl lokale als auch Remotecomputer über die [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]-Versionen der Client- und Servertools verfügen.  
  
2.  Öffnen Sie auf dem Remoteserver, der eine Analysis Services-Instanz hostet, TCP-Port 2383 in Windows-Firewall. Wenn Sie Analysis Services als benannte Instanz installiert haben oder einen benutzerdefinierten Port verwenden, ist die Portnummer anders. Weitere Informationen finden Sie unter [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
3.  Überprüfen Sie auf dem Remote Server, ob die folgenden Dienste gestartet wurden:  RPC-Dienst (Remote Procedure CallService), TCP/IP-NetBIOS-hilfdienst, Windows-Verwaltungsinstrumentation (WMI)-Dienst Windows-Remoteverwaltung (WS-Management).  
  
4.  Starten Sie auf dem Remoteserver das Snap-In Gruppenrichtlinienobjekt-Editor (gpedit.msc).  
  
5.  Öffnen Sie "Computerkonfiguration" &gt; "Administrative Vorlagen" &gt; "Netzwerk" &gt; "Netzwerkverbindungen" &gt;"Windows-Firewall" und dann "Domänenprofil".  
  
6.  Doppelklicken Sie **auf Windows-Firewall: Eingehende Remote Verwaltungs Ausnahme**zulassen, wählen Sie **aktiviert**aus, und klicken Sie dann auf **OK**.  
  
7.  Doppelklicken Sie **auf Windows-Firewall: Ausnahme**für eingehende Datei-und Druckerfreigabe zulassen, wählen Sie **aktiviert**aus, und klicken Sie dann auf **OK**.  
  
8.  Verwenden Sie auf dem lokalen Computer mit den-Client Tools die folgenden Cmdlets, um die Remote Verwaltung zu überprüfen. ersetzen Sie dabei den Platzhalter " *Remote Servername* " durch den tatsächlichen Servernamen. Lassen Sie den Instanznamen weg, wenn Analysis Services als Standardinstanz installiert ist. Damit der Befehl funktioniert, müssen Sie zuvor das SQLPS-Modul importiert haben.  
  
    ```  
    PS SQLSERVER:\> cd sqlas  
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 In einigen Fällen können zusätzliche Konfigurationsschritte erforderlich sein. Möglicherweise müssen Sie Folgendes am Remoteserver eingeben, bevor Sie von einem anderen Computer Befehle an ihn ausgeben können:  
  
```  
Enable-psremoting  
```  
  
  
###  <a name="bkmk_connect"></a>Herstellen einer Verbindung mit einem Analysis Services Objekt  
 Der Analysis Services PowerShell-Anbieter unterstützt die Navigation der Analysis Services-Objekthierarchie und legt den Kontext zum Ausführen von Befehlen fest. Der Anbieter ist eine Erweiterung des SQLSERVER-Stammanbieters, die über das SQLPS-Modul verfügbar ist. Nachdem Sie das SQLPS-Modul geladen haben, können Sie im Pfad navigieren.  
  
 Sie können eine Verbindung mit einer lokalen oder Remote-Instanz herstellen. Einige Cmdlets können jedoch nur auf einer lokalen Instanz (merge-partition) ausgeführt werden. Sie können eine systemeigene Verbindung oder eine HTTP-Verbindung für Analysis Services-Server verwenden, die Sie für HTTP-Zugriff konfiguriert haben. Die folgenden Abbildungen zeigen den Navigationspfad für systemeigene und HTTP-Verbindungen an. Die folgenden Abbildungen zeigen den Navigationspfad für systemeigene und HTTP-Verbindungen an.  
  
 **Native Verbindungen mit Analysis Services**  
  
 ![Native Verbindung mit Analysis Services](media/ssas-powershell-nativeconnection.gif "Native Verbindung mit Analysis Services")  
  
 Das folgende Beispiel zeigt, wie eine systemeigene Verbindung verwendet wird, um durch die Objekthierarchie zu navigieren. Vom Anbieter aus können Sie `dir` ausgeben, um Instanzinformationen anzuzeigen. Sie können Objekte dieser Instanz mithilfe von `cd` anzeigen.  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 Die folgenden Sammlungen sollten angezeigt werden: Assemblys, Datenbanken, Rollen und Ablauf Verfolgungen. Wenn Sie weiterhin `cd` und `dir` verwenden, können Sie den Inhalt der einzelnen Auflistungen anzeigen.  
  
 **HTTP-Verbindungen mit Analysis Services**  
  
 ![HTTP-Verbindung mit Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP-Verbindung mit Analysis Services")  
  
 Http-Verbindungen sind nützlich, wenn Sie Ihren Server mit den Anweisungen in diesem Thema für den HTTP-Zugriff konfiguriert haben: [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
 Wenn eine Server-URL http://localhost/olap/msmdpump.dll von angenommen wird, könnte eine Verbindung wie folgt aussehen:  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 Die folgenden Sammlungen sollten angezeigt werden: Assemblys, Datenbanken, Rollen und Ablauf Verfolgungen. Wenn Sie den Inhalt dieser Auflistungen nicht anzeigen können, prüfen Sie die Authentifizierungseinstellungen im virtuellen OLAP-Verzeichnis. Stellen Sie sicher, dass der anonyme Zugriff deaktiviert ist. Wenn Sie Windows-Authentifizierung verwenden, stellen Sie sicher, dass das Windows-Benutzerkonto über Administratorberechtigungen für die Analysis Services-Instanz verfügt.  
  
###  <a name="bkmk_admin"></a>Verwalten des Dienstanbieter  
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
  
###  <a name="bkmk_help"></a>Hilfe zum Analysis Services PowerShell  
 Verwenden Sie ein beliebiges der folgenden Cmdlets, um Cmdlet-Verfügbarkeit zu überprüfen und weitere Informationen zu Diensten, Prozessen und Objekten abzurufen.  
  
1.  `Get-help` gibt die integrierte Hilfe für ein Analysis Services-Cmdlet zurück, einschließlich Beispielen:  
  
    ```  
    Get-help invoke-ascmd -examples  
    ```  
  
2.  `Get-command` gibt eine Liste der elf Analysis Services PowerShell-Cmdlets zurück:  
  
    ```  
    get-command -module SQLASCmdlets  
    ```  
  
3.  `Get-member` gibt Eigenschaften oder Methoden eines Dienstes oder eines Prozesses zurück.  
  
    ```  
    Get-service mssqlserverolapservice | get-member -type Property  
    ```  
  
    ```  
    Get-service mssqlserverolapservice | get-member -type Method  
    ```  
  
    ```  
    Get-process msmdsrv | get-member -type Property  
    ```  
  
4.  `Get-member` kann verwendet werden, um Eigenschaften oder Methoden eines Objekts (z. B. AMO-Methoden auf dem Serverobjekt) zurückzugeben, wobei der SQLAS-Anbieter zum Angeben der Serverinstanz verwendet wird.  
  
    ```  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | get-member -type Method  
    ```  
  
5.  `Get-PSdrive` gibt eine Liste der Anbieter zurück, die derzeit installiert sind. Wenn Sie das SQLPS-Modul importiert haben, sehen Sie den `SQLServer`-Anbieter in der Liste (SQLAS ist Teil des SQLServer-Anbieters und wird nie getrennt in der Liste angezeigt):  
  
    ```  
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md)   
 [Verwalten von tabellarischen Modellen mit PowerShell (Blog)](https://go.microsoft.com/fwlink/?linkID=227685)   
 [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
