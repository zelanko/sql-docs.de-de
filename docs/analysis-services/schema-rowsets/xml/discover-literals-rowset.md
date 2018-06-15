---
title: DISCOVER_LITERALS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed865f22291b3e2e47c4934e455e0e75795d35cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030351"
---
# <a name="discoverliterals-rowset"></a>DISCOVER_LITERALS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt Informationen zu Literalen, einschließlich Datentypen und Werten, zurück, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) unterstützt werden.  
  
 Beim Aufrufen der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) Methode mit der **DISCOVER_LITERALS** Enumerationswert in der [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) Element, das **Discover** Methode gibt die **DISCOVER_LITERALS** Rowset.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_LITERALS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||Der Name des in der Zeile beschriebenen Literals.<br /><br /> Beispiel: **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||Ein tatsächlicher Literalwert.<br /><br /> Z. B. wenn **LiteralName** ist **DBLITERAL_LIKE_PERCENT** und das Prozentzeichen (**%**) stimmt mit keinem oder mehreren Zeichen in einer LIKE-Klausel, die den Wert von der **LiteralValue** Spalte ist "**%**".|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||Die Zeichen, die im Literal nicht gültig sind.<br /><br /> Wenn Tabellennamen z. B. etwas anderes als ein numerisches Zeichen enthalten können, ist diese Zeichenfolge "**0123456789**".|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||Die Zeichen, die nicht als erstes Zeichen des Literals verwendet werden dürfen. Wenn das Literal mit irgendeinem gültigen Zeichen beginnen kann, ist dies **null**.|  
|**LiteralMaxLength**|**DBTYPE_I4**||Es können maximal 250 Zeichen eingegeben werden. Wenn die Spalte über keine maximale Länge verfügt, ist der Wert -1 (Standardwert).|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_LITERALS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_KEYWORDS-Rowset & #40; XMLA & #41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
