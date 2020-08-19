---
description: Member-Objekt (ADO MD)
title: Member-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e0797a4d273c51b950e3973d1864480755a20d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440922"
---
# <a name="member-object-ado-md"></a>Member-Objekt (ADO MD)
Stellt einen Member einer Ebene in einem Cube, die untergeordneten Elemente eines Members einer Ebene oder einen Member einer Position entlang einer Achse eines Cellsets dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Eigenschaften eines Members unterscheiden sich** abhängig vom Kontext, in dem er verwendet wird. Ein **Member** einer [Ebene](../../../ado/reference/ado-md-api/level-object-ado-md.md) in einer [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) verfügt über eine [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) -Eigenschaft **, die die Elemente auf der** nächst niedrigeren Ebene in der Hierarchie vom aktuellen **Member**zurückgibt. Bei einem **Member** einer [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) **ist die Auflistung** der untergeordneten Elemente immer leer. Außerdem gilt die [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) -Eigenschaft **nur für Elemente einer** **Ebene**.  
  
 Ein **Member** der **Position** verfügt über zwei Eigenschaften, die für die Anzeige des [Cellsets](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)nützlich sind: [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) und [parametrisameasprev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md). Ein Fehler tritt auf, wenn der Zugriff auf diese Eigenschaften über einen **Member** einer **Ebene**erfolgt.  
  
 Mit den Auflistungen und Eigenschaften eines **Member** -Objekts einer **Ebene**können Sie die folgenden Aktionen ausführen:  
  
-   Identifizieren Sie den **Member** mit den Eigenschaften " [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) " und " [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) ".  
  
-   Gibt eine Zeichenfolge zurück, die verwendet wird, wenn der **Member** mit der [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md) -Eigenschaft angezeigt wird  
  
-   Gibt eine sinnvolle Zeichenfolge zurück, die ein Measure oder **ein Formelelement** mit der [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) -Eigenschaft beschreibt.  
  
-   Bestimmen Sie die Art des **Members mit** der [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) -Eigenschaft.  
  
-   Abrufen von Informationen über die **Ebene** des **Members mit den** Eigenschaften " [leveltiefe](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) " und " [Levelname](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) ".  
  
-   Abrufen verwandter **Member** in einer [Hierarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) mit den übergeordneten und unter [geordneten](../../../ado/reference/ado-md-api/parent-property-ado-md.md) [Eigenschaften.](../../../ado/reference/ado-md-api/children-property-ado-md.md)  
  
-   Zählt **die untergeordneten** Elemente eines Members mit der [childCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) -Eigenschaft.  
  
-   Verwenden Sie die standardmäßige ADO [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, um zusätzliche Informationen über das **Level** -Objekt zu erhalten.  
  
 Durch die Auflistungen und Eigenschaften **Member** eines Members einer **Position** auf einer [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md)können Sie folgende Aufgaben ausführen:  
  
-   Identifizieren Sie den **Member** mit den Eigenschaften " [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) " und " [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) ".  
  
-   Gibt eine Zeichenfolge zurück, die verwendet wird, wenn der **Member** mit der [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md) -Eigenschaft angezeigt wird  
  
-   Gibt eine sinnvolle Zeichenfolge zurück, die ein Measure oder **ein Formelelement** mit der [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) -Eigenschaft beschreibt.  
  
-   Abrufen von Informationen über die **Ebene** des **Members mit den** Eigenschaften " [leveltiefe](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) " und " [Levelname](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) ".  
  
-   Zählt **die untergeordneten** Elemente eines Members mit der [childCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) -Eigenschaft.  
  
-   Verwenden Sie die [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) -Eigenschaft, um zu bestimmen, ob auf der **Achse** unmittelbar nach diesem **Member**mindestens ein untergeordnetes Element vorhanden ist.  
  
-   Verwenden Sie die Eigenschaft " [parametrisameasprev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md) ", um zu bestimmen, **ob das übergeordnete Element dieses Elements** mit dem übergeordneten Element des **unmittelbar vorangehenden**Members identisch ist.  
  
-   Verwenden Sie die standardmäßige ADO [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung, um zusätzliche Informationen über das **Level** -Objekt zu erhalten.  
  
 Die **Properties** -Auflistung enthält vom Anbieter bereitgestellte Eigenschaften. In der folgenden Tabelle sind die verfügbaren Eigenschaften aufgeführt. Die tatsächliche Eigenschaften Liste kann je nach Implementierung des Anbieters abweichen. Eine ausführlichere Liste der verfügbaren Eigenschaften finden Sie in der Dokumentation für Ihren Anbieter.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|CatalogName|Der Name des Katalogs, zu dem dieser Cube gehört.|  
|Kinderkardinalität|Die Anzahl der untergeordneten Elemente des Elements.|  
|CubeName|Der Name des Cubes.|  
|Beschreibung|Eine aussagekräftige Beschreibung des Members.|  
|Dimensionuniquename|Der eindeutige Name der [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|Hierarchyuniquename|Der eindeutige Name der Hierarchie.|  
|LevelNumber|Der Abstand zwischen der Ebene und dem Stamm der Hierarchie.|  
|LevelUniqueName|Der eindeutige Name der Ebene.|  
|MemberCaption|Eine Bezeichnung oder Beschriftung, die dem Element zugeordnet ist.|  
|Mitglieds-ID|Die GUID des Elements.|  
|MemberName|Der Name des Members.|  
|Mitgliedordinalzahl|Die Ordinalzahl des Elements.|  
|MemberType|Der Typ des Elements.|  
|Mitgliedenname|Der eindeutige Name des Members.|  
|ParentCount|Die Anzahl der übergeordneten Elemente, die dieser Member besitzt.|  
|ParentLevel|Die Ebenennummer des übergeordneten Elements des Elements.|  
|ParentUniqueName|Der eindeutige Name des übergeordneten Elements des Members.|  
|SchemaName|Der Name des Schemas, zu dem dieser Cube gehört.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Beispiel (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Members-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
