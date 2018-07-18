---
title: DMSCHEMA_MINING_MODEL_CONTENT-Rowset | Microsoft-Dokumentation
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
- DMSCHEMA_MINING_MODEL_CONTENT
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT rowset
ms.assetid: 1e85d9e7-3b74-42ac-b94e-f52f76d8a25d
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 76724967936008e52cb43f7af02bbb7a833475d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165451"
---
# <a name="dmschemaminingmodelcontent-rowset"></a>DMSCHEMA_MINING_MODEL_CONTENT-Rowset
  Ermöglicht es der Clientanwendung, den Inhalt eines Data Mining-Modells zu durchsuchen. Clientanwendungen können spezielle Strukturvorgangseinschränkungen verwenden, die am Ende dieses Themas erläutert werden, um zum Inhalt des Miningmodells zu navigieren.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DMSCHEMA_MINING_MODEL_CONTENT` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Der Katalogname. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] füllt diese Spalte mit dem Namen der Datenbank, von denen das Modell ein Element.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Der nicht gekennzeichnete Schemaname. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `VT_NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Der Name des Modells, dem der von dieser Zeile beschriebene Inhalt zugeordnet ist.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Die Namen der Attribute, die diesem Knoten entsprechen.|  
|`NODE_NAME`|`DBTYPE_WSTR`||Der Name des Knotens. Derzeit enthält diese Spalte den gleichen Wert wie `NODE_UNIQUE_NAME`. Dies ändert sich möglicherweise in zukünftigen Versionen.|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name des Knotens.|  
|`NODE_TYPE`|`DBTYPE_I4`||Der Typ des Knotens. Erzeugt einen der folgenden Werte (diese Liste kann durch Data Mining-Algorithmen von Drittanbietern erweitert werden):<br /><br /> -   `DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT` (`2`)<br />-   `DM_NODE_TYPE_TREE_INTERIOR` (`3`)<br />-   `DM_NODE_TYPE_TREE_DISTRIBUTION` (`4`)<br />-   `DM_NODE_TYPE_CLUSTER` (`5`)<br />-   `DM_NODE_TYPE_UNKNOWN` (`6`)<br />-   `DM_NODE_TYPE_ITEMSET` (`7`)<br />-   `DM_NODE_TYPE_ASSOCIATION_RULE` (`8`)<br />-   `DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE` (`9`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE` (`10`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE` (`11`)<br />-   `DM_NODE_TYPE_SEQUENCE` (`13`)<br />-   `DM_NODE_TYPE_TRANSITION` (`14`)<br />-   `DM_NODE_TYPE_TIME_SERIES` (`15`)<br />-   `DM_NODE_TYPE_TS_TREE` (`16`)<br />-   `DM_NODE_TYPE_NN_SUBNETWORK` (`17`) Neuronale Netzwerke, Subnetzwerke<br />-   `DM_NODE_TYPE_NN_INPUT_LAYER` (`18`) Neuronale Netzwerke, eingabeebenen (übergeordnete Elemente der Eingabeknoten)<br />-   **DM_NODE_TYPE_NN_HIDDEN_LAYER** (`19`) neuronale Netzwerke, verborgene Ebenen (übergeordnete Elemente von verborgenen Knoten)<br />-   `DM_NODE_TYPE_NN_OUTPUT_LAYER` (`20`) Neuronale Netzwerke, Ausgabeebenen (übergeordnete Elemente der Ausgabeknoten)<br />-   `DM_NODE_TYPE_NN_INPUT_NODE` (`21`) Neuronale Netzwerke, Eingabeknoten<br />-   `DM_NODE_TYPE_NN_HIDDEN_NODE` (`22`) Neuronale Netzwerke, verborgene Knoten<br />-   `DM_NODE_TYPE_NN_OUTPUT_NODE` (`23`) Neuronale Netzwerke, Ausgabeknoten<br />-   `DM_NODE_TYPE_NN_MARGINAL_STAT_NODE` (`24`) Neuronale Netzwerke, randstatistik<br />-   **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (`25`)<br />-   `DM_NODE_TYPE_NB_MARGINAL_STAT_NODE` (`26`) Neuronale Netzwerke, randstatistik|  
|`NODE_GUID`|`DBTYPE_GUID`||Der GUID (Globally Unique Identifier) des Knotens. Die Spalte wird von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nicht unterstützt, sie enthält immer `NULL`.|  
|`NODE_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, die dem Knoten zugeordnet ist. Diese Eigenschaft dient hauptsächlich zu Anzeigezwecken.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Eine Schätzung der Anzahl untergeordneter Elemente des Knotens.|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Der eindeutige Name des dem Knoten übergeordneten Elements. Für sämtliche Knoten auf der Stammebene wird `NULL` zurückgegeben.|  
|`NODE_DESCRIPTION`|`DBTYPE_WSTR`||Eine benutzerfreundliche Beschreibung des Knotens.|  
|`NODE_RULE`|`DBTYPE_WSTR`||Eine XML-Beschreibung der Regel, die in den Knoten eingebettet ist.|  
|`MARGINAL_RULE`|`DBTYPE_WSTR`||Eine XML-Beschreibung der Regel, die vom übergeordneten Knoten zum Knoten verschoben wird.|  
|`NODE_PROBABILITY`|`DBTYPE_R8`||Die diesem Knoten zugeordnete Wahrscheinlichkeit.|  
|`MARGINAL_PROBABILITY`|`DBTYPE_R8`||Die Wahrscheinlichkeit für das Erreichen des Knotens vom übergeordneten Knoten aus.|  
|`NODE_DISTRIBUTION`|`DBTYPE_HCHAPTER`||Eine Tabelle, die das Wahrscheinlichkeitshistogramm des Knotens enthält.|  
|`NODE_SUPPORT`|`DBTYPE_R8`||Die Anzahl der Fälle, die diesen Knoten unterstützen.|  
|`MSOLAP_MODEL_COLUMN`|`DBTYPE_WSTR`||Der Name der Spalte aus der Modelldefinition, zu der dieser Knoten gehört.|  
|`MSOLAP_NODE_SCORE`|`DBTYPE_R8`||Das Ergebnis, das für diesen Knoten berechnet wurde.|  
|`MSOLAP_NODE_SHORT_CAPTION`|`DBTYPE_WSTR`||Eine Kurzbeschriftung für den Knoten, die zu Anzeigezwecken für eine bessere Lesbarkeit verwendet werden kann.|  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DMSCHEMA_MINING_MODEL_CONTENT` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Optional.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Optional.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`NODE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`NODE_TYPE`|`DBTYPE_I4`|Optional.|  
|`NODE_GUID`|`DBTYPE_WSTR`|Optional.|  
|`NODE_CAPTION`|`DBTYPE_WSTR`|Optional.|  
|`TREE_OPERATION`|`DBTYPE_UI4`|Optional. Weitere Anmerkungen finden Sie unten.|  
  
 Die Einschränkung `TREE_OPERATION` bezieht sich nicht auf eine bestimmte Spalte des `DMSCHEMA_MINING_MODEL_CONTENT`-Rowsets, sondern gibt einen Strukturoperator an. Der Consumer kann eine `NODE_UNIQUE_NAME`-Einschränkung und den Strukturoperator (`ANCESTORS`, `CHILDREN`, `SIBLINGS`, `PARENT`, `DESCENDANTS` und `SELF`) festlegen, um die angeforderte Menge von Elementen abzurufen. Der `SELF`-Operator fügt die Zeile für den Knoten selbst in die Liste der zurückgegebenen Zeilen ein. Die folgende Tabelle beschreibt die Konstanten, aus denen die Bitmapdefinition für die `TREE_OPERATION`-Einschränkung besteht. Sie können mithilfe des `OR`-Operators kombiniert werden.  
  
|Konstante|value|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|`0x00000020`|  
|**DMTREEOP_CHILDREN**|`0x00000001`|  
|**DMTREEOP_SIBLINGS**|`0x00000002`|  
|**DMTREEOP_PARENT**|`0x00000004`|  
|**DMTREEOP_SELF**|`0x00000008`|  
|**DMTREEOP_DESCENDANTS**|`0x00000010`|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining Schema Rowsets](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
