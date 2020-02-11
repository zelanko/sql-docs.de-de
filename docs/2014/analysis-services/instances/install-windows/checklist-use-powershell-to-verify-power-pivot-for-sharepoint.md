---
title: 'Prüfliste: Verwenden von PowerShell zum Überprüfen von PowerPivot für SharePoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 868fb0f7176faf1c1e795b8efe43f8b6d4cdb3f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "76918095"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a>Prüfliste: Überprüfen von PowerPivot für SharePoint mithilfe von PowerShell
  
  [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] -Installations- oder -Wiederherstellungsvorgänge sind erst abgeschlossen, nachdem ein solider Überprüfungstestlauf ausgeführt wurde, durch den die Einsatzbereitschaft der Dienste und Daten bestätigt wird. In diesem Artikel erfahren Sie, wie Sie diese Schritte mit Windows PowerShell ausführen. Jeder Schritt wird in einem eigenen Abschnitt behandelt, sodass Sie direkt zu einer bestimmten Aufgabe wechseln können. Führen Sie z. B. das Skript im Abschnitt [Datenbanken](#bkmk_databases) dieses Themas aus, um die Namen von Dienstanwendung und Inhaltsdatenbanken zu überprüfen, wenn Sie Wartungen oder Sicherungen für sie planen möchten.  
  
|||  
|-|-|  
|![PowerShell-Inhalt](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell-Inhalt")|Ein vollständiges PowerShell-Skript finden Sie am Ende des Themas. Verwenden Sie das vollständige Skript als Ausgangspunkt für die Erstellung eines benutzerdefinierten Skripts, das zur Überwachung der gesamten [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] -Bereitstellung eingesetzt wird.|  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **In diesem Thema**: die überfüllten Elemente im folgenden Inhaltsverzeichnis entsprechen den Bereichen des Diagramms. Das Diagramm veranschaulicht  
  
|||  
|-|-|  
|[Vorbereiten der PowerShell-Umgebung](#bkmk_prerequisites)<br /><br /> [Symptome und empfohlene Aktionen](#bkmk_symptoms)<br /><br /> **(A)** [Analysis Services-Windows-Dienst](#bkmk_windows_service)<br /><br /> **(B)** [powerpivotsystemservice und powerpivotengineservice](#bkmk_engine_and_system_service)<br /><br /> **(C)** [Power Pivot-Dienst Anwendung (en) und](#bkmk_powerpivot_service_application) Proxys<br /><br /> **(D)** [Datenbanken](#bkmk_databases)<br /><br /> [SharePoint-Funktionen](#bkmk_features)<br /><br /> [Zeit Geber Aufträge](#bkmk_timer_jobs)<br /><br /> [Integritäts Regeln](#bkmk_health_rules)<br /><br /> **(E)** [Windows-und ULS-Protokolle](#bkmk_logs)<br /><br /> [MSOLAP-Anbieter](#bkmk_msolap)<br /><br /> [ADOMD.NET-Client Bibliothek](#bkmk_adomd)<br /><br /> [Regeln zur Sammlung von Integritäts Daten](#bkmk_health_collection)<br /><br /> [Lösungen](#bkmk_solutions)<br /><br /> [Manuelle Überprüfungs Schritte](#bkmk_manual)<br /><br /> [Weitere Ressourcen](#bkmk_more_resources)<br /><br /> [Vollständiges PowerShell-Skript](#bkmk_full_script)|![PowerShell-Überprüfung von PowerPivot](../../../sql-server/install/media/ssas-powershell-component-verification.png "PowerShell-Überprüfung von PowerPivot")|  
  
##  <a name="bkmk_prerequisites"></a>Vorbereiten der PowerShell-Umgebung  
 Mithilfe der Schritte in diesem Abschnitt bereiten Sie die PowerShell-Umgebung vor. Je nach Konfiguration der Skriptumgebung sind die Schritte u. U. nicht erforderlich.  
  
 **PowerShell-Berechtigungen**  
  
 Öffnen Sie ein PowerShell-Fenster oder PowerShell ISE (integrierte Skriptumgebung) mit **Administratorrechten**. Wenn Sie Befehle ohne Administratorrechte ausführen, wird eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
 Get-SPLogEvent: Sie müssen **Administratorrechte** für den Computer besitzen, um dieses Cmdlet auszuführen.  
  
 **SharePoint und [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] ** Mond  
  
 Wenn beim Ausführen der zugehörigen SharePoint-Cmdlets eine Fehlermeldung ähnlich der folgenden angezeigt wird, führen Sie den Add-PSSnapin-Befehl aus:  
  
 Die Benennung „Get-PowerPivotSystemService“ **wurde nicht als Name eines Cmdlets**, einer Funktion, einer Skriptdatei oder eines ausführbaren Programms erkannt. Prüfen Sie die Schreibweise des Namens bzw. stellen Sie sicher, dass der Pfad korrekt angegeben wurde, und versuchen Sie es erneut.  
  
```  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
```  
  
 **Windows PowerShell**  
  
 Weitere Informationen zu PowerShell ISE finden Sie unter [Einführung in Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) und [Verwenden von Windows PowerShell zur Verwaltung von SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).  
  
|||  
|-|-|  
|![Allgemeine Anwendungseinstellungen für PowerPivot in SharePoint](../../../sql-server/install/media/ssas-powerpivot-logo.png "Allgemeine Anwendungseinstellungen für PowerPivot in SharePoint")|Die meisten Komponenten in der Zentraladministration können mithilfe des [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Management-Dashboards optional überprüft werden. Um das Dashboard in der Zentraladministration zu öffnen, klicken Sie auf **Allgemeine Anwendungseinstellungen**und dann in **PowerPivot** auf **Management-Dashboard**. Weitere Informationen zum Dashboard finden Sie unter [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).|  
  
##  <a name="bkmk_symptoms"></a>Symptome und empfohlene Aktionen  
 Die folgende Tabelle enthält eine Liste der Symptome oder Probleme und den jeweiligen Abschnitt, in dem Sie Unterstützung für die Problemlösung finden.  
  
|Symptom|Siehe Abschnitt|  
|-------------|-----------------|  
|Datenaktualisierung wird nicht ausgeführt|Lesen Sie den Abschnitt [Timer Jobs](#bkmk_timer_jobs) , und stellen Sie sicher, dass der **Zeitgeberauftrag für die PowerPivot-Onlinedatenaktualisierung** online ist.|  
|Die Daten im Management-Dashboard sind veraltet|Lesen Sie den Abschnitt [Zeitgeberaufträge](#bkmk_timer_jobs) , und stellen Sie sicher, dass der **Zeitgeberauftrag für die Verarbeitung des Management-Dashboards** online ist.|  
|Einige Bereiche des Management-Dashboards|Wenn Sie PowerPivot für SharePoint in einer Farm installieren, die die Topologie der Zentraladministration ohne Excel Services oder PowerPivot für SharePoint aufweist, müssen Sie die Microsoft ADOMD.NET-Clientbibliothek herunterladen und installieren, wenn Sie Vollzugriff auf die integrierten Berichte im PowerPivot-Management-Dashboard erhalten möchten. Einige Berichte im Dashboard verwenden ADOMD.NET für den Zugriff auf interne Daten, die Berichtsdaten zur PowerPivot-Abfrageverarbeitung und zum Serverzustand in der Farm liefern. Siehe den Abschnitt [ADOMD.Net-Clientbibliothek](#bkmk_adomd) und das Thema [Installieren von ADOMD.NET auf Web-Front-End-Servern, auf denen die Zentraladministration ausgeführt wird](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).|  
|\<zukünftige Inhalts>||  
  
##  <a name="bkmk_windows_service"></a>Analysis Services-Windows-Dienst  
 Durch das Skript in diesem Abschnitt wird die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz im SharePoint-Modus überprüft. Überprüfen Sie, ob der Dienst **ausgeführt**wird.  
  
```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
Name              DisplayName                                Status  
----              -----------                                ------  
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running  
```  
  
##  <a name="bkmk_engine_and_system_service"></a>Powerpivotsystemservice und powerpivotengineservice  
 Durch die Skripts in diesem Abschnitt werden die [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] -Systemdienste überprüft. Es gibt einen Systemdienst für eine SharePoint 2013-Bereitstellung und zwei Dienste für eine SharePoint 2010-Bereitstellung.  
  
 **PowerPivotSystemService**  
  
 Überprüfen Sie, ob der Status **Online**ist.  
  
```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
TypeName                                  Status Applications                             Farm  
--------                                  ------ ------------                             ----  
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c  
```  
  
 **PowerPivotEngineService**  
  
> [!NOTE]  
>  Über **springen Sie dieses Skript, wenn** Sie SharePoint 2013 verwenden. Der PowerPivotEngineService ist nicht Teil einer SharePoint 2013-Bereitstellung. Wenn Sie das Get-Power Pivot**Engine**Service-Cmdlet auf SharePoint 2013 ausführen, wird eine Fehlermeldung ähnlich der folgenden angezeigt. Diese Fehlermeldung wird selbst dann zurückgegeben, wenn Sie den Add-PSSnapin-Befehl ausgeführt haben, der im Abschnitt zu den Voraussetzungen in diesem Thema erläutert wird.  
>   
>  Die Benennung "Get-PowerPivotEngineService" wird nicht als Name eines Cmdlets erkannt  
  
 Überprüfen Sie in einer SharePoint 2010-Bereitstellung, ob der Status **Online**ist.  
  
```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```
  
```Output  
TypeName  : SQL Server Analysis Services  
Status    : Online  
Name      : MSOLAP$POWERPIVOT  
Instances : {POWERPIVOT}  
Farm      : SPFarm Name=SharePoint_Config  
```  
  
##  <a name="bkmk_powerpivot_service_application"></a>Power Pivot-Dienst Anwendung (en) und Proxys  
 Überprüfen Sie, ob der Status **Online**ist. Die Excel Services-Anwendung verwendet keine Dienstanwendungs-Datenbank. Folglich gibt das Cmdlet keinen Datenbanknamen zurück. Merken Sie sich die von der [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Dienstanwendung verwendete Datenbank, damit sie im weiter unten beschriebenen Abschnitt zu Datenbanken überprüfen können, ob die Datenbank online ist.  
  
 **PowerPivot und Excel-Dienstanwendung(en)**  
  
 Überprüfen Sie in einer SharePoint 2010-Bereitstellung, ob der Status **Online**ist.  
  
```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database  
Get-SPExcelServiceApplication | Select typename, DisplayName, status  
```
  
```Output  
TypeName          : PowerPivot Service Application  
Name              : PowerPivotServiceApplication1  
Status            : Online  
UnattendedAccount : PowerPivotUnattendedAccount  
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp  
Farm              : SPFarm Name=SharePoint_Config  
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a  
  
TypeName    : Excel Services Application Web Service Application  
DisplayName : Excel Services Application  
Status      : Online  
```  
  
 **Dienst Anwendungs Pool**  
  
> [!NOTE]  
>  Im folgenden Codebeispiel wird zuerst die applicationpool-Eigenschaft der standardmäßigen [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] -Dienstanwendung zurückgegeben. Der Name wird in der Zeichenfolge analysiert und verwendet, um den Status des Anwendungspoolobjekts abzurufen.  
>   
>  Überprüfen Sie, ob der Status **Online**ist. Wenn der Status nicht online ist oder beim Durchsuchen der [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Website "http-Fehler" angezeigt wird, überprüfen Sie, ob die Identitäts Anmelde Informationen in den IIS-Anwendungs Pools weiterhin korrekt sind. Der IIS-Poolname entspricht dem Wert der ID-Eigenschaft, die vom Get-SPServiceApplicationPool-Befehl zurückgegeben wird.  
  
```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)  
$position = $poolname.lastindexof("=")  
$poolname = $poolname.substring($position+1)  
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
Name                           Status ProcessAccountName Id  
----                           ------ ------------------ -------   
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea  
```  
  
 ![Hinweis](../../../reporting-services/media/rs-fyinote.png "note") Der Anwendungs Pool kann auch auf der Seite "zentral Administration" auf der Seite " **Dienst Anwendungen verwalten**" überprüft werden. Klicken Sie auf den Namen der Dienstanwendung und dann im Menüband auf **Eigenschaften** .  
  
 **PowerPivot und Excel Services-Anwendungsproxys**  
  
 Überprüfen Sie, ob der Status **Online**ist.  
  
```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
TypeName                                                 Status UnattendedAccount           DisplayName  
--------                                                 ------ -----------------           -----------  
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1  
Excel Services Application Web Service Application Proxy Online                             Excel Services Application  
```  
  
##  <a name="bkmk_databases"></a>Termin  
 Das folgende Skript gibt den Status der Dienstanwendungs-Datenbanken und aller Inhaltsdatenbanken zurück. Überprüfen Sie, ob der Status **Online**ist.  
  
```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
Name                                                                       Status Server                  TypeName   
----                                                                       ------ ------                  --------   
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase  
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database   
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database  
```  
  
##  <a name="bkmk_features"></a>SharePoint-Funktionen  
 Überprüfen Sie, ob die Website-, Web- und Farmfunktionen online sind.  
  
```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
DisplayName     Status Scope Farm                           
-----------     ------ ----- ----                           
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config  
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config  
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config  
```  
  
##  <a name="bkmk_timer_jobs"></a>Zeit Geber Aufträge  
 Überprüfen Sie, ob die Zeitgeberaufträge **Online**sind. 
  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService wird unter SharePoint 2013 nicht installiert. Folglich werden EngineService-Zeitgeberaufträge in einer SharePoint 2013-Bereitstellung vom Skript nicht aufgelistet.  
  
```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
      Status DisplayName                                                                          LastRunTime          Service                               
------ -----------                                                                          -----------          -------                               
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT  
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT  
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT  
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService  
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService  
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService  
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService  
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService  
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService  
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService  
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService  
```  
  
##  <a name="bkmk_health_rules"></a>Integritäts Regeln  
 Eine SharePoint 2013-Bereitstellung verfügt über weniger Regeln. Eine vollständige Liste der Regeln für jede SharePoint-Umgebung und eine Erläuterung zur Verwendung der Regeln finden Sie unter [Power Pivot-Integritäts Regeln-konfigurieren](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).  
  
```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
Name                          Enabled Summary  
----                          ------- -------           
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled  
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.  
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.  
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash  
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.  
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin  
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.  
```  
  
##  <a name="bkmk_logs"></a>Windows-und ULS-Protokolle  
 **Windows-Ereignisprotokoll**  
  
 Mit dem folgenden Befehl wird das Windows-Ereignisprotokoll nach Ereignissen durchsucht, die sich auf die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz im SharePoint-Modus beziehen. Weitere Informationen zum Deaktivieren von Ereignissen oder Ändern der Ereignis Ebene finden Sie unter [Konfigurieren und Anzeigen von SharePoint-Protokolldateien und Diagnoseprotokollierung &#40;PowerPivot für SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).  
  
 **Dienst Name:** MSOLAP $ Power Pivot  
  
 **Anzeige Name in Windows-Diensten:** SQL Server Analysis Services (Power Pivot)  
  
```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default  
```
  
```Output
TimeGenerated           EntryType Source            Message  
-------------           --------- ------            -------  
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.  
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.  
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.  
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.  
```  
  
 **SharePoint ULS-Protokoll, Letzte 48 Stunden**  
  
 Der folgende Befehl gibt [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Meldungen aus dem ULS-Protokoll zurück, die in den letzten 48 Stunden erstellt wurden. Passen Sie den addhours-Parameter gemäß Ihren Anforderungen an.  
  
```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default  
```  
  
 Die folgende Abwandlung des Befehls gibt nur Protokollereignisse für die Kategorie **Datenaktualisierung** zurück.  
  
```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message  
```
  
```Output
Timestamp   : 4/14/2014 7:15:01 PM  
Area        : PowerPivot Service  
Category    : Data Refresh  
EventID     : 43  
Level       : High  
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77  
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..  
  
Timestamp   : 4/14/2014 7:15:02 PM  
Area        : PowerPivot Service  
Category    : Data Refresh  
EventID     : 99  
Level       : High  
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77  
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to   
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout.   
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the   
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The   
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at   
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...  
```  
  
##  <a name="bkmk_msolap"></a>MSOLAP-Anbieter  
 Überprüfen Sie den MSOLAP-Anbieter. [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]und [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] erfordern MSOLAP. 5.  
  
```powershell
$excelApp = Get-SPExcelServiceApplication  
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
ProviderId ProviderType Description  
---------- ------------ -----------  
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services       
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0   
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0  
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0  
```  
  
 Weitere Informationen finden Sie unter [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) und [Hinzufügen von MSOLAP.5 als vertrauenswürdigen Datenanbieter in Excel Services](https://technet.microsoft.com/library/hh758436.aspx).  
  
##  <a name="bkmk_adomd"></a>ADOMD.NET-Client Bibliothek  
  
```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default  
```
  
```Output
name                                                  version      vendor  
----                                                  -------      ------  
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation  
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation  
```  
  
 Weitere Informationen finden Sie unter [Installieren von ADOMD.NET auf Web-Front-End-Servern, auf denen die Zentraladministration ausgeführt wird](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).  
  
##  <a name="bkmk_health_collection"></a>Regeln zur Sammlung von Integritäts Daten  
 Überprüfen Sie, ob der **Status** auf Online und **Enabled** auf True festgelegt ist.  
  
```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default  
```
  
```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData  
----                         ------ ------- ---------                   ----------------------  
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14  
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14  
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14  
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14  
```  
  
 Weitere Informationen finden Sie unter [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).  
  
##  <a name="bkmk_solutions"></a>Lösungen  
 Wenn die anderen Komponenten online sind, können Sie die Überprüfung der Lösungen überspringen. Wenn die Integritätsregeln jedoch fehlen, überprüfen Sie, ob die beiden Lösungen vorhanden sind und angezeigt werden. Überprüfen Sie, ob die beiden PowerPivot-Lösungen den Status **Online** und **Deployed**haben.  
  
```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default  
```  
  
2013 SharePoint 2013:
  
```Output
Name                                 Status Deployed        DeploymentState DeployedServers  
----                                 ------ --------        --------------- ---------------  
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}  
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}  
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}  
```  
  
SharePoint 2010:
  
```Output
Name                 Status Deployed        DeploymentState DeployedServers   
----                 ------ --------        --------------- ---------------   
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}  
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}  
```  
  
 Weitere Informationen zur Bereitstellung von SharePoint-Lösungen finden Sie unter [Bereitstellen von Lösungspaketen (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).  
  
##  <a name="bkmk_manual"></a>Manuelle Überprüfungs Schritte  
 In diesem Abschnitt werden die Überprüfungsschritte beschrieben, die nicht mithilfe von PowerShell-Cmdlets ausgeführt werden können.  
  
 **Geplante Datenaktualisierung:** Konfigurieren Sie den Aktualisierungs Zeitplan für eine Arbeitsmappe, um **auch so bald wie möglich zu aktualisieren**.  Weitere Informationen finden Sie im Abschnitt "Überprüfen der Datenaktualisierung" unter [Planen der Datenaktualisierung und Datenquellen, die die Windows-Authentifizierung nicht unterstützen &#40;PowerPivot für SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).  
  
##  <a name="bkmk_more_resources"></a>Weitere Ressourcen  
 [Cmdlets für die Verwaltung von Webservern (IIS) in Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).  
  
 [PowerShell zum Überprüfen von Diensten, IIS-Websites und Anwendungs Pool Status in SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).  
  
 [Referenz zu Windows PowerShell für SharePoint 2013](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)  
  
 [Referenz zu Windows PowerShell für SharePoint Foundation 2010](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)  
  
 [Verwalten von Excel Services mit Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)  
  
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
 [Verwenden des Get-evenlog-Cmdlets](https://technet.microsoft.com/library/ee176846.aspx)  
  
##  <a name="bkmk_full_script"></a>Vollständiges PowerShell-Skript  
 Das folgende Skript enthält alle in den vorherigen Abschnitten beschriebenen Befehle. Von dem Skript werden die Befehle in derselben Reihenfolge ausgeführt, in der sie in diesem Thema dargestellt sind. Das Skript enthält einige optionale Varianten der in diesem Thema behandelten Befehle. Diese können verwendet werden, wenn Sie zusätzliche Filter benötigen. Die Varianten sind durch ein Kommentarzeichen (#) deaktiviert. Das Skript enthält außerdem einige Anweisungen zur Überprüfung von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im SharePoint-Modus. Die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Anweisungen sind durch ein Kommentarzeichen (#) deaktiviert.  
  
```powershell
# This script audits services related to PowerPivot for SharePoint  
$starttime = Get-Date  
write-host -foregroundcolor DarkGray StartTime $starttime
  
Write-Host  "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Analysis Services Windows Service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default  
  
Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default  
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section  
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default  
  
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default  
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section  
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default  

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"  
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default  
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance  
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance  

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status
  
#Write-Host ""  
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version  
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)  
$position = $poolname.lastindexof("=")  
$poolname = $poolname.substring($position+1)  
$poolname = $poolname.substring(0,$poolname.length-1)  
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default  
  
#Write-Host ""  
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default  
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default  

Write-Host -ForegroundColor Green "DATABASES"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default  
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default  
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default  

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default  

Write-Host -ForegroundColor Green "health rules"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default  
  
$time = Get-Date  
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time  

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default  
#The following is the same command but with the Inforamtion events filtered out.  
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default  
  
#Write-Host ""  
Write-Host -ForegroundColor Green "ULS Log data"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default  
#the following example filters for the category 'data refresh'  
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message  
  
$time = Get-Date  
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time  

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
$excelApp = Get-SPExcelServiceApplication  
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default  
  
Write-Host -ForegroundColor Green "ADOMD.net client library"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default  
  
Write-Host -ForegroundColor Green "Usage Data Rules"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default  
  
Write-Host -ForegroundColor Green "Solutions"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default  
  
$time = Get-Date  
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
