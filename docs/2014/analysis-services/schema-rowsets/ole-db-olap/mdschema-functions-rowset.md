---
title: MDSCHEMA_FUNCTIONS-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_FUNCTIONS rowset
ms.assetid: 5253fa8c-b1ce-4504-aff6-a246b5e675c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d5966a975cab0f70c24801e83ee9eab7fa99398
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090870"
---
# <a name="mdschemafunctions-rowset"></a>MDSCHEMA_FUNCTIONS-Rowset
  Beschreibt die Funktionen, die Clientanwendungen zur Verfügung stehen, die mit der Datenbank verbunden sind.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **MDSCHEMA_FUNCTIONS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**FUNKTIONSNAME**|**DBTYPE_WSTR**||Der Name der Funktion.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Eine Beschreibung der Funktion.|  
|**PARAMETER_LIST**|**DBTYPE_WSTR**||Eine durch Trennzeichen getrennte Liste von Parametern, die wie in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic formatiert sind. Zum Beispiel könnte ein Parameter "Name als Zeichenfolge" sein.|  
|**RETURN_TYPE**|**DBTYPE_I4**||Der **VARTYPE** des Rückgabedatentyps der Funktion.|  
|**URSPRUNG**|**DBTYPE_I4**||Der Ursprung der Funktion.<br /><br /> -1 für MDX-Funktionen.<br />-2 für benutzerdefinierte Funktionen.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**||Der Name der Schnittstelle für benutzerdefinierte Funktionen.<br /><br /> Der Gruppenname für MDX-Funktionen (Multidimensional Expressions).|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**||Der Name der Typschnittstelle für benutzerdefinierte Funktionen. **NULL** für MDX-Funktionen.|  
|**DLL-NAME**|**DBTYPE_WSTR**||(Optional) Der Name der Assembly, die die benutzerdefinierte Funktion implementiert.<br /><br /> Gibt **VT_NULL** für MDX-Funktionen zurück.|  
|**HELP_FILE**|**DBTYPE_WSTR**||(Optional) Der Name der Datei, die die Hilfedokumentation für die benutzerdefinierte Funktion enthält.<br /><br /> Gibt **VT_NULL** für MDX-Funktionen zurück.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||(Optional) Gibt die Hilfekontext-ID für diese Funktion zurück.|  
|**OBJEKT**|**DBTYPE_WSTR**||(Optional) Der allgemeine Name der Objektklasse, für die eine Eigenschaft gilt. Z. B. das Rowset, der < Ebenenname >. Member-Funktion gibt "**Ebene**".<br /><br /> Gibt **VT_NULL** für benutzerdefinierte Funktionen oder MDX-Funktionen ohne Eigenschaft zurück.|  
|**BESCHRIFTUNG**|**DBTYPE_WSTR**||Die Anzeigebeschriftung für die Funktion.|  
  
 Das Rowset wird nach **ORIGIN**, **INTERFACE_NAME**und **FUNCTION_NAME**sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **MDSCHEMA_FUNCTIONS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Optional.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**FUNKTIONSNAME**|**DBTYPE_WSTR**|Optional.|  
|**URSPRUNG**|**DBTYPE_I4**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB für OLAP-Schemarowsets](ole-db-for-olap-schema-rowsets.md)  
  
  
