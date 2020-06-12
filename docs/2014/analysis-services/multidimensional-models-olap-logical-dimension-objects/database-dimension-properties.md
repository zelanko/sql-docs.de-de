---
title: Daten Bank Dimensions Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545188"
---
# <a name="database-dimension-properties"></a>Eigenschaften von Datenbankdimensionen
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden die Merkmale einer Dimension durch die Metadaten für die Dimension definiert, basierend auf den Einstellungen verschiedener Dimensions Eigenschaften und den Attributen oder Hierarchien, die in der Dimension enthalten sind. In der folgenden Tabelle werden die Dimensionseigenschaften in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] beschrieben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|`AttributeAllMemberName`|Gibt den Namen des Alle-Elements für Attribute in einer Dimension an.|  
|`Collation`|Bestimmt die von der Dimension verwendete Sortierung.|  
|`CurrentStorageMode`|Enthält den aktuellen Speichermodus für die Dimension.|  
|`DependsOnDimension`|Enthält die ID einer anderen Dimension, von der die Dimension abhängt, falls vorhanden.|  
|`Description`|Enthält die Beschreibung einer Dimension.|  
|`ErrorConfiguration`|Konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln.|  
|`ID`|Enthält den eindeutigen Bezeichner (ID) der Dimension.|  
|`Language`|Gibt die Standardsprache für die Dimension an.|  
|`MdxMissingMemberMode`|Legt die Verarbeitung fehlender Elemente in MDX-Anweisungen (Multidimensional Expressions) fest.|  
|`MiningModelID`|Enthält die ID des Miningmodells, der die Data Mining-Dimension zugeordnet ist. Diese Eigenschaft kann nur angewendet werden, wenn die Dimension eine Miningmodelldimension ist.|  
|`Name`|Gibt den Namen der Dimension an.|  
|`ProactiveCaching`|Definiert die Einstellungen für die Dimension für die proaktive Zwischenspeicherung.|  
|`ProcessingGroup`|Gibt die Verarbeitungsgruppe an. Die Werte sind ByAttribute oder ByTable. Der Standardwert ist `ByAttribute`.|  
|`ProcessingMode`|Gibt an, ob [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] während oder nach der Verarbeitung indizieren und aggregieren soll.|  
|`ProcessingPriority`|Bestimmt die Verarbeitungspriorität der Dimension während Hintergrundvorgängen wie verzögerte Aggregation, Indizierung oder Clustererstellung.|  
|`Source`|Identifiziert die Datenquellensicht, an die die Dimension gebunden ist.|  
|`StorageMode`|Bestimmt den Speichermodus für die Dimension.|  
|`Type`|Gibt den Typ der Dimension an.|  
|`UnknownMember`|Gibt an, ob das unbekannte Element sichtbar ist.|  
|`UnknownMemberName`|Gibt die Beschriftung in der standardmäßigen Sprache der Dimension für das unbekannte Element der Dimension an.|  
|`WriteEnabled`|Gibt an, ob das Rückschreiben von Dimensionen unterstützt wird (unterliegt den Sicherheitsberechtigungen).|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen von Werten für die Eigenschaften ErrorConfiguration und UnknownMember beim Arbeiten mit NULL-Werten und anderen Problemen mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attribute und Attribut Hierarchien](attributes-and-attribute-hierarchies.md)   
 [Benutzer Hierarchien](user-hierarchies.md)   
 [Dimensions Beziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
