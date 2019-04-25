---
title: Anforderungen für die Webanwendung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 22a181aec3eaeeb50f1958f9de1380de7a8a85f7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765198"
---
# <a name="web-application-requirements-master-data-services"></a>Anforderungen für die Webanwendung (Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ist eine Webanwendung, die von den Internetinformationsdiensten (IIS) gehostet wird. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] kann nur mit Internet Explorer (IE) 7 oder höher verwendet werden. Internet Explorer 7 und frühere Versionen, Microsoft Edge und Chrome werden nicht unterstützt.  
  
 Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] zum Erstellen und Konfigurieren der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] konfiguriert IIS auf dem lokalen Computer und eignet sich deshalb besonders für Aufgaben in Verbindung mit der anfänglichen Webkonfiguration. Konfigurieren Sie z.B. eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Umgebung mit einer einzelnen [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung, oder konfigurieren Sie die erste Webanwendung in einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Bereitstellung für horizontales Skalieren. Verwenden Sie IIS-Tools, um komplexere Aufgaben, z. B. das Konfigurieren mehrerer Webserver in einer Bereitstellung für horizontales Skalieren, auszuführen.  
  
> [!NOTE]  
>  Jeder Computer, auf dem Sie Komponenten von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installieren, muss lizenziert werden. Weitere Informationen finden Sie im Endbenutzerlizenzvertrag (End User License Agreement, EULA).  
  
## <a name="requirements"></a>Anforderungen  
  
### <a name="operating-system"></a>Betriebssystem  
 Die folgenden Windows-Betriebssysteme enthalten die Funktionalität der Internetinformationsdienste (IIS), die für die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Webanwendung und den Webdienst erforderlich ist.  
  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer (64-Bit) x64|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (64-Bit) x64|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Business Intelligence (64-Bit) x64|  
|-------------------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------|  
|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2<br /><br /> Windows Server 2008 R2 SP1<br /><br /> Windows 7 Professional, Enterprise und Ultimate<br /><br /> Windows 8.0 Professional, Enterprise und Ultimate|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2<br /><br /> Windows Server 2008 R2 SP1<br /><br /> Windows Server 2012|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2<br /><br /> Windows Server 2008 R2 SP1<br /><br /> Windows Server 2012|  
  
 Eine vollständige Liste der Windows-Betriebssysteme, die für Ihre Edition von Microsoft Intune [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 Um in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung zu arbeiten, muss Silverlight 5 auf dem Clientcomputer installiert sein. Falls Sie nicht über die erforderliche Version von Silverlight verfügen, werden Sie aufgefordert, diese zu installieren, wenn Sie zu einem Bereich der Webanwendung navigieren, in dem sie erforderlich ist. Sie können Silverlight 5 von [hier](https://go.microsoft.com/fwlink/?LinkId=243096)installieren.  
  
### <a name="role-and-role-services-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a>Rolle und Rollendienste (Betriebssysteme Windows Server 2008 oder Windows Server 2008 R2, Windows 7)  
 Unter Windows Server 2008 R2 können Sie den **Server-Manager**in der Microsoft Management Console (MMC) verwenden, um die Rolle **Webserver (IIS)** und die folgenden erforderlichen Rollendienste zu installieren.  
  
> [!NOTE]  
>  Verwenden Sie unter den Betriebssystemen [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] und Windows 7 die Option **Programme und Funktionen** in der Systemsteuerung, um diese Optionen im Dialogfeld **Windows-Funktionen** zu aktivieren.  
  
||  
|-|  
|Web Server<br /><br /> Allgemeine HTTP-Funktionen<br /><br /> Statischer Inhalt<br /><br /> Standarddokument<br /><br /> Verzeichnissuche<br /><br /> HTTP-Fehler<br /><br /> Anwendungsentwicklung<br /><br /> ASP.NET<br /><br /> .NET-Erweiterbarkeit<br /><br /> ISAPI-Erweiterungen<br /><br /> ISAPI-Filter<br /><br /> Integrität und Diagnose<br /><br /> HTTP-Protokollierung<br /><br /> Anforderungsüberwachung<br /><br /> Sicherheit<br /><br /> Windows-Authentifizierung<br /><br /> Anforderungsfilterung<br /><br /> Leistung<br /><br /> Komprimierung statischer Inhalte<br /><br /> Verwaltungstools<br /><br /> IIS-Verwaltungskonsole|  
  
### <a name="role-and-role-services-windows-server-2012-or-windows-8-operating-systems"></a>Rolle und Rollendienste (Betriebssystem Windows Server 2012 oder Windows 8)  
 Unter Windows Server 2012 können Sie den **Server-Manager**in der Microsoft Management Console (MMC) verwenden, um die Rolle **Webserver (IIS)** und die folgenden erforderlichen Rollendienste zu installieren.  
  
> [!NOTE]  
>  Verwenden Sie unter dem Betriebssystem Windows 8 die Option **Programme und Funktionen** in der Systemsteuerung, um diese Optionen im Dialogfeld **Windows-Funktionen** zu aktivieren.  
  
||  
|-|  
|Internetinformationsdienste (IIS)<br /><br /> Webverwaltungstools<br /><br /> IIS-Verwaltungskonsole<br /><br /> WWW (World Wide Web)-Dienste<br /><br /> Anwendungsentwicklung<br /><br /> .NET-Erweiterbarkeit 3.5<br /><br /> .NET-Erweiterbarkeit 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> ISAPI-Erweiterungen<br /><br /> ISAPI-Filter<br /><br /> Allgemeine HTTP-Funktionen<br /><br /> Standarddokument<br /><br /> Verzeichnissuche<br /><br /> HTTP-Fehler<br /><br /> Statischer Inhalt<br /><br /> [Hinweis: Installieren Sie nicht WebDAV-Veröffentlichung]<br /><br /> Integrität und Diagnose<br /><br /> HTTP-Protokollierung<br /><br /> Anforderungsüberwachung<br /><br /> Leistung<br /><br /> Komprimierung statischer Inhalte<br /><br /> Sicherheit<br /><br /> Anforderungsfilterung<br /><br /> Windows-Authentifizierung|  
  
### <a name="features-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a>Funktionen (Betriebssysteme Windows Server 2008 oder Windows Server 2008 R2, Windows 7)  
 Unter [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] oder Windows Server 2008 R2 können Sie den **Server-Manager** verwenden, um die folgenden erforderlichen Funktionen zu installieren.  
  
> [!NOTE]  
>  Verwenden Sie unter den Betriebssystemen [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] und Windows 7 die Option **Programme und Funktionen** in der Systemsteuerung, um diese Optionen im Dialogfeld **Windows-Funktionen** zu aktivieren.  
  
||  
|-|  
|.NET Framework 3.0-Funktionen<br /><br /> WCF-Aktivierung<br /><br /> HTTP-Aktivierung<br /><br /> Nicht-HTTP-Aktivierung<br /><br /> Aktivierungsdienst für Windows-Prozesse<br /><br /> Prozessmodell<br /><br /> .NET-Umgebung<br /><br /> Konfiguration-APIs|  
  
### <a name="features-windows-server-2012-or-windows-8-operating-systems"></a>Funktionen (Betriebssystem Windows Server 2012 oder Windows 8)  
 Unter Windows Server 2012 können Sie den **Server-Manager** verwenden, um die folgenden erforderlichen Funktionen zu installieren.  
  
> [!NOTE]  
>  Verwenden Sie unter dem Betriebssystem Windows 8 die Option **Programme und Funktionen** in der Systemsteuerung, um diese Optionen im Dialogfeld **Windows-Funktionen** zu aktivieren.  
  
||  
|-|  
|.NET Framework 3.5 (einschließlich .NET 2.0 und 3.0)<br /><br /> .NET Framework 4.5 Advanced Services<br /><br /> ASP.NET 4.5<br /><br /> WCF Services<br /><br /> HTTP-Aktivierung [Hinweis: Dies ist erforderlich.]<br /><br /> TCP-Portfreigabe<br /><br /> Aktivierungsdienst für Windows-Prozesse<br /><br /> Prozessmodell<br /><br /> .NET-Umgebung<br /><br /> Konfiguration-APIs|  
  
### <a name="accounts-and-permissions"></a>Konten und Berechtigungen  
  
|Typ|Description|  
|----------|-----------------|  
|Windows-Konto|Sie müssen sich am Webservercomputer mit einem Windows-Konto anmelden, das über die Berechtigung zum Konfigurieren von Windows-Rollen, Rollendiensten und Funktionen sowie zum Erstellen und Verwalten von Anwendungspools, Websites und Webanwendungen in IIS auf dem lokalen Computer verfügt.|  
|Dienstkonto|Wenn Sie die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]erstellen, müssen Sie eine Identität für den Anwendungspool angeben, in dem die Anwendung ausgeführt wird. Dieses Konto kann sich von dem Konto unterscheiden, das beim Erstellen der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank als Dienstkonto angegeben wurde.<br /><br /> Die ID muss einem Domänenbenutzerkonto entsprechen und wird für den Datenbankzugriff zur Datenbankrolle mds_exec in der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Datenbank hinzugefügt. Weitere Informationen finden Sie unter [Datenbankanmeldenamen, -benutzer und -rollen &#40;Master Data Services&#41;](../database-logins-users-and-roles-master-data-services.md). Darüber hinaus wird dieses Konto einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Windows-Gruppe hinzugefügt, z.B. **MDS_ServiceAccounts**, der Berechtigungen für das temporäre Kompilierungsverzeichnis **MDSTempDir** im Dateisystem erteilt wurden. Weitere Informationen finden Sie unter [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md).<br /><br /> Das Anwendungspoolkonto benötigt die VIEW SERVER STATE-Berechtigung, um Serverfehler zu vermeiden. Beispielsweise schlägt der Befehl „MDS-Version überprüfen“ mit einem Serverfehler fehl. Weitere Informationen finden Sie unter [Befehl „MDS-Version überprüfen“ schlägt mit einem Serverfehler in SQL Server 2012 und SQL Server 2014 fehl](https://go.microsoft.com/fwlink/p/?LinkId=526304)|  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von Master Data Services](install-master-data-services.md)   
 [Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)   
 [Webkonfiguration &#40;Seite im Konfigurations-Manager für Master Data Services&#41;](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  
