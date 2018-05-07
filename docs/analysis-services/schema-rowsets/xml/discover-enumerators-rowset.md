---
title: DISCOVER_ENUMERATORS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4324869aec4da69731f6256148a4767b23ee6804
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="discoverenumerators-rowset"></a>DISCOVER_ENUMERATORS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt eine Liste mit Namen, Datentypen und Enumerationswerten von Enumeratoren zurück, die vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) für eine bestimmte Datenquelle unterstützt werden. Der XMLA-Anbieter veröffentlicht alle Enumerationskonstanten, die er erkennt.  
  
 Beim Aufrufen der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) Methode mit der **DISCOVER_ENUMERATORS** Enumerationswert in der [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) Element, das **Discover** Methode gibt die **DISCOVER_ENUMERATORS** -Schemarowsets.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Für jeden Enumerator gibt es mehrere Elemente, eines für jeden Wert in der Enumeration. Das Rowset, das jeden Enumerator repräsentiert, ist "flat", und der Name des Enumerators kann für Elemente, die zur selben Enumeration gehören, wiederholt werden.  
  
 Das **DISCOVER_ENUMERATORS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Enumerationsname**|**DBTYPE_WSTR**||Der Name des Enumerators, der eine Wertemenge enthält.|  
|**EnumDescription**|**DBTYPE_WSTR**||Eine lokalisierbare Beschreibung des Enumerators. Kann **NULL**sein.|  
|**EnumType**|**DBTYPE_WSTR**||Der Datentyp der Enumerationswerte.|  
|**ElementName**|**DBTYPE_WSTR**||Der Name eines der Wertelemente im Enumeratorsatz.<br /><br /> Beispiel: **TDP**|  
|**ElementDescription**|**DBTYPE_WSTR**||(Optional) Eine lokalisierbare Beschreibung des Elements. Kann **NULL**sein.|  
|**ElementValue**|**DBTYPE_WSTR**||Der Wert des Elements. Kann **NULL**sein.<br /><br /> Beispiel: **01**|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_ENUMERATORS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**Enumerationsname**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
