---
title: MDSCHEMA_SETS-Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 666f8aa8889f2d15e9e62499e41ad9c0bc69fcff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028051"
---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS-Rowset
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt alle Sätze, die zurzeit in einer Datenbank definiert werden, einschließlich Sätzen im Bereich einer Sitzung.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die **MDSCHEMA_SETS** Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Der Name der Datenbank.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Nicht unterstützt.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Der Name des Cubes.|  
|**GRUPPENNAME**|**DBTYPE_WSTR**|Der Name der Menge, gemäß der **CREATE SET** Anweisung.|  
|**BEREICH**|**DBTYPE_I4**|Der Gültigkeitsbereich des Satzes:<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Nicht unterstützt.|  
|**AUSDRUCK**|**DBTYPE_WSTR**|Der Ausdruck für den Satz.|  
|**DIMENSIONEN**|**DBTYPE_WSTR**|Eine durch Trennzeichen getrennte Liste der in dem Satz enthaltenen Hierarchien.|  
|**SET_CAPTION**|**DBTYPE_WSTR**|Eine Bezeichnung oder Beschriftung, die dem Satz zugeordnet ist. Die Bezeichnung oder Beschriftung dient hauptsächlich zu Anzeigezwecken.|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Eine Zeichenfolge, die den Pfad des Anzeigeordners angibt, der von der Clientanwendung zum Anzeigen der Menge verwendet wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Zu den Tools und Clients, die vom [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], den umgekehrten Schrägstrich (\\) ebenentrennzeichen ist. Um mehrere Anzeigeordner bereitzustellen, verwenden Sie ein Semikolon (;), um die Ordner zu trennen.|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|Der Kontext für den Satz. Der Satz kann statisch oder dynamisch sein. Diese Spalte kann einen der folgenden Werte besitzen:<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 Das Rowset wird sortiert nach **CATALOG_NAME**, **SCHEMA_NAME**und **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die **MDSCHEMA_SETS** Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**GRUPPENNAME**|**DBTYPE_WSTR**|Optional.|  
|**BEREICH**|**DBTYPE_I4**|Optional.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Optional.<br /><br /> Hinweis: Nur eine Hierarchie enthalten sein, und nur die benannten Mengen, deren Hierarchien den Einschränkungen exakt zurückgegeben werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
