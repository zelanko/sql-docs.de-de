---
title: DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset | Microsoft Docs
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
- DMSCHEMA_MINING_SERVICE_PARAMETERS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9079be52d50da3a400496dc602166c857f2b1691
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149987"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>DMSCHEMA_MINING_SERVICE_PARAMETERS-Rowset
  Beschreibt die Parameter für die Algorithmen auf dem Server.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_SERVICE_PARAMETERS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Name des Algorithmus|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`||Der Name des Parameters.|  
|`PARAMETER_TYPE`|`DBTYPE_WSTR`||Der Typ des Parameters.|  
|`IS_REQUIRED`|`DBTYPE_BOOL`||Ein boolescher Wert, der `TRUE` zurückgibt, wenn der Parameter erforderlich ist.|  
|`PARAMETER_FLAGS`|`DBTYPE_UI4`||Eine Bitmaske, die die Eigenschaften des Parameters beschreibt:<br /><br /> -   `DM_PARAMETER_TRAINING` (`0x0000001`) gibt an, der Parameter für das Training verwendet wird<br />-   `DM_PARAMETER_PREDICTION` (`0x00000002`) gibt an, der Parameter für die Vorhersage verwendet wird<br />-   `DM_PARAMETER_CONTENT` (`0x00000003`) gibt an, der Parameter für die inhaltseinschränkung verwendet wird|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung des Parameters.|  
|`DEFAULT_VALUE`|`DBTYPE_WSTR`||Der Standardwert des Parameters. Gibt `NULL` zurück, wenn der Standardwert kein einfacher Datentyp ist.|  
|`VALUE_ENUMERATION`|`DBTYPE_WSTR`||Ein Enumerator von möglichen Werten für den Parameter.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Der Name der Datei, die die Dokumentation dieses Parameters enthält.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||Die Hilfekontext-ID für diese Funktion.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_SERVICE_PARAMETERS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  