---
title: MDSCHEMA_SETS-Rowset | Microsoft-Dokumentation
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
- MDSCHEMA_SETS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fecc8167d697be2195c9ae44e214afcbc1f3a05b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275476"
---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS-Rowset
  Beschreibt alle Sätze, die zurzeit in einer Datenbank definiert werden, einschließlich Sätzen im Bereich einer Sitzung.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `MDSCHEMA_SETS` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Der Name der Datenbank.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Der Name des Cubes.|  
|`SET_NAME`|`DBTYPE_WSTR`||Der Name des Satzes entsprechend den Angaben der `CREATE SET`-Anweisung.|  
|`SCOPE`|`DBTYPE_I4`||Der Gültigkeitsbereich des Satzes:<br /><br /> -   `MDSET_SCOPE_GLOBAL` (`1`)<br />-   `MDSET_SCOPE_SESSION` (`2`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Wird nicht unterstützt.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Der Ausdruck für den Satz.|  
|`DIMENSIONS`|`DBTYPE_WSTR`||Eine durch Trennzeichen getrennte Liste der in dem Satz enthaltenen Hierarchien.|  
|`SET_CAPTION`|`DBTYPE_WSTR`||Eine Bezeichnung oder Beschriftung, die dem Satz zugeordnet ist. Die Bezeichnung oder Beschriftung dient hauptsächlich zu Anzeigezwecken.|  
|`SET_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Eine Zeichenfolge, die den Pfad des Anzeigeordners angibt, der von der Clientanwendung zum Anzeigen der Menge verwendet wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Für Tools und Clients, die vom [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], den umgekehrten Schrägstrich (\\) ebenentrennzeichen ist. Um mehrere Anzeigeordner bereitzustellen, verwenden Sie ein Semikolon (;), um die Ordner zu trennen.|  
|`SET_EVALUATION_CONTEXT`|`DBTYPE_I4`||Der Kontext für den Satz. Der Satz kann statisch oder dynamisch sein.<br /><br /> Diese Spalte kann einen der folgenden Werte besitzen:<br /><br /> -MDSET_RESOLUTION_STATIC = 1<br />-MDSET_RESOLUTION_DYNAMIC = 2|  
  
 Das Rowset wird sortiert nach `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `MDSCHEMA_SETS` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SET_NAME`|`DBTYPE_WSTR`|Optional.|  
|`SCOPE`|`DBTYPE_I4`|Optional.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Optional.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Optional. **Hinweis:** kann nur eine Hierarchie eingefügt werden, und nur die benannten Mengen, deren Hierarchien den Einschränkungen exakt werden zurückgegeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
