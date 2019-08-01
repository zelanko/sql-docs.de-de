---
title: Hardware- und Softwareanforderungen für die Installation von SQL Server | Microsoft-Dokumentation
ms.custom: sqlfreshmay19
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Setup [SQL Server], software
- software [SQL Server]
- installing SQL Server, software
- operating systems [SQL Server], SQL Server requirements
- Setup [SQL Server], cross-language support
- operating systems [SQL Server], cross-language support
- network connections [SQL Server], requirements
- disk space [SQL Server], SQL Server installations
- WOW [SQL Server]
- Setup [SQL Server], hardware
- dependencies [SQL Server], SQL Server installations
- cluster hardware requirements [SQL Server]
- endpoints [SQL Server], SQL Server installations
- Internet [SQL Server], SQL Server installations
- hardware [SQL Server]
- Windows on Windows [SQL Server]
- installing SQL Server, hardware
- Setup Configuration Checker
- SCC [SQL Server]
- operating systems [SQL Server]
- space [SQL Server], SQL Server installations
- system configuration checker
- installing SQL Server, cross-language support
- Internet [SQL Server]
- space [SQL Server]
- extended system support [SQL Server]
- 64-bit edition [SQL Server]
- failover clustering [SQL Server]
- failover clustering [SQL Server], hardware requirements
- 32-bit edition [SQL Server]
- locales [SQL Server], SQL Server installations
- cross-language support
- disk space [SQL Server]
- localized SQL Server versions
ms.assetid: 09bcf20b-0a40-4131-907f-b61479d5e4d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54f2bdb3d844a8e5aab947f19f7905173b2cb04f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419571"
---
# <a name="hardware-and-software-requirements-for-installing-sql-server"></a>Hardware- und Softwareanforderungen für die Installation von SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel sind die Mindestanforderungen an die Hardware und Software aufgeführt, um [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] auf dem Windows-Betriebssystem zu installieren und auszuführen. 

[!INCLUDE[sscurrent](../../includes/sssqlv14-md.md)] führt Unterstützung für [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] unter Linux ein. Weitere Informationen finden Sie unter [Installationsleitfaden für die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter Linux](../../linux/sql-server-linux-setup.md#system). 

  
**Probieren Sie es aus:**  
  
-   Download von SQL Server aus dem [**Evaluierungscenter**.](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) 
  
-   Starten eines virtuellen Computers, auf dem [**SQL Server 2017**](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) bereits installiert ist.  
  
**Die folgenden Überlegungen betreffen alle Editionen:**  
  
-   Es wird empfohlen, [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] auf Computern mit dem NTFS- oder ReFS-Dateiformat auszuführen. Die Installation von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] auf einem Computer mit FAT32-Dateisystem wird zwar unterstützt, ist aber nicht empfehlenswert, da sie weniger Sicherheit als eine Installation unter dem NTFS- oder ReFS-Dateisystem bietet.  
  
-   Das[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup blockiert Installationen auf schreibgeschützten, zugeordneten oder komprimierten Laufwerken.  
  
-   Bei der Installation tritt ein Fehler auf, wenn Sie das Setup über eine Remotedesktopverbindung mit den Medien auf einer lokalen Ressource im RDC-Client starten. Für die Remoteinstallation müssen sich die Medien auf einer Netzwerkfreigabe oder lokal auf dem physischen oder virtuellen Computer befinden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsmedien befinden sich entweder auf einer Netzwerkfreigabe, einem zugeordneten Laufwerk, einem lokalen Laufwerk oder werden einem virtuellen Computer als ISO zur Verfügung gestellt.  
  
-   Für die Installation von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] muss .NET 4.6.1 als erforderliche Komponente installiert werden. .NET 4.6.1 wird automatisch vom Setup installiert, wenn [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ausgewählt wird.  
  
-   Beim[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup werden die folgenden vom Produkt benötigten Softwarekomponenten installiert:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setuphilfsdateien  
  
-   Die Mindestanforderungen an die Version zum Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter [!INCLUDE[win8srv](../../includes/win8srv-md.md)] oder [!INCLUDE[win8](../../includes/win8-md.md)] finden Sie unter [Installieren von SQL Server unter Windows Server 2012 oder Windows 8](https://support.microsoft.com/kb/2681562).  
  
##  <a name="hwswr"></a> Hardware- und Softwareanforderungen  
Die folgenden Anforderungen gelten für alle Installationen:  
  
|Komponente|Anforderung|  
|---------------|-----------------|  
|.NET Framework|[!INCLUDE[sql2016](../../includes/sssql15-md.md)] RC1 und höher erfordern [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 für die Datenbank-Engine, die Master Data Services oder die Replikation. SQL Server-Setup installiert [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] automatisch. Sie können [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] auch manuell von der Seite [Microsoft .NET Framework 4.6 (Web Installer) für Windows](https://support.microsoft.com/kb/3045560)aus installieren.<br/><br/>[!INCLUDE[sql2019](../../includes/sssqlv15-md.md)] erfordert .NET Framework 4.6.2. .NET Framework ist im [Download Center](https://www.microsoft.com/download/details.aspx?id=53344) verfügbar.<br/><br/> Weitere Informationen, Empfehlungen und Anleitungen zu [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](https://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]und [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)] erfordern [KB2919355](https://support.microsoft.com/kb/2919355) vor der Installation von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6.|  
|Netzwerksoftware|Die unterstützten Betriebssysteme für [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] verfügen über integrierte Netzwerksoftware. Benannte Instanzen und Standardinstanzen einer eigenständigen Installation unterstützen die folgenden Netzwerkprotokolle: Freigegebener Arbeitsspeicher, Named Pipes, TCP/IP und VIA.<br/><br/> **Hinweis:** Das VIA-Protokoll wird auf Failoverclustern nicht unterstützt. Clients oder Anwendungen, die auf demselben Knoten des Failoverclusters wie die SQL Server-Instanz ausgeführt werden, können das Shared Memory-Protokoll verwenden, um eine Verbindung zum SQL Server über dessen lokale Pipeadresse herzustellen. Diese Art der Verbindung ist jedoch nicht clusterfähig und schlägt nach einem Failover der Instanz fehl. Deswegen wird sie nicht empfohlen und sollte nur in sehr speziellen Szenarien verwendet werden.<br/><br/> **Wichtig:** Das VIA-Protokoll ist veraltet. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br/><br/> Weitere Informationen zu Netzwerkprotokollen und Netzwerkbibliotheken finden Sie unter [Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md).|  
|Festplatte|[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] erfordert mindestens 6 GB verfügbaren Festplattenspeicher.<br/><br/> Der erforderliche freie Festplattenspeicher ist von den installierten [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] -Komponenten abhängig. Weitere Informationen finden Sie unter [Anforderungen an den Festplattenspeicherplatz](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace) weiter unten in diesem Artikel. Informationen zu unterstützten Speichertypen für Datendateien finden Sie unter [Speichertypen für Datendateien](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes).|  
|Laufwerk|Ein DVD-Laufwerk ist erforderlich, falls die Installation von einem DVD-Medium erfolgt.|  
|Monitor|[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] erfordert eine Super VGA-Grafikkarte mit einer Mindestauflösung von 800x600 Pixel.|  
|Internet|Zur Nutzung des Internets ist ein Internetzugang erforderlich (möglicherweise gebührenpflichtig).|  
  
> [!NOTE]
> Wegen des Virtualisierungsaufwands ist das Ausführen von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] auf einer VM langsamer als das systeminterne Ausführen.  
  
> [!IMPORTANT]
> Es gibt zusätzliche Hardware- und Softwareanforderungen für die PolyBase-Funktion. Weitere Informationen finden Sie unter [Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)(Erste Schritte mit PolyBase).  
  
##  <a name="pmosr"></a> Anforderungen an Prozessor, Arbeitsspeicher und Betriebssystem  
 Der folgende Arbeitsspeicher- und Prozessoranforderungen gelten für alle Editionen von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]:  
  
|Komponente|Anforderung|  
|---------------|-----------------|  
|Arbeitsspeicher \*|**Minimum:**<br/><br/> Express-Editionen: 512 MB<br/><br/> Alle anderen Editionen: 1 GB<br/><br/> **Empfohlen:**<br/><br/> Express-Editionen: 1 GB<br/><br/> Alle anderen Editionen: Mindestens 4 GB. Mit zunehmender Datenbankgröße sollte außerdem der Speicher erhöht werden, um eine optimale Leistung sicherzustellen.|  
|Prozessorgeschwindigkeit:|**Mindestens:** x64-Prozessor: 1,4 GHz<br/><br/> **Empfohlen:** 2,0 GHz oder schneller|  
|Prozessortyp|x64-Prozessor: AMD Opteron, AMD Athlon 64, Intel Xeon mit Intel EM64T-Unterstützung, Intel Pentium IV mit EM64T-Unterstützung|  
  
> [!NOTE]  
> Die Installation von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] wird nur auf x64-Prozessoren unterstützt. Es wird nicht mehr auf x86 Prozessoren unterstützt.  
  
 \* Zur Installation der [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]-Komponente in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) sind mindestens 2 GB RAM erforderlich. Dies unterscheidet sich von den Arbeitsspeichermindestanforderungen von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]. Informationen zum Installieren von DQS finden Sie unter [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 **WOW64-Unterstützung:**  
  
 WOW64 (Windows 32-bit on Windows 64-bit) ist eine Funktion von 64-Bit-Editionen von Windows, die es ermöglicht, 32-Bit-Anwendungen systemintern im 32-Bit-Modus auszuführen. Anwendungen sind im 32-Bit-Modus funktionsfähig, obwohl es sich beim zugrunde liegenden Betriebssystem um ein 64-Bit-Betriebssystem handelt. WOW64 wird nicht für [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] -Installationen unterstützt. Allerdings werden Verwaltungstools in WOW64 unterstützt.  


**Server Core-Unterstützung:**

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions" 

Installationen von SQL Server 2019 werden im Server Core-Modus folgender Windows Server-Editionen unterstützt:

|                              |                                |
| :------------------------    | :------------------------------|
| Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| Windows Server 2016 Standard | Windows Server 2016 Datacenter |
   | &nbsp; | &nbsp; |

::: moniker-end

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"

Installationen von SQL Server 2016 und 2017 werden im Server Core-Modus folgender Windows Server-Editionen unterstützt:

|                              |                                |
| :------------------------    | :------------------------------|
| Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| Windows Server 2012 R2 Standard | Windows Server 2012 R2 Datacenter|
| Windows Server 2012 Standard | Windows Server 2012 Datacenter |
| Windows Server 2008 R2 SP1 Standard | Windows Server 2008 R2 SP1 Datacenter |
| Windows Server 2008 R2 SP1 Enterprise | Windows Server 2008 R2 SP1 Web|
   | &nbsp; | &nbsp; |
::: moniker-end

Weitere Informationen zum Installieren von SQL Server unter Server Core finden Sie unter [Installieren von SQL Server unter Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md).  

  
### <a name="features-supported-on-32-bit-client-operating-systems"></a>Unterstützte Funktionen auf 32-Bit-Clientbetriebssystemen  
 Windows-Clientbetriebssystemen, z.B. Windows 10 und Windows 8.1, sind als 32-Bit- oder 64-Bit-Architekturen verfügbar.   Alle SQL Server-Funktionen werden auf 64-Bit-Clientbetriebssystemen unterstützt. Microsoft unterstützt auf 32-Bit-Clientbetriebssystemen die folgenden Funktionen:  
  
-   Data Quality Client
-   Konnektivität der Clienttools
-   Integration Services
-   Abwärtskompatibilität der Clienttools
-   Clienttools SDK
-   Dokumentationskomponenten
-   Distributed Replay-Komponenten
-   Distributed Replay Controller
-   Distributed Replay Client
-   SQL Client Connectivity SDK
  
 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] und höhere Server-Betriebssysteme sind nicht als 32-Bit-Architektur verfügbar. Alle unterstützten Serverbetriebssysteme sind nur als 64-Bit verfügbar. Alle Funktionen werden auf 64-Bit-Serverbetriebssystemen unterstützt.  
  
