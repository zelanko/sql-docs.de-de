---
title: Anforderungen für die Webanwendung
description: Informieren Sie sich über die Anforderungen zum Installieren und Ausführen der Master Data Services Webanwendung, die von Internetinformationsdienste gehostet wird.
ms.custom: ''
ms.date: 02/13/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
keywords:
- Master Data Services
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 513e376199c6f53953d49b70eae17f8da916f6bf
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362966"
---
# <a name="web-application-requirements-master-data-services"></a>Anforderungen für die Webanwendung (Master Data Services)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ist eine Webanwendung, die von den Internetinformationsdiensten (IIS) gehostet wird. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] funktioniert nur in Internet Explorer 9 (IE) oder höher. Internet Explorer 8 und frühere Versionen, Microsoft Edge und Chrome werden nicht unterstützt.  

**Anweisungen zum Installieren und Konfigurieren von IIS** finden Sie unter [Installieren und Konfigurieren von IIS](../../master-data-services/master-data-services-installation-and-configuration.md#InstallIIS).
  
 Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] zum Erstellen und Konfigurieren der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] konfiguriert IIS auf dem lokalen Computer und eignet sich deshalb besonders für Aufgaben in Verbindung mit der anfänglichen Webkonfiguration. Konfigurieren Sie z.B. eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Umgebung mit einer einzelnen [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, oder konfigurieren Sie die erste Webanwendung in einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Bereitstellung für horizontales Skalieren. Verwenden Sie IIS-Tools, um komplexere Aufgaben, z. B. das Konfigurieren mehrerer Webserver in einer Bereitstellung für horizontales Skalieren, auszuführen.  
  
> [!NOTE]  
>  Jeder Computer, auf dem Sie Komponenten von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installieren, muss lizenziert werden. Weitere Informationen finden Sie im Endbenutzerlizenzvertrag (End User License Agreement, EULA).  
  
## <a name="requirements"></a>Anforderungen  
  
### <a name="operating-system"></a>Betriebssystem  
 Überprüfen Sie vor der Installation von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]folgende Voraussetzungen:    
    
-   [Hardware- und Softwareanforderungen für die Installation von SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)    
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 Um in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung zu arbeiten, muss Silverlight 5 auf dem Clientcomputer installiert sein. Falls Sie nicht über die erforderliche Version von Silverlight verfügen, werden Sie aufgefordert, diese zu installieren, wenn Sie zu einem Bereich der Webanwendung navigieren, in dem sie erforderlich ist. Sie können Silverlight 5 von [hier](https://go.microsoft.com/fwlink/?LinkId=243096) installieren.  
  
### <a name="role-and-role-services"></a>Rolle und Rollendienste  
 Unter Windows Server 2012 oder Windows Server 2012 R2 können Sie den **Server-Manager**in der Microsoft Management Console (MMC) verwenden, um die Rolle **Webserver (IIS)** und die erforderlichen Rollendienste zu installieren.  
 
 
> [!IMPORTANT]  
>Die**Komprimierung dynamischer Inhalte** ist standardmäßig aktiviert. Dadurch wird die Größe der XML-Antwort erheblich verringert und die Netzwerk-E/A reduziert, obwohl die CPU-Auslastung erhöht wird.  Weitere Klicken Sie informationen finden Sie unter **[CTP 2.0] Verbesserte Leistung** in [What's New in Master Data Services &#40;MDS&#41;](../../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
- Internetinformationsdienste
- Webverwaltungstools
- IIS-Verwaltungskonsole
- WWW (World Wide Web)-Dienste
- Anwendungsentwicklung
- .NET-Erweiterbarkeit 3.5
- .NET-Erweiterbarkeit 4.5
- ASP.NET 3.5
- ASP.NET 4.5
- ISAPI-Erweiterungen
- ISAPI-Filter
- Allgemeine HTTP-Funktionen
- Standarddokument
- Verzeichnissuche
- HTTP-Fehler
- Statischer Inhalt [Hinweis: Installieren Sie die WebDAV-Veröffentlichung nicht.]
- Integrität und Diagnose
- HTTP-Protokollierung
- Anforderungsüberwachung
- Leistung
- Komprimierung statischer Inhalte
- Sicherheit
- Anforderungsfilterung
- Windows-Authentifizierung
  
### <a name="features"></a>Features 
 Unter Windows Server 2012 und Windows Server 2012 R2 können Sie den **Server-Manager** verwenden, um die folgenden erforderlichen Funktionen zu installieren.  
  
- .NET Framework 3.5 (einschließlich .NET 2.0 und 3.0)
- .NET Framework 4.5 Advanced Services
- ASP.NET 4.5
- WCF Services
- HTTP-Aktivierung [Hinweis: Dies ist erforderlich.]
- TCP-Portfreigabe
- Windows-Prozessaktivierungsdienst
- Prozessmodell
- .NET-Umgebung
- Konfiguration-APIs
- Komprimierung dynamischer Inhalte
  
 Nachfolgend finden Sie ein PowerShell-Beispielskript zum Hinzufügen von erforderlichen Serverrollen und -funktionen. Die erforderlichen Serverrollen und -funktionen variieren je nach Umgebung.  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature -Restart  
```  
  
 Weitere Informationen zu PowerShell-Befehlen finden Sie unter [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature).  
  
### <a name="accounts-and-permissions"></a>Konten und Berechtigungen  
  
|type|BESCHREIBUNG|  
|----------|-----------------|  
|Windows-Konto|Sie müssen sich am Webservercomputer mit einem Windows-Konto anmelden, das über die Berechtigung zum Konfigurieren von Windows-Rollen, Rollendiensten und Funktionen sowie zum Erstellen und Verwalten von Anwendungspools, Websites und Webanwendungen in IIS auf dem lokalen Computer verfügt.|  
|Dienstkonto|Wenn Sie die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]erstellen, müssen Sie eine Identität für den Anwendungspool angeben, in dem die Anwendung ausgeführt wird. Dieses Konto kann sich von dem Konto unterscheiden, das beim Erstellen der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank als Dienstkonto angegeben wurde.<br /><br /> Die ID muss einem Domänenbenutzerkonto entsprechen und wird für den Datenbankzugriff zur Datenbankrolle mds_exec in der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank hinzugefügt. Weitere Informationen finden Sie unter [Datenbankanmeldenamen, -benutzer und -rollen](../../master-data-services/database-logins-users-and-roles-master-data-services.md). Darüber hinaus wird dieses Konto einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Windows-Gruppe hinzugefügt, z.B. **MDS_ServiceAccounts**, der Berechtigungen für das temporäre Kompilierungsverzeichnis **MDSTempDir**im Dateisystem erteilt wurden. Weitere Informationen finden Sie unter [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
      
 [Erstellen Sie eine Master Data Manager-Webanwendung &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [Webkonfiguration &#40;Seite im Konfigurations-Manager für Master Data Sevices&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
