---
title: Installation der Eingabeaufforderung von Reporting Services SharePoint-Modus und im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fc1e5ae5d17d45b937a5dd44ab3ea6fe5f8620eb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108779"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a>Installieren des SharePoint-Modus und einheitlichen Modus von Reporting Services über die Eingabeaufforderung
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unterstützt eine Befehlszeileninstallation vom SQL Server-Setupprogramm aus. Dieses Thema enthält mehrere Beispiele für die Installation über die Befehlszeile, die speziell für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]gelten. Eine vollständige Beschreibung der Befehlszeilenoptionen, die für alle SQL Server-Komponenten verfügbar sind, finden Sie unter [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md). Die Befehlszeilenoptionen für das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte werden in diesem Thema nicht behandelt. Informationen zur Befehlszeileninstallation des Add-Ins finden Sie unter [Installieren des Add-Ins mithilfe der Installationsdatei "rsSharePoint.msi"](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint-Modus | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus  
  
## <a name="rsinstallmode-native-mode"></a>RSINSTALLMODE (einheitlicher Modus)  
 Die primäre Eingabeeinstellung zum Installieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist die **/RSINSTALLMODE** -Eingabeeinstellung. Die Einstellung verfügt über zwei Optionen: **DefaultNativeMode** und **FilesOnlyMode**.  
  
 Wenn die SQL Server-Datenbank-Engine in die Installation eingeschlossen wird, lautet der standardmäßige RSINSTALLMODE "DefaultNativeMode". Wird die SQL Server-Datenbank-Engine nicht in die Installation einbezogen, lautet der standardmäßige RSINSTALLMODE "FilesOnlyMode". Wenn Sie "DefaultNativeMode" auswählen, ohne dass die SQL Server-Datenbank-Engine in die Installation einbezogen wird, wird der RSINSTALLMODE bei der Installation automatisch in "FilesOnlyMode" geändert. Weitere Informationen zu den Eingabeeinstellungen finden Sie unter [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a>RSSHPINSTALLMODE (SharePoint-Modus)  
 Die Eingabeeinstellung zum Installieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus ist **/RSSHPINSTALLMODE**. Die Eingabeeinstellung hat eine Option: SharePointFilesOnlyMode. Mit der Option werden alle für den SharePoint-Modus benötigten Dateien installiert, nach der Installation sind jedoch Konfigurationsschritte erforderlich. Die zusätzlichen Konfigurationsschritte werden mithilfe der SharePoint-Zentraladministration ausgeführt. Weitere Informationen finden Sie unter [install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
## <a name="examples-of-sharepoint-mode-installation"></a>Beispiele für die Installation des SharePoint-Modus  
 Im folgenden Beispiel werden SQL Server, der Datenbank-Engine-Dienst und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus sowie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint (RS_SHPWFE) installiert.  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 Im folgenden Beispiel wird nur der SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert.  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 Im folgenden Beispiel werden alle SQL Server-Funktionen, einschließlich des einheitlichen Modus und des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], installiert.  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a>Beispiele für ein Upgrade des SharePoint-Modus  
 Im folgenden Beispiel wird der SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aktualisiert. Das Kennwort des vorhandenen Berichtsserver-Dienstkontos lautet**RSUPGRADEPASSWORD** . RSUPGRADEPASSWORD ist ein Pflichtfeld in einem Upgradeszenario, sofern das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstkonto kein integriertes Konto ist.  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 Das folgende Beispiel kann verwendet werden, um eine Installation des SharePoint-Modus zu aktualisieren, die auf der Architektur für den gemeinsamen SharePoint-Dienst basiert. Im Beispiel wird der ALLOWUPGRADEFORSSRSSHAREPOINTMODE-Schalter verwendet. Der Schalter wird nicht zum Upgrade älterer Versionen benötigt, die nicht auf der Architektur für den gemeinsamen Dienst basieren:  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a>Beispiele für die Installation des einheitlichen Modus  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Sy-p-Parameter](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep)   
 [Installieren von PowerPivot über die Eingabeaufforderung](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
