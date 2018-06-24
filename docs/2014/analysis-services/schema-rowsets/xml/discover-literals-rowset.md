---
title: DISCOVER_LITERALS-Rowset | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_LITERALS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4643ab803f3e6a7d63c4172423e909b6badd64b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057890"
---
# <a name="discoverliterals-rowset"></a>DISCOVER_LITERALS-Rowset
  Gibt Informationen zu Literalen, einschließlich Datentypen und Werten, zurück, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) unterstützt werden.  
  
 Beim Aufrufen der [Discover](../../xmla/xml-elements-methods-discover.md) Methode mit der `DISCOVER_LITERALS` Enumerationswert in der [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) Element, den `Discover` Methode gibt die `DISCOVER_LITERALS` Rowset.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_LITERALS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`LiteralName`|`DBTYPE_WSTR`||Der Name des in der Zeile beschriebenen Literals.<br /><br /> Beispiel: `DBLITERAL_LIKE_PERCENT`|  
|`LiteralValue`|`DBTYPE_WSTR`||Ein tatsächlicher Literalwert.<br /><br /> Wenn beispielsweise `LiteralName` `DBLITERAL_LIKE_PERCENT` lautet und das Prozentzeichen (`%`) keinem oder mehreren Zeichen in einer LIKE-Klausel entspricht, enthält die `LiteralValue`-Spalte den Wert `%`.|  
|`LiteralInvalidChars`|`DBTYPE_WSTR`||Die Zeichen, die im Literal nicht gültig sind.<br /><br /> Beispielsweise wenn Tabellennamen etwas anderes als ein numerisches Zeichen enthalten können, ist diese Zeichenfolge "`0123456789`".|  
|`LiteralInvalidStartingChars`|`DBTYPE_WSTR`||Die Zeichen, die nicht als erstes Zeichen des Literals verwendet werden dürfen. Wenn das Literal mit irgendeinem gültigen Zeichen beginnen kann, ist dies die `null`.|  
|`LiteralMaxLength`|`DBTYPE_I4`||Es können maximal 250 Zeichen eingegeben werden. Wenn die Spalte über keine maximale Länge verfügt, ist der Wert -1 (Standardwert).|  
|`LiteralNameEnumValue`|`DBTYPE_I4`|||  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_LITERALS` Rowset kann eingeschränkt werden, für die Spalten in der folgenden Tabelle.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`LiteralName`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_KEYWORDS-Rowset &#40;XMLA&#41;](discover-keywords-rowset-xmla.md)  
  
  