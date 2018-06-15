---
title: DMSCHEMA_MINING_MODEL_XML-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e4aa4451c8fed5ceec07609bbb0a22628bc35777
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028241"
---
# <a name="dmschemaminingmodelxml-rowset"></a>DMSCHEMA_MINING_MODEL_XML-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt die XML-Struktur des Miningmodells wieder. Das Format der XML-Zeichenfolge entspricht dem Standard der Predictive Model Markup Language (PMML 2.1).  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DMSCHEMA_MINING_MODEL_XML** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Der Katalogname. Wird mit dem Namen der Datenbank aufgefüllt, von der das Modell ein Element ist.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Der nicht gekennzeichnete Schemaname. Diese Spalte wird nicht von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; er enthält immer **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Der Name des Modells. Diese Spalte darf keinen **NULL**-Wert enthalten.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||Der Modelltyp. Dies ist eine anbieterspezifische Zeichenfolge. Diese kann **NULL**sein.|  
|**MODEL_GUID**|**DBTYPE_GUID**||Der GUID, der das Modell identifiziert. Anbieter, die keine GUIDs verwenden, um Tabellen zu identifizieren, geben **NULL**zurück.|  
|**MODEL_PMML**|**DBTYPE_WSTR**||Eine XML-Wiedergabe des Modellinhalts im PMML-Format.|  
|**SIZE**|**DBTYPE_UI4**||Die Anzahl der Bytes in der XML-Zeichenfolge.|  
|**SPEICHERORT**|**DBTYPE_WSTR**||Der Speicherort der XML-Datei. Der Wert ist **NULL** , wenn keine physische Datei zum Speichern verwendet wird.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das DMSCHEMA_MINING_MODEL_XML-Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_W**STR|Optional.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Optional.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Schemarowsets](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
