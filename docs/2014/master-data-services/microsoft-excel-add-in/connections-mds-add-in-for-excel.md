---
title: Verbindungen (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c5593e7dd54ebdfcc2eb67dd94f6f9f9dd02cbcb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62764653"
---
# <a name="connections-mds-add-in-for-excel"></a>Verbindungen (MDS-Add-I für Excel)
  Um Daten in den [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]herunterzuladen, müssen Sie zuerst eine Verbindung herstellen. Eine Verbindung ist, wie der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Webdienst weiß, mit welcher MDS-Datenbank eine Verbindung hergestellt werden soll.  
  
 Die Verbindungszeichenfolge ist normalerweise die URL der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]-Webanwendung, z.B. http://contoso/mds.  
  
 Jedes Mal, wenn Sie Excel starten, müssen Sie eine Verbindung mit einem MDS-Repository herstellen. Die einzige Ausnahme ist, wenn das aktive Arbeitsblatt bereits von MDS verwaltete Daten enthält. In diesem Fall wird jedes Mal automatisch eine Verbindung hergestellt, wenn Sie Daten im Blatt aktualisieren oder veröffentlichen.  
  
 Sie können mehrere Verbindungen herstellen. Die Verbindung, auf die zuletzt zugegriffen wurde, wird als Standard angesehen.  
  
 Es können gleichzeitig mehrere Benutzer verbunden werden. Konflikte können jedoch entstehen, wenn mehrere Benutzer versuchen, die gleichen Daten zu veröffentlichen. Weitere Informationen finden Sie unter [Veröffentlichungsdaten &#40;MDS-Add-in für Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Herstellen einer automatischen Verbindung und Laden von häufig verwendeten Daten  
 Wenn Sie immer eine Verbindung mit dem gleichen Server herstellen und den gleichen Satz Daten laden möchten, können Sie Shortcutabfragedateien erstellen, die Verbindungs- und Filterinformationen enthalten. Weitere Informationen zu Abfragedateien finden Sie unter [Shortcutabfragedateien &#40;MDS-Add-In für Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="data-quality-services"></a>Data Quality Services  
 Der [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] hat die Data Quality Services-Funktionalität, mit der Sie Daten vor dem Veröffentlichen im MDS-Repository zuordnen können. Wenn Sie eine Verbindung herstellen und eine DQS-Datenbank auf der gleichen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie die MDS-Datenbank installiert wird, können Sie DQS-Schaltflächen im Menüband anzeigen. Wenn die Datenbank DQS_Main nicht in der Instanz vorhanden ist, werden diese Schaltflächen nicht angezeigt und die Datenqualitätsfunktionalität ist nicht verfügbar.  
  
## <a name="troubleshooting-connections"></a>Fehlerbehandlung von Verbindungen  
 Für die Verbindung mit MDS, wenn Sie alle Probleme finden Sie unter auftreten [ https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx ](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) Tipps zur Problembehandlung.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Herstellen einer Verbindung mit einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank|[Herstellen einer Verbindung mit einem MDS-Repository &#40;MDS-Add-In für Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Laden Sie MDS-Daten in Excel.|[Laden von Daten aus MDS in Excel](export-data-to-excel-from-master-data-services.md)|  
|Filtern Sie MDS-Daten, bevor Sie sie in Excel laden.|[Filtern von Daten vor dem Laden &#40;MDS-Add-in für Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Laden von Daten &#40;MDS-Add-in für Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Shortcutabfragedateien &#40;MDS-Add-In für Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Master Data Services-Add-In für Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
