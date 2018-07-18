---
title: Hardware- und Softwareanforderungen für Analysis Services-Server im SharePoint-Modus (SQLServer 2014) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fb86ca0a-518c-4c61-ae78-7680c57fae1f
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2bd9afb97eae82bdb3bfe63859e9081dca5586b4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232670"
---
# <a name="hardware-and-software-requirements-for-analysis-services-server-in-sharepoint-mode-sql-server-2014"></a>Hardware- und Softwareanforderungen für Analysis Services-Server im SharePoint-Modus (SQL Server 2014)
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] unterstützt sowohl SharePoint 2010 als auch SharePoint 2013. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 wird außerhalb der SharePoint-Farm ausgeführt, obwohl es auf SharePoint-Servern installiert werden kann. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 wird auf Anwendungsservern in einer SharePoint 2010-Farm ausgeführt und verwendet die SharePoint-Funktionen und -Infrastruktur, um Servervorgänge zu unterstützen. Um [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] für eine der SharePoint-Versionen zu installieren, verwenden Sie den Installations-Assistenten für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Führen Sie nach der Installation die folgenden Schritte aus:  
  
-   Führen Sie die für die genutzte SharePoint-Version geeignete Version des [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Konfigurationstools aus.  
  
-   Für SharePoint 2013 installieren die [installieren oder Deinstallieren des PowerPivot für SharePoint-Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  

  
##  <a name="bkmk_sqleditions"></a> Anforderungen für die SQL Server-Edition  
 Nicht alle Business Intelligence-Funktionen sind in allen Editionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]verfügbar. Weitere Informationen finden Sie unter [von den SQL Server 2014-Editionen unterstützte Funktionen](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) und [Editionen und Komponenten von SQL Server 2014](../editions-and-components-of-sql-server-2016.md).  
  
 Die aktuellen versionsanmerkungen finden Sie unter [Microsoft SQL Server 2014 Release Notes](http://go.microsoft.com/fwlink/?LinkID=296445).  
  

  
##  <a name="bkmk_sqllicense"></a> SQL Server-Lizenzierung  
 Weitere Informationen zur SQL Server-Lizenzierung finden Sie in den folgenden Themen:  
  
-   [SQL Server 2014-Lizenzierung Datenblatt](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Bezugsquellen: SQLServer-Lizenzierung unterstützt Modelle](http://www.microsoft.com/server-cloud/products/sql-server/buy.aspx#fbid=Zae0-E6r5oh) (http://www.microsoft.com/server-cloud/products/sql-server/buy.aspx#fbid=Zae0-E6r5oh).  
  

  
##  <a name="bkmk_ssas__sharepoint_2013"></a> Für SharePoint 2013 installierte Analysis Services  
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
  
-   [Hardware- und softwareanforderungen für SharePoint 2013](http://technet.microsoft.com/library/cc262485\(office.15\).aspx).  
  
 Die standardmäßigen Hardware- und Softwareempfehlungen für SharePoint 2013 beziehen sich auf eine webbasierte Dokumentverwaltungslösung für eine Arbeitsgruppe oder ein Team. Da die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Verarbeitung datenintensiv ist, reicht die Standardempfehlung nur aus, wenn die Arbeitsauslastung insgesamt niedrig ist, also z. B. weniger als 100 Benutzer oder Arbeitsmappen verarbeitet werden müssen. Eine umfangreichere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Bereitstellung erfordert eine höhere Rechenleistung.  
  

  
##  <a name="bkmk_ssas__sharepoint_2010"></a> Auf einem SharePoint 2010-Server installierte Analysis Services  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 wird auf Anwendungsservern in einer SharePoint 2010-Farm ausgeführt und verwendet die SharePoint-Funktionen und -Infrastruktur, um Servervorgänge zu unterstützen. In der folgenden Tabelle sind die Anforderungen für SharePoint 2010-Bereitstellungen zusammengefasst:  
  
|Komponente|Anforderung|  
|---------------|-----------------|  
|SharePoint-Version|SharePoint 2010 Enterprise ist mit Excel Services, Secure Store Service und Forderungen an den Windows-Tokendienst in der gleichen Serverfarm konfiguriert.<br /><br /> SharePoint muss mit der Serverfarmoption im SharePoint-Setup installiert werden (die eigenständige Installation von SharePoint wird nicht unterstützt). [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] erfordert, dass die Serverfarminfrastruktur den Administrator- und Datenzugriff unterstützt. Von der eigenständigen Installation werden diese Dienste nicht bereitgestellt.<br /><br /> Die unter Windows 7 oder Windows Vista ausgeführte Developer Edition wird für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Serverinstallationen nicht unterstützt.|  
|Service Packs|SharePoint Server 2010 Service Pack 1 (SP1) ist erforderlich.<br /><br /> SharePoint 2010 Service Pack 1 ist erforderlich, damit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Funktionen.<br /><br /> Wenn eine frühere Version von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] aktualisiert wird, ist das kumulative Update "SharePoint 2010 August 2010 Cumulative Update" erforderlich. Das kumulative Update "SharePoint 2010 August 2010 Cumulative Update" oder später sollte nach dem Installieren von SharePoint 2010 Service Pack 1 installiert werden. Eine neue Installation von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] das kumulative Update ist nicht erforderlich. Weitere Informationen finden Sie unter [August 2010 Cumulative Update for SharePoint freigegeben wurde](http://blogs.technet.com/b/stefan_gossner/archive/2010/09/02/august-2010-cumulative-update-for-sharepoint-has-been-released.aspx).|  
|SharePoint-Webanwendung|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2010 unterstützt nur SharePoint-Webanwendungen, die für den klassischen Authentifizierungsmodus konfiguriert sind. Wenn Sie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint einer vorhandenen Farm hinzufügen, müssen Sie sicherstellen, dass die Webanwendung, die Sie hierfür verwenden möchten, für den klassischen Authentifizierungsmodus konfiguriert ist. Anweisungen zum Prüfen des Authentifizierungsmodus finden im Abschnitt "Überprüfen Sie die Webanwendung klassischen Authentifizierungsmodus verwendet" im [Bereitstellen der PowerPivot-Lösungen in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md).|  
|Für die serverseitige Aktualisierung von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Daten erforderliche Datenanbieter|Bei der serverseitigen Datenaktualisierung werden die gleichen Datenabrufschritte wiederholt, die beim ursprünglichen Importieren der Daten ausgeführt wurden. Das bedeutet, dass die zum Importieren der Daten auf einer Clientarbeitsstation verwendeten Datenanbieter auch auf dem [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Server vorhanden sein müssen.<br /><br /> Darüber hinaus ist für die Verwendung von Datenfeeds auf einem SharePoint-Server ADO.NET Data Services erforderlich. Vom SharePoint-Installationsprogramm für die erforderlichen Komponenten wird diese Software nicht für Sie installiert. Die folgende Software muss manuell installiert werden:<br /><br /> ADO.NET Data Services 3.5 SP1-Laufzeitassemblys, die zum Exportieren einer SharePoint-Liste als Datenfeed verwendet werden. Laden Sie die für Ihr Betriebssystem passende Version herunter, und installieren Sie sie:<br /><br /> Verwenden Sie für Windows Server 2008 R2, [ADO.NET Data Services-Update für .NET Framework 3.5 SP1 für Windows 7 und Windows Server 2008 R2 (http://go.microsoft.com/fwlink/?LinkId=182557)](http://go.microsoft.com/fwlink/?LinkId=182557). Windows Server 2008 R2 **SP1** enthält bereits den aktualisierten Anbieter.<br /><br /> Verwenden Sie für Windows Server 2008 [ADO.NET Data Services-Update für .NET Framework 3.5 SP1 für Windows 2000, Windows Server 2003, Windows XP, Windows Vista und Windows Server 2008 (http://go.microsoft.com/fwlink/?LinkId=158125)](http://go.microsoft.com/fwlink/?LinkId=158125).|  
  
 [Bestimmen von Hardware- und Softwareanforderungen (SharePoint 2010) ()http://go.microsoft.com/fwlink/?LinkId=169734)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
 
  
## <a name="additional-information"></a>Zusätzliche Informationen  
 Weitere Informationen zu Änderungen in SharePoint finden Sie unter [Änderungen zwischen SharePoint 2010 und SharePoint 2013](http://technet.microsoft.com/library/ff607742\(office.15\).aspx) (http://technet.microsoft.com/library/ff607742(office.15).aspx).  
  

  
  