###  <a name="TOP_Principal"></a> Betriebssystemkompatibilität   

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions" 
Die folgende Tabelle zeigt, welche Editionen von SQL Server 2019 mit welchen Windows-Versionen kompatibel sind:  
  

| SQL Server-Edition:               | Enterprise | Entwickler | Standard | Web | Express |  
| :------------------------         | :--------- | :-------- | :------- | :-- | :------ | 
| Windows Server 2019 Datacenter    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2019 Standard      |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2019 Essentials    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2016 Datacenter    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2016 Standard      |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2016 Essentials    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| &nbsp; | &nbsp; |
::: moniker-end

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"

Die folgende Tabelle zeigt, welche Editionen von SQL Server 2016 und 2017 mit welchen Windows-Versionen kompatibel sind:  
  
| SQL Server-Edition:               | Enterprise | Entwickler | Standard | Web | Express |  
| :------------------------         | :--------- | :-------- | :------- | :-- | :------ | 
| Windows Server 2019 Datacenter    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2019 Standard      |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2019 Essentials    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2016 Datacenter    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2016 Standard      |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2016 Essentials    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 R2 Datacenter |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 R2 Standard   |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 R2 Essentials |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 R2 Foundation |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 Datacenter    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 Standard      |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 Essentials    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows Server 2012 Foundation    |    Ja     |    Ja    |    Ja   | Ja |   Ja   |
| Windows 10 IoT Enterprise         |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 10 Enterprise             |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 10 Professional           |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 10 Home                   |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 8.1 Enterprise            |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 8.1 Pro                   |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 8.1 Enterprise            |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 8 Pro                     |    Nein      |    Ja    |    Ja   | Nein  |   Ja   |
| Windows 8                         |    Nein      |    Ja    |    Ja   | Nein  |   Ja   | 

> [!NOTE]  
> Ausnahmen für die Betriebssystemunterstützung, die in diesem Abschnitt erwähnt wurden, sind die folgenden Business Intelligence-Funktionen für [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und früher, die auf Windows Server 2008 R2 SP1 oder höher installiert werden können.  
>  
>-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] – SharePoint  
>-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte  
::: moniker-end


  
##  <a name="CrossLanguageSupport"></a> Sprachübergreifende Unterstützung  
 Weitere Informationen zu sprachübergreifender Unterstützung und Überlegungen zur Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in lokalisierten Sprachen finden Sie unter [Lokale Sprachversionen in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
##  <a name="HardDiskSpace"></a> Anforderungen an den Festplattenspeicherplatz  
 Während der Installation von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]erstellt Windows Installer temporäre Dateien auf dem Systemlaufwerk. Überprüfen Sie, ob Sie über mindestens 6,0 GB freien Speicherplatz auf dem Systemlaufwerk für diese Dateien verfügen, bevor Sie Setup ausführen, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren oder zu aktualisieren. Diese Anforderung gilt auch dann, wenn Sie Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Nichtstandard-Laufwerk installieren.  
  
 Die tatsächlichen Anforderungen für den Festplattenspeicherplatz basieren auf der Systemkonfiguration und den Funktionen, die Sie installieren möchten. In der folgenden Tabelle sind die Speicherplatzanforderungen für die Komponenten von [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] aufgeführt.  
  
|**Feature**|**Erforderlicher Speicherplatz**|  
|-----------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] und Datendateien, Replikation, Volltextsuche und Data Quality Services|1480 MB|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (wie oben beschrieben) mit R-Services (datenbankintern)|2744 MB|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (wie oben beschrieben) mit dem PolyBase-Abfragedienst für externe Daten|4194 MB|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und Datendateien|698 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|967 MB|  
|[!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] (Eigenständig)|280 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] – SharePoint|1203 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte|325 MB|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|121 MB|  
|Konnektivität der Clienttools|328 MB|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|306 MB|  
|Clientkomponenten (außer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation und Integration Services-Tools)|445 MB|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|280 MB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Onlinedokumentation zum Anzeigen und Verwalten von Hilfeinhalten*|27 MB|  
|Alle Funktionen|8030 MB|  
  
 *Die Onlinedokumentation erfordert 200 MB Festplattenspeicherplatz.  
  
##  <a name="StorageTypes"></a> Speichertypen für Datendateien  
 Für Datendateien werden folgende Speichertypen unterstützt:  
  
-   Lokaler Datenträger 
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt aktuell Laufwerke, die standardmäßig eine native Sektorgröße von 512 Byte und 4 KB haben.  Festplatten mit einer Sektorgröße von mehr als 4 KB führen möglicherweise zu Fehlern, wenn versucht wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datendateien darauf zu speichern.  Weitere Informationen zur Unterstützung von Festplattensektorgrößen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Begrenzungen der Unterstützung von Festplattensektorgrößen in SQL Server](https://support.microsoft.com/kb/926930). 
    - Bei der[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstallation wird nur der lokale Datenträger zum Installieren der tempdb-Dateien unterstützt. Stellen Sie sicher, dass der für die tempdb-Daten und die Protokolldateien angegebene Pfad auf allen Clusterknoten gültig ist. Sind die tempdb-Verzeichnisse auf dem Failoverzielknoten während des Failovers nicht verfügbar, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource nicht online geschaltet.
-   Freigegebener Speicher  
-   [Direkte Speicherplätze \(S2D\)](https://technet.microsoft.com/windows-server-docs/storage/storage-spaces/storage-spaces-direct-overview)  
-   SMB-Dateifreigabe  
    - Der SMB-Speicher wird bei eigenständigen oder gruppierten Installationen nicht für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datendateien unterstützt. Verwenden Sie stattdessen den direkt angeschlossenen Speicher, ein SAN (Storage Area Network) oder S2D. 
    - Der SMB-Speicher kann von einem Windows File Server oder einem SMB-Speichergerät eines Drittanbieters gehostet werden. Bei Verwendung von Windows File Server sollte die Windows File Server-Version 2008 oder höher verwendet werden. Weitere Informationen zum Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit SMB-Dateifreigabe als Speicheroption finden Sie unter [Installieren von SQL Server mit SMB-Dateifreigabe als Speicheroption](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md)aufgeführt.  
  
  
  
##  <a name="DC_support"></a> Die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Domänencontroller  
 Aus Sicherheitsgründen sollte [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] nicht auf einem Domänencontroller installiert werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup wird die Installation auf einem Computer, der als Domänencontroller fungiert, nicht blockieren, es gelten jedoch die folgenden Einschränkungen:  
  
-   Sie können keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste auf einem Domänencontroller unter einem lokalen Dienstkonto ausführen.    
-   Nachdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer installiert wurde, können Sie den Computer nicht von einem Domänenmitglied zu einem Domänencontroller ändern. Sie müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, bevor Sie den Hostcomputer zu einem Domänencontroller ändern.    
-   Nachdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer installiert wurde, können Sie den Computer nicht von einem Domänencontroller zu einem Domänenmitglied ändern. Sie müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, bevor Sie den Hostcomputer zu einem Domänenmitglied ändern.   
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden nicht unterstützt, wenn es sich bei den Clusterknoten um Domänencontroller handelt.   
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird auf einem schreibgeschützten Domänencontroller nicht unterstützt. Beim Setup von[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können keine Sicherheitsgruppen erstellt oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonten für einen schreibgeschützten Domänencontroller bereitgestellt werden. In diesem Szenario tritt ein Setupfehler auf. 
- Eine Failoverclusterinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird in einer Umgebung, in der nur auf einen schreibgeschützten Domänencontroller zugegriffen werden kann, nicht unterstützt. 
  
## <a name="see-also"></a>Weitere Informationen  
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   

