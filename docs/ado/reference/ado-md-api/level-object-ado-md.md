---
description: Level-Objekt (ADO MD)
title: Level-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
author: rothja
ms.author: jroth
ms.openlocfilehash: 34dc7bc7eb6d80b3ec50cb1838cda0d0e419053b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986511"
---
# <a name="level-object-ado-md"></a>Level-Objekt (ADO MD)
Enthält einen Satz von Membern, von denen jeder denselben Rang innerhalb einer Hierarchie aufweist.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit den Auflistungen und Eigenschaften eines **Level** -Objekts können Sie folgende Aufgaben ausführen:  
  
-   Identifizieren Sie die **Ebene** mit den Eigenschaften " [Name](./name-property-ado-md.md) " und " [UniqueName](./uniquename-property-ado-md.md) ".  
  
-   Gibt eine Zeichenfolge zurück, die beim Anzeigen der **Ebene** mit der [Caption](./caption-property-ado-md.md) -Eigenschaft verwendet werden soll.  
  
-   Gibt eine sinnvolle Zeichenfolge zurück, die die **Ebene** mit der [Description](./description-property-ado-md.md) -Eigenschaft beschreibt.  
  
-   Gibt die [Member](./member-object-ado-md.md) -Objekte zurück, die die **Ebene** mit der [Members](./members-collection-ado-md.md) -Auflistung bilden.  
  
-   Gibt die Anzahl der Ebenen aus dem Stamm der **Ebene** mit der Eigenschaft " [Tiefe](./depth-property-ado-md.md) " zurück.  
  
-   Verwenden Sie die standardmäßige ADO [Properties](../ado-api/properties-collection-ado.md) -Auflistung, um zusätzliche Informationen über das **Level** -Objekt zu erhalten.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|CubeName|Der Name des Cubes.|  
|Beschreibung|Eine aussagekräftige Beschreibung der Ebene.|  
|Dimensionuniquename|Der eindeutige Name der [Dimension](./dimension-object-ado-md.md).|  
|Hierarchyuniquename|Der eindeutige Name der Hierarchie.|  
|LevelCaption|Eine Bezeichnung oder Beschriftung, die der Ebene zugeordnet ist.|  
|LevelCardinality|Die Anzahl der Elemente in der Ebene.|  
|Levelguid|Die GUID der Ebene.|  
|LevelName|Der Name der Ebene.|  
|LevelNumber|Der Abstand zwischen der Ebene und dem Stamm der Hierarchie.|  
|LevelType|Der Typ der Ebene.|  
|LevelUniqueName|Der eindeutige Name der Ebene.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](./level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CubeDef-Beispiel (VBScript)](./cubedef-example-vbscript.md)   
 [Hierarchy-Objekt (ADO MD)](./hierarchy-object-ado-md.md)   
 [Levels-Auflistung (ADO MD)](./levels-collection-ado-md.md)   
 [Members-Auflistung (ADO MD)](./members-collection-ado-md.md)   
 [Properties-Collection (ADO)](../ado-api/properties-collection-ado.md)