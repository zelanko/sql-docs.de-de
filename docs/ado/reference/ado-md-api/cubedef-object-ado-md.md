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
ms.openlocfilehash: 61795a8cb10fb0b469f89012d52dfb4723aa0a89
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949788"
---
# <a name="cubedef-object-ado-md"></a>CubeDef-Objekt (ADO MD)
Stellt einen Cube aus einem mehrdimensionalen Schema dar, der einen Satz verwandter Dimensionen enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit den Auflistungen und Eigenschaften eines **CubeDef** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Identifizieren Sie eine **CubeDef** mit der [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) -Eigenschaft.  
  
-   Gibt eine Zeichenfolge zurück, die den Cube mit der [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) -Eigenschaft beschreibt.  
  
-   Gibt die Dimensionen zurück, die den Cube mit der [Dimensions](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) Auflistung bilden.  
  
-   Rufen Sie zusätzliche Informationen über die **CubeDef** mit der standardmäßigen ADO [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Sammlung ab.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|CreatedOn|Das Datum und die Uhrzeit der Erstellung des Cubes.|  
|Cubeguid|Die Cube-GUID.|  
|CubeName|Der Name des Cubes.|  
|Cubetype|Der Typ des Cubes.|  
|Dataupdatedby|Die Benutzer-ID der Person, die das letzte Datenupdate durchgeführt hat.|  
|Beschreibung|Eine aussagekräftige Beschreibung des Cubes.|  
|LastSchemaUpdate|Datum und Uhrzeit des letzten Schema Updates.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
|Schemaupdatedby|Die Benutzer-ID der Person, die die letzte Schema Aktualisierung durchgeführt hat.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CubeDef-Beispiel (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Catalog-Objekt (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [CubeDefs-Sammlung (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Dimensions Auflistung (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
