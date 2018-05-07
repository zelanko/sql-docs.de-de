---
title: DISCOVER_KEYWORDS-Rowset (XMLA) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc9da6245c9ae856d0366fd7ee7909d7b6299977
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="discoverkeywords-rowset-xmla"></a>DISCOVER_KEYWORDS-Rowset (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt Informationen über vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) reservierte Schlüsselwörter zurück.  
  
 Wenn Sie die [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) -Methode mit dem **DISCOVER_KEYWORDS** -Enumerationswert im [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) -Element aufrufen, gibt die **Discover** -Methode das **DISCOVER_KEYWORDS** -Rowset zurück.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_KEYWORDS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Schlüsselwort**|**DBTYPE_WSTR**||Eine Liste aller von einem Anbieter reservierten Schlüsselwörter.<br /><br /> Beispiel: **AND**|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_KEYWORDS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**Schlüsselwort**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_LITERALS-Rowset](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)  
  
  
