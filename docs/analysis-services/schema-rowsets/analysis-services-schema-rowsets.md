---
title: Analysis Services-Schemarowsets | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ea3d947e8cfbea4b183f4416ebabf6bb0ebf7b61
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services-Schemarowsets
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Schemarowsets sind vordefinierte Tabellen, die Informationen zu Analysis Services-Objekten und zum Serverstatus enthalten, einschließlich Datenbankschema, aktive Sitzungen, Verbindungen, Befehle und Aufträge, die auf dem Server ausgeführt werden. Sie können Schemarowsettabellen in einem XML/A-Skriptfenster in SQL Server Management Studio abfragen, eine DMV-Abfrage für ein Schemarowset ausführen oder eine benutzerdefinierte Anwendung erstellen, die Schemarowsetinformationen enthält (z. B. eine Berichterstellungsanwendung, durch die die Liste der verfügbaren Dimensionen abgerufen wird, die zum Erstellen eines Berichts verwendet werden können).  
  
> [!NOTE]  
>  Bei Verwendung von Schemarowsets im XML/A-Skripts, die Informationen, die in zurückgegeben wird die *Ergebnis* Parameter von der [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) Methode ist gemäß den in diesem Abschnitt beschriebenen rowsetspaltenlayouts strukturiert. Vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) werden die Rowsets unterstützt, die von der XML for Analysis-Spezifikation benötigt werden. Einige der standardmäßigen Schemarowsets für OLE DB, OLE DB für OLAP und OLE DB für Data Mining-Datenquellenanbieter werden vom XMLA-Anbieter ebenfalls unterstützt. Die unterstützten Rowsets werden in den folgenden Themen beschrieben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[XML for Analysis-Schemarowsets](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten XMLA-Rowsets.|  
|[OLE DB-Schemarowsets](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten OLE DB-Schemarowsets.|  
|[OLE DB für OLAP-Schemarowsets](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten OLE DB für OLAP-Schemarowsets.|  
|[Datamining-Schemarowsets](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Beschreibt die vom XMLA-Anbieter unterstützten Data Mining-Schemarowsets.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenzugriff auf mehrdimensionale Modelle & #40; Analysis Services – mehrdimensionale Daten & #41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Verwenden Sie dynamische Verwaltungssichten & #40; DMVs & #41; zum Überwachen von Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
