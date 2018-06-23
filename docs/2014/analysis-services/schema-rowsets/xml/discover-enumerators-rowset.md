---
title: DISCOVER_ENUMERATORS-Rowset | Microsoft Docs
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
- DISCOVER_ENUMERATORS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2c4eb36f93faba7f32352de41d5c6fde4e0dac2c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160082"
---
# <a name="discoverenumerators-rowset"></a>DISCOVER_ENUMERATORS-Rowset
  Gibt eine Liste mit Namen, Datentypen und Enumerationswerten von Enumeratoren zurück, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) für eine bestimmte Datenquelle unterstützt werden. Der XMLA-Anbieter veröffentlicht alle Enumerationskonstanten, die er erkennt.  
  
 Beim Aufrufen der [Discover](../../xmla/xml-elements-methods-discover.md) Methode mit der `DISCOVER_ENUMERATORS` Enumerationswert in der [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) Element, die `Discover` Methode gibt die `DISCOVER_ENUMERATORS` -Schemarowsets.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Für jeden Enumerator gibt es mehrere Elemente, eines für jeden Wert in der Enumeration. Das Rowset, das jeden Enumerator repräsentiert, ist "flat", und der Name des Enumerators kann für Elemente, die zur selben Enumeration gehören, wiederholt werden.  
  
 Die `DISCOVER_ENUMERATORS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`EnumName`|`DBTYPE_WSTR`||Der Name des Enumerators, der eine Wertemenge enthält.|  
|`EnumDescription`|`DBTYPE_WSTR`||Eine lokalisierbare Beschreibung des Enumerators. Kann `NULL`.|  
|`EnumType`|`DBTYPE_WSTR`||Der Datentyp der Enumerationswerte.|  
|`ElementName`|`DBTYPE_WSTR`||Der Name eines der Wertelemente im Enumeratorsatz.<br /><br /> Beispiel: `TDP`|  
|`ElementDescription`|`DBTYPE_WSTR`||(Optional) Eine lokalisierbare Beschreibung des Elements. Kann `NULL`.|  
|`ElementValue`|`DBTYPE_WSTR`||Der Wert des Elements. Kann `NULL`.<br /><br /> Beispiel: `01`|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DISCOVER_ENUMERATORS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`EnumName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis – Schemarowsets](xml-for-analysis-schema-rowsets.md)  
  
  