---
title: Cube-Eigenschaften | Microsoft-Dokumentation
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
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 785bc878c238b1fbba5acbd7ba3bc0525b8d6cc6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312480"
---
# <a name="cube-properties"></a>Cubeeigenschaften
  Cubes verfügen über eine Reihe von Eigenschaften, die Sie festlegen können und die sich auf das cubeweite Verhalten auswirken. Diese Eigenschaften sind in der folgenden Tabelle zusammengefasst.  
  
> [!NOTE]  
>  Manche Eigenschaften werden beim Erstellen des Cubes automatisch festgelegt und können nicht geändert werden.  
  
 Weitere Informationen über das Festlegen von Cubeeigenschaften finden Sie unter [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](../cube-designer-analysis-services-multidimensional-data.md).  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`AggregationPrefix`|Gibt das für Aggregationsnamen verwendete gemeinsame Präfix an.|  
|`Collation`|Gibt den Gebietsschemabezeichner (LCID) und das Vergleichsflag, durch einen Unterstrich voneinander getrennt, an, wie z. B. Latin1_General_C1_AS.|  
|`DefaultMeasure`|Enthält einen mehrdimensionalen Ausdruck (Multidimensional Expression, MDX), der das Standardmeasure für den Cube definiert.|  
|`Description`|Stellt eine Beschreibung des Cubes bereit, die in Clientanwendungen verwendet werden kann.|  
|`ErrorConfiguration`|Enthält konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln.|  
|`EstimatedRows`|Gibt die Anzahl der geschätzten Zeilen im Cube an.|  
|`ID`|Enthält den eindeutigen Bezeichner (ID) des Cubes.|  
|`Language`|Gibt den Standardsprachbezeichner für den Cube an.|  
|`Name`|Gibt den benutzerfreundlichen Namen des Attributs an.|  
|`ProactiveCaching`|Definiert die Einstellungen für den Cube für die proaktive Zwischenspeicherung.|  
|`ProcessingMode`|Gibt an, ob während oder nach der Verarbeitung indiziert und aggregiert werden soll. Optionen sind **regulären** oder `lazy`.|  
|`ProcessingPriority`|Legt die Verarbeitungspriorität des Cubes bei Hintergrundvorgängen wie z. B. verzögerte Aggregationen und Indizierungen fest. Der Standardwert ist **0**.|  
|`ScriptCacheProcessingMode`|Gibt an, ob der Skriptcache während oder nach der Verarbeitung erstellt werden soll. Optionen sind **regulären** und `lazy`.|  
|`ScriptErrorHandlingMode`|Bestimmt die Fehlerbehandlung. Optionen sind `IgnoreNone` oder `IgnoreAll`|  
|`Source`|Zeigt die für den Cube verwendete Datenquellensicht.|  
|`StorageLocation`|Gibt den Speicherort des Dateisystems für den Cube an. Wenn kein Speicherort angegeben ist, wird er von der Datenbank geerbt, die das Cubeobjekt enthält.|  
|`StorageMode`|Gibt den Speichermodus für den Cube an. Werte sind `MOLAP`, `ROLAP`, oder `HOLAP``.`|  
|`Visible`|Bestimmt die Sichtbarkeit des Cubes.|  
  
> [!NOTE]  
>  Weitere Informationen zum Festlegen von Werten für die ErrorConfiguration-Eigenschaft, bei der Arbeit mit null-Werte und andere Probleme mit der Datenintegrität finden Sie unter [Handling Data Integrity Issues in Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Siehe auch  
 [Proaktives Zwischenspeichern &#40;Partitionen&#41;](partitions-proactive-caching.md)  
  
  
