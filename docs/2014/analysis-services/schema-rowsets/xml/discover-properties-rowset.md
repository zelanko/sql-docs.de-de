---
title: DISCOVER_PROPERTIES-Rowset | Microsoft Docs
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
- DISCOVER_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: af566467345e29362a7b2fdd2c5bda04a35a6dd5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147998"
---
# <a name="discoverproperties-rowset"></a>DISCOVER_PROPERTIES-Rowset
  Gibt eine Liste mit Informationen und Werten zu den standardmäßigen und anwenderspezifischen Eigenschaften zurück, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA-Anbieter (XML for Analysis) für die angegebene Datenquelle unterstützt werden. Nicht unterstützte Eigenschaften werden nicht im zurückgegebenen Resultset aufgelistet.  
  
 Beim Aufrufen der [Discover](../../xmla/xml-elements-methods-discover.md) Methode mit der `DISCOVER_PROPERTIES` Enumerationswert in der [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) Element, die `Discover` Methode gibt die `DISCOVER_PROPERTIES` Rowset...  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DISCOVER_PROPERTIES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typ|Länge|Description|  
|-----------------|----------|------------|-----------------|  
|`PropertyName`|`DBTYPE_WSTR`||Der Name der Eigenschaft.|  
|`PropertyDescription`|`DBTYPE_WSTR`||Eine lokalisierbare Textbeschreibung der Eigenschaft. Gelegten `NULL`.|  
|`PropertyType`|`DBTYPE_WSTR`||Der XML-Datentyp der Eigenschaft.<br /><br /> Gelegten `NULL`.|  
|`PropertyAccessType`|`DBTYPE_WSTR`||Der Zugriff für die Eigenschaft. Der Wert kann `Read`, `Write`, oder `ReadWrite`.|  
|`IsRequired`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob eine Eigenschaft erforderlich ist.<br /><br /> True, wenn eine Eigenschaft erforderlich ist; False, wenn keine erforderlich ist.<br /><br /> Gelegten `NULL`.|  
|`Value`|`DBTYPE_WSTR`||Der aktuelle Wert der Eigenschaft.<br /><br /> Gelegten `NULL`.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das `DISCOVER_PROPERTIES`-Rowset kann auf die in der folgenden Tabelle aufgeführte Spalte eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`PropertyName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  