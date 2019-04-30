---
title: CubeDef-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1027fc76cb09f7b846e1b8edad52a3cb5dbf2bc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225908"
---
# <a name="cubedef-object-ado-md"></a>CubeDef-Objekt (ADO MD)
Stellt einen Cube aus einem mehrdimensionalen Schema, das mit einem Satz von verknüpften Dimensionen dar.  
  
## <a name="remarks"></a>Hinweise  
 Mit dem Auflistungen und Eigenschaften einer **CubeDef** -Objekts können Sie folgende Möglichkeiten:  
  
-   Identifizieren einer **CubeDef** mit der [Namen](../../../ado/reference/ado-md-api/name-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben einer Zeichenfolge, die den Cube beschreibt die [Beschreibung](../../../ado/reference/ado-md-api/description-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben der Dimensionen, die den Cube mit bilden die [Dimensionen](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) Auflistung.  
  
-   Weitere Informationen zum Abrufen der **CubeDef** mit dem standard-ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
 Die **Eigenschaften** Auflistung enthält die Eigenschaften vom Anbieter bereitgestellt. Die folgende Tabelle enthält Eigenschaften, die möglicherweise verfügbar sind. Die tatsächliche Eigenschaftenliste kann je nach der Implementierung des Anbieters abweichen. Finden Sie unter der Dokumentation für Ihren Anbieter, um eine vollständige Liste der verfügbaren Eigenschaften.  
  
|Name|Description|  
|----------|-----------------|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|CreatedOn|Datum und Uhrzeit der Erstellung des Cubes.|  
|CubeGUID|GUID des Cubes.|  
|CubeName|Der Name des Cubes.|  
|CubeType|Der Typ des Cubes.|  
|DataUpdatedBy|Benutzer-ID der Person, die der letzten datenaktualisierung durchführen.|  
|Description|Eine aussagekräftige Beschreibung des Cubes.|  
|LastSchemaUpdate|Datum und Uhrzeit der letzten Aktualisierung des Schemas.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
|SchemaUpdatedBy|Benutzer-ID der Person, die Aktualisierung des letzten Schemas ausführen.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [CubeDef-Beispiel (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Katalogobjekt (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [CubeDefs-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Auflistung von Dimensionen (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
