---
title: DMSCHEMA_MINING_FUNCTIONS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d069e944aeed7d2f49ad30fda3402d8f50cb1cd5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027720"
---
# <a name="dmschemaminingfunctions-rowset"></a>DMSCHEMA_MINING_FUNCTIONS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt die Data Mining-Funktionen, die von dem Data Mining-Algorithmus unterstützt werden, der auf einem Server verfügbar ist, auf dem [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ausgeführt wird.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DMSCHEMA_MINING_FUNCTIONS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**DIENSTNAME**|**DBTYPE_WSTR**||Name des Algorithmus|  
|**FUNKTIONSNAME**|**DBTYPE_WSTR**||Der Name der Funktion.|  
|**FUNCTION_SIGNATURE**|**DBTYPE_WSTR**||Die Signatur der Funktion.|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||**FALSE** , wenn die Funktion skalare Inhalte zurückgibt (wie die Länge des Zeichenarguments), **TRUE** , wenn die Funktion eine Tabelle zurückgibt (wie eine Histogrammtabelle).|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Eine benutzerfreundliche Beschreibung der Funktion.|  
|**HELP_FILE**|**DBTYPE_WSTR**||Der Name der Datei, die die Dokumentation dieser Funktion enthält.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||Die Hilfekontext-ID für diese Funktion.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DMSCHEMA_MINING_FUNCTIONS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**DIENSTNAME**|**DBTYPE_WSTR**|Optional.|  
|**FUNKTIONSNAME**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Schemarowsets](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
