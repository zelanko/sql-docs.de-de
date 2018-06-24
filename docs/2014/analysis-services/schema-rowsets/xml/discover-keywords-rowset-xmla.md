---
title: DISCOVER_KEYWORDS-Rowset (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_KEYWORDS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df7fd7c6bf7dbe9ebd0bb9057b5c82dc351afab3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056341"
---
# <a name="discoverkeywords-rowset-xmla"></a>DISCOVER_KEYWORDS-Rowset (XMLA)
  Gibt Informationen über vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) reservierte Schlüsselwörter zurück.  
  
 Beim Aufrufen der [Discover](../../xmla/xml-elements-methods-discover.md) Methode mit der `DISCOVER_KEYWORDS` Enumerationswert in der [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) Element, den `Discover` Methode gibt die `DISCOVER_KEYWORDS` Rowset.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_KEYWORDS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||Eine Liste aller von einem Anbieter reservierten Schlüsselwörter.<br /><br /> Beispiel: `AND`|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_KEYWORDS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_LITERALS-Rowset](discover-literals-rowset.md)  
  
  