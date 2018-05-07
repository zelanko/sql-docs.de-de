---
title: DMSCHEMA_MINING_MODELS Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cd9f66d6fc8155c8390f45130f1354f9d223bc81
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingmodels-rowset"></a>DMSCHEMA_MINING_MODELS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Listet die Data Mining-Modelle im aktuellen Katalog auf. Die **DMSCHEMA_MINING_MODELS** Rowset enthält Informationen wie Modellnamen, Verarbeitungsdatum und die jedes Miningmodell zugeordneten miningalgorithmen.  
  
 aus. Die **DMSCHEMA_MINING_MODELS** Schemarowset ist vergleichbar mit der [DBSCHEMA_TABLES](../../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md) -Schemarowsets und die gleiche Weise verwendet werden kann.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die **DMSCHEMA_MINING_MODELS** Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Der Katalogname. Wird mit dem Namen der Datenbank aufgefüllt, von der das Modell ein Element ist.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Der nicht gekennzeichnete Schemaname. Diese Spalte wird nicht von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; er enthält immer **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Der Miningmodellname. Diese Spalte enthält den Namen des Miningmodells und ist nie leer.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Der Modelltyp.|  
|**MODEL_GUID**|**DBTYPE_GUID**|Der GUID des Modells.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Eine benutzerfreundliche Beschreibung des Modells.|  
|**MODEL_PROPID**|**DBTYPE_UI4**|Die Eigenschaften-ID des Modells. Diese Spalte wird nicht von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; er enthält immer **NULL**.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**|Das Datum, an dem das Modell erstellt wurde.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**|Das Datum, an dem die Modelldefinition zuletzt geändert wurde.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Die Enumeration, die den von dem Modell verwendeten Typ des Data Mining-Algorithmus angibt. Dieser Typ kann folgende Werte besitzen:<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (1)<br /><br /> **DM_SERVICETYPE_SEGMENTATION**(2)<br /><br /> **DM_SERVICETYPE_ ZUORDNUNG**(4)<br /><br /> **DM_SERVICETYPE_ DENSITY_ESTIMATE**(8)<br /><br /> **DM_SERVICETYPE_SEQUENCE**(16)|  
|**DIENSTNAME**|**DBTYPE_WSTR**|Der anbieterspezifische Name des von dem Modell verwendeten Data Mining-Algorithmus.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**|Die für die Erstellung des Miningmodells verwendete Anweisung.|  
|**PREDICTION_ENTITY**|**DBTYPE_WSTR**|Eine durch Trennzeichen getrennte Liste, die angibt, welche Miningspalten vorhergesagt werden können.|  
|**IS_POPULATED**|**DBTYPE_BOOL**|Ein boolesches Flag, das angibt, ob das Modell aufgefüllt wurde.<br /><br /> **"True"** ist das Modell aufgefüllt ist, andernfalls **"false"**.|  
|**MINING_PARAMETERS**|**DBTYPE_WSTR**|Eine durch Trennzeichen getrennte Liste der Parameter, die beim Erstellen des Modells verwendet wurden.|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|Die ID der Miningstruktur, auf der das Modell basiert.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**|Das Datum, an dem das Modell zuletzt geändert wurde.|  
|**MSOLAP_IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Ein boolesches Flag, das angibt, ob das Modell Drillthrough unterstützt.|  
|**FILTER**|**DBTYPE_WSTR**|Der dem Miningmodell zugeordnete Filterausdruck.<br /><br /> NULL oder eine leere Zeichenfolge gibt an, dass kein Filter angewendet wird.|  
|**TRAINING_SET_SIZE**|**DBTYPE_UIS**|Die Anzahl der Fälle, die enthalten sind, in der Mining-Modelltraining festgelegt, nachdem die Struktur verarbeitet wurde und alle vorhandenen Filter auf das Modell angewendet wurden.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die **DMSCHEMA_MINING_MODELS** Rowset kann eingeschränkt werden, für die Spalten in der folgenden Tabelle.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Optional.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Optional.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Optional.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Optional.|  
|**DIENSTNAME**|**DBTYPE_WSTR**|Optional.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Optional.|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|Optional.|  
  
 Beispiele zum Abfragen dieses Rowsets, finden Sie unter [Abfragen, die Parameter, die zum Erstellen eines Miningmodells verwendet](../../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Schemarowsets](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
