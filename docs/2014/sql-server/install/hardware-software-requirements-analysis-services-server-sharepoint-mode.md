---
title: Hardware-und Software Anforderungen für Analysis Services-Server im SharePoint-Modus (SQL Server 2014) | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: database-engine
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 425639d6e22491028f552bc97990267b2b33e799
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73637815"
---
# <a name="hardware-and-software-requirements-for-analysis-services-server-in-sharepoint-mode-sql-server-2014"></a>Hardware- und Softwareanforderungen für Analysis Services-Server im SharePoint-Modus (SQL Server 2014)

[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] unterstützt sowohl SharePoint 2010 als auch SharePoint 2013. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 wird außerhalb der SharePoint-Farm ausgeführt, obwohl es auf SharePoint-Servern installiert werden kann. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 wird auf Anwendungsservern in einer SharePoint 2010-Farm ausgeführt und verwendet die SharePoint-Funktionen und -Infrastruktur, um Servervorgänge zu unterstützen. Um [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] für eine der SharePoint-Versionen zu installieren, verwenden Sie den Installations-Assistenten für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Führen Sie nach der Installation die folgenden Schritte aus:  
  
- Führen Sie die für die genutzte SharePoint-Version geeignete Version des [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Konfigurationstools aus.  
  
- Installieren Sie für SharePoint 2013 die [Installation oder Deinstallation des PowerPivot für SharePoint Add &#40;-in Share&#41;Point 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).  

##  <a name="bkmk_sqleditions"></a> Anforderungen für die SQL Server-Edition  
 Nicht alle Business Intelligence-Funktionen sind in allen Editionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]verfügbar. Weitere Informationen finden Sie [unter von den Editionen von SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) und [Editionen und Komponenten von SQL Server 2014](../editions-and-components-of-sql-server-2016.md)unterstützte Funktionen.  
  
 Die aktuellen Anmerkungen zu dieser Version finden Sie in den Anmerkungen zur Version [Microsoft SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  

  
##  <a name="bkmk_sqllicense"></a>SQL Server Lizenzierung  
 Weitere Informationen zur SQL Server-Lizenzierung finden Sie in den folgenden Themen:  
  
-   [SQL Server 2014-Lizenzierungs Daten](https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) Blatt (https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Kauf: SQL Server-Unterstützung von Lizenzierungs Modellen](https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2) (https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2).  
  
##  <a name="bkmk_ssas__sharepoint_2013"></a>Analysis Services auf SharePoint 2013 installiert  
 Wenn Sie den Analysis Services-Server im SharePoint-Modus eigenständig auf einem Server installieren, basieren die Mindestsystemanforderungen auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und nicht auf den Anforderungen des SharePoint-Servers.  
  
 [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
 Optimale Unterstützung für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint bieten Unternehmensserver der neuen Generation mit höheren RAM- und Verarbeitungskapazitäten. Zum Speichern von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Daten im Arbeitsspeicher wird eine hohe RAM-Kapazität belegt. Der RAM-Speicher ermöglicht die Anpassung an strukturelle Änderungen. Zusätzliche Prozessoren unterstützen zeitintensive Scans unaggregierter Rohdaten. Die Datenstruktur ändert sich dynamisch in Reaktion auf anwendergesteuerte Datenanalysen, die durch eine Excel-Client- oder -Front-End-Schnittstelle initiiert werden.  
  
> [!TIP]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint verwendet L2- und L3-Caches. Zur Leistungsverbesserung ziehen Sie die Verwendung von Prozessoren mit größeren L2- und L3-Caches in Betracht.  
  
 In der folgenden Tabelle sind die minimale und empfohlene Hardwarekonfiguration für einen eigenständigen [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)]-Server beschrieben, der nicht Teil der SharePoint-Farm ist:  
  
|Komponente|Minimum|Empfohlen|  
|---------------|-------------|-----------------|  
|Prozessor|64-Bit-Dual-Core-Prozessor, 3 GHz|16 Kerne|  
|RAM|8 GB RAM|64 GB RAM|  
|Speicherung|80 GB Speicherplatz|80 GB oder mehr|  
  
 Wenn Sie einen Analysis Services-Server im SharePoint-Modus auf einem SharePoint-Farmserver installieren, finden Sie unter folgenden Links die Mindestsystemanforderungen sowohl für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] als auch für den SharePoint-Server:  
  
-   [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Hardware-und Softwareanforderungen für SharePoint 2013](https://technet.microsoft.com/library/cc262485\(office.15\).aspx).  
  
 Die standardmäßigen Hardware- und Softwareempfehlungen für SharePoint 2013 beziehen sich auf eine webbasierte Dokumentverwaltungslösung für eine Arbeitsgruppe oder ein Team. Da die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Verarbeitung datenintensiv ist, reicht die Standardempfehlung nur aus, wenn die Arbeitsauslastung insgesamt niedrig ist, also z. B. weniger als 100 Benutzer oder Arbeitsmappen verarbeitet werden müssen. Eine umfangreichere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Bereitstellung erfordert eine höhere Rechenleistung.  
  
##  <a name="bkmk_ssas__sharepoint_2010"></a>Analysis Services auf einem SharePoint 2010-Server installiert  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 wird auf Anwendungsservern in einer SharePoint 2010-Farm ausgeführt und verwendet die SharePoint-Funktionen und -Infrastruktur, um Servervorgänge zu unterstützen. In der folgenden Tabelle sind die Anforderungen für SharePoint 2010-Bereitstellungen zusammengefasst:  
  
|Komponente|Anforderung|  
|---------------|-----------------|  
|SharePoint-Version|SharePoint 2010 Enterprise ist mit Excel Services, Secure Store Service und Forderungen an den Windows-Tokendienst in der gleichen Serverfarm konfiguriert.<br /><br /> SharePoint muss mit der Serverfarmoption im SharePoint-Setup installiert werden (die eigenständige Installation von SharePoint wird nicht unterstützt). [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] erfordert, dass die Serverfarminfrastruktur den Administrator- und Datenzugriff unterstützt. Von der eigenständigen Installation werden diese Dienste nicht bereitgestellt.<br /><br /> Die unter Windows 7 oder Windows Vista ausgeführte Developer Edition wird für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Serverinstallationen nicht unterstützt.|  
|Service Packs|SharePoint Server 2010 Service Pack 1 (SP1) ist erforderlich.<br /><br /> SharePoint 2010 Service Pack 1 ist für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Featureserforderlich.<br /><br /> Wenn eine frühere Version von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] aktualisiert wird, ist das kumulative Update "SharePoint 2010 August 2010 Cumulative Update" erforderlich. Das kumulative Update "SharePoint 2010 August 2010 Cumulative Update" oder später sollte nach dem Installieren von SharePoint 2010 Service Pack 1 installiert werden. Für eine Neuinstallation von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ist das kumulative Update nicht erforderlich. Weitere Informationen finden Sie unter das [kumulative Update von August 2010 für SharePoint wurde veröffentlicht](http://blogs.technet.com/b/stefan_gossner/archive/2010/09/02/august-2010-cumulative-update-for-sharepoint-has-been-released.aspx).|  
|SharePoint-Webanwendung|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2010 unterstützt nur SharePoint-Webanwendungen, die für den klassischen Authentifizierungsmodus konfiguriert sind. Wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint einer vorhandenen Farm hinzufügen, müssen Sie sicherstellen, dass die Webanwendung, die Sie hierfür verwenden möchten, für den klassischen Authentifizierungsmodus konfiguriert ist. Anweisungen zum Überprüfen des Authentifizierungsmodus finden Sie im Abschnitt "überprüfen, ob die Webanwendung die Authentifizierung im klassischen Modus verwendet" unter Bereitstellen von [Power Pivot-Lösungen in SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint).|  
|Für die serverseitige Aktualisierung von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Daten erforderliche Datenanbieter|Bei der serverseitigen Datenaktualisierung werden die gleichen Datenabrufschritte wiederholt, die beim ursprünglichen Importieren der Daten ausgeführt wurden. Das bedeutet, dass die zum Importieren der Daten auf einer Clientarbeitsstation verwendeten Datenanbieter auch auf dem [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Server vorhanden sein müssen.<br /><br /> Darüber hinaus ist für die Verwendung von Datenfeeds auf einem SharePoint-Server ADO.NET Data Services erforderlich. Vom SharePoint-Installationsprogramm für die erforderlichen Komponenten wird diese Software nicht für Sie installiert. Die folgende Software muss manuell installiert werden:<br /><br /> ADO.NET Data Services 3.5 SP1-Laufzeitassemblys, die zum Exportieren einer SharePoint-Liste als Datenfeed verwendet werden. Laden Sie die für Ihr Betriebssystem passende Version herunter, und installieren Sie sie:<br /><br /> Verwenden Sie für Windows Server 2008 R2 [ADO.NET Data Services Update für .NET Framework 3,5 SP1 für Windows 7 und Windows Server 2008 R2](https://www.microsoft.com/download/details.aspx?id=2343). Windows Server 2008 R2 **SP1** enthält bereits den aktualisierten Anbieter.<br /><br /> Verwenden Sie für Windows Server 2008 [ADO.NET Data Services Update für .NET Framework 3,5 SP1 für Windows 2000, Windows Server 2003, Windows XP, Windows Vista und Windows Server 2008 (https://go.microsoft.com/fwlink/?LinkId=158125)](https://www.microsoft.com/download/details.aspx?id=22734).|  
  
 [Bestimmen von Hardware-und Software Anforderungen (SharePoint 2010) (https://go.microsoft.com/fwlink/?LinkId=169734)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
## <a name="additional-information"></a>Zusätzliche Informationen  

Weitere Informationen zu SharePoint-Änderungen finden [Sie unter Änderungen von SharePoint 2010 zu SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).