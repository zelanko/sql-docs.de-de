---
title: DMSCHEMA_MINING_MODELS Rowset | Microsoft Docs
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
- DMSCHEMA_MINING_MODELS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d8296ddb800b7691936236aa0cdb6550c89c34c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148478"
---
# <a name="dmschemaminingmodels-rowset"></a>DMSCHEMA_MINING_MODELS-Rowset
  Listet die Data Mining-Modelle im aktuellen Katalog auf. Das `DMSCHEMA_MINING_MODELS`-Rowset enthält Informationen wie Modellnamen, das Verarbeitungsdatum und die jedem Miningmodell zugeordneten Miningalgorithmen.  
  
 zugreifen. Die `DMSCHEMA_MINING_MODELS` Schemarowset ist vergleichbar mit der [DBSCHEMA_TABLES](../ole-db/dbschema-tables-rowset.md) -Schemarowsets und die gleiche Weise verwendet werden kann.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_MODELS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Der Katalogname. Wird mit dem Namen der Datenbank aufgefüllt, von der das Modell ein Element ist.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname. Die Spalte wird von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Der Miningmodellname. Diese Spalte enthält den Namen des Miningmodells und ist nie leer.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Der Modelltyp.|  
|`MODEL_GUID`|`DBTYPE_GUID`||Der GUID des Modells.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung des Modells.|  
|`MODEL_PROPID`|`DBTYPE_UI4`||Die Eigenschaften-ID des Modells. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem das Modell erstellt wurde.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem die Modelldefinition zuletzt geändert wurde.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Die Enumeration, die den von dem Modell verwendeten Typ des Data Mining-Algorithmus angibt. Dieser Typ kann folgende Werte besitzen:<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (1)<br />-   `DM_SERVICETYPE_SEGMENTATION`(2)<br />-   `DM_SERVICETYPE_ ASSOCIATION`(4)<br />-   `DM_SERVICETYPE_ DENSITY_ESTIMATE`(8)<br />-   `DM_SERVICETYPE_SEQUENCE`(16)|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Der anbieterspezifische Name des von dem Modell verwendeten Data Mining-Algorithmus.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||Die für die Erstellung des Miningmodells verwendete Anweisung.|  
|`PREDICTION_ENTITY`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste, die angibt, welche Miningspalten vorhergesagt werden können.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Ein boolesches Flag, das angibt, ob das Modell aufgefüllt wurde.<br /><br /> `TRUE` Wenn das Modell aufgefüllt wird; andernfalls `FALSE`.|  
|`MINING_PARAMETERS`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste der Parameter, die beim Erstellen des Modells verwendet wurden.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`||Die ID der Miningstruktur, auf der das Modell basiert.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Das Datum, an dem das Modell zuletzt geändert wurde.|  
|`MSOLAP_IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Ein boolesches Flag, das angibt, ob das Modell Drillthrough unterstützt.|  
|`FILTER`|`DBTYPE_WSTR`||Der dem Miningmodell zugeordnete Filterausdruck.<br /><br /> NULL oder eine leere Zeichenfolge gibt an, dass kein Filter angewendet wird.|  
|`TRAINING_SET_SIZE`|`DBTYPE_UIS`||Die Anzahl der Fälle, die enthalten sind, in der Mining-Modelltraining festgelegt, nachdem die Struktur verarbeitet wurde und alle vorhandenen Filter auf das Modell angewendet wurden.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_MODELS` Rowset kann eingeschränkt werden, für die Spalten in der folgenden Tabelle.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Optional.|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Optional.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`|Optional.|  
  
 Beispiele zum Abfragen dieses Rowsets, finden Sie unter [Abfragen, die Parameter, die zum Erstellen eines Miningmodells verwendet](../../data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  