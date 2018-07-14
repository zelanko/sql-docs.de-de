---
title: DMSCHEMA_MINING_FUNCTIONS-Rowset | Microsoft-Dokumentation
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
- DMSCHEMA_MINING_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b726c81df5a6085ee52b177d95b4917d7cb8be1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169645"
---
# <a name="dmschemaminingfunctions-rowset"></a>DMSCHEMA_MINING_FUNCTIONS-Rowset
  Beschreibt die Datamining-Funktionen, die von Datamining-Algorithmen auf einem Server verfügbar, die ausgeführt wird, unterstützt werden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_FUNCTIONS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Name des Algorithmus|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`||Der Name der Funktion.|  
|`FUNCTION_SIGNATURE`|`DBTYPE_WSTR`||Die Signatur der Funktion.|  
|`RETURNS_TABLE`|`DBTYPE_BOOL`||`FALSE` Wenn die Funktion skalare Inhalte (z. B. die Länge des Arguments Zeichen); zurückgibt. `TRUE` die Funktion eine Tabelle (z. B. eine Histogrammtabelle) zurück.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung der Funktion.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Der Name der Datei, die die Dokumentation dieser Funktion enthält.|  
|`HELP_CONTEXT`|`DBTYPE_I4`||Die Hilfekontext-ID für diese Funktion.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_FUNCTIONS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
