---
title: DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41554600e77c3055f998d7fa32b6f7330c06de52
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037494"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt die Parameter für die Algorithmen auf dem Server.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DMSCHEMA_MINING_SERVICE_PARAMETERS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|**DIENSTNAME**|**DBTYPE_WSTR**|Name des Algorithmus|  
|**PARAMETERNAME**|**DBTYPE_WSTR**|Der Name des Parameters.|  
|**PARAMETERTYP**|**DBTYPE_WSTR**|Der Typ des Parameters.|  
|**IS_REQUIRED**|**DBTYPE_BOOL**|Ein boolescher Wert, der **TRUE** zurückgibt, wenn der Parameter erforderlich ist.|  
|**PARAMETER_FLAGS**|**DBTYPE_UI4**|Eine Bitmaske, die die Eigenschaften des Parameters beschreibt:<br /><br /> **DM_PARAMETER_TRAINING** (**0x0000001**) gibt an, dass der Parameter für das Training verwendet wird.<br /><br /> **DM_PARAMETER_PREDICTION** (**0x00000002**) gibt an, dass der Parameter für die Vorhersage verwendet wird.<br /><br /> **DM_PARAMETER_CONTENT** (**0x00000003**) gibt an, dass der Parameter für die Inhaltseinschränkung verwendet wird.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Eine benutzerfreundliche Beschreibung des Parameters.|  
|**STANDARDWERT**|**DBTYPE_WSTR**|Der Standardwert des Parameters. Gibt **NULL** zurück, wenn der Standardwert kein einfacher Datentyp ist.|  
|**VALUE_ENUMERATION**|**DBTYPE_WSTR**|Ein Enumerator von möglichen Werten für den Parameter.|  
|**HELP_FILE**|**DBTYPE_WSTR**|Der Name der Datei, die die Dokumentation dieses Parameters enthält.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|Die Hilfekontext-ID für diese Funktion.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DMSCHEMA_MINING_SERVICE_PARAMETERS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**DIENSTNAME**|**DBTYPE_WSTR**|Optional.|  
|**PARAMETERNAME**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Schemarowsets](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
