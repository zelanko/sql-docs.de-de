---
title: ASSL-Objekte und-Objekteigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aee5e7b94aaaca2b35e34f8c4d49c2834189f114
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62736614"
---
# <a name="assl-objects-and-object-characteristics"></a>ASSL-Objekte und -Objekteigenschaften
  Objekte in Analysis Services Scripting Language (ASSL) folgen spezifischen Richtlinien in Bezug auf Objektgruppen, Vererbung, Benennung, Erweiterung und Verarbeitung.  
  
## <a name="object-groups"></a>Objektgruppen  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Alle [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Objekte weisen eine XML-Darstellung auf. Die Objekte sind in zwei Gruppen unterteilt:  
  
 **Hauptobjekte**  
 Hauptobjekte können unabhängig erstellt, geändert und gelöscht werden. Zu den Hauptobjekten gehören:  
  
-   Server  
  
-   Datenbanken  
  
-   Dimensionen  
  
-   Cubes  
  
-   Measuregruppen  
  
-   Partitionen  
  
-   Perspektiven  
  
-   Miningmodelle  
  
-   Rollen  
  
-   Einem Server oder einer Datenbank zugeordnete Befehle  
  
-   Datenquellen  
  
 Hauptobjekte haben die folgenden Eigenschaften, um ihren Verlauf und Status nachzuverfolgen.  
  
-   `CreatedTimestamp`  
  
-   `LastSchemaUpdate`  
  
-   
  `LastProcessed` (wenn geeignet)  
  
> [!NOTE]  
>  Die Klassifizierung eines Objekts als Hauptobjekt wirkt sich darauf aus, wie eine Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dieses Objekt behandelt und wie es in der Objektdefinitionssprache gehandhabt wird. Diese Klassifizierung ist jedoch keine Garantie dafür, dass [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Tools für die Verwaltung und Entwicklung das unabhängige Erstellen, Bearbeiten oder Löschen dieser Objekte zulassen.  
  
 **Nebenobjekte**  
 Nebenobjekte sind Objekte, die nur im Rahmen des Erstellens, Änderns oder Löschens des übergeordneten Hauptobjekts erstellt, geändert oder gelöscht werden können. Zu den Nebenobjekten gehören:  
  
-   Hierarchien und Ebenen  
  
-   Attributes  
  
-   Measures  
  
-   Miningmodellspalten  
  
-   Einem Cube zugeordnete Befehle  
  
-   Aggregationen  
  
## <a name="object-expansion"></a>ObjectExpansion  
 Mit der `ObjectExpansion`-Beschränkung kann der Grad der Erweiterung des vom Server zurückgegebenen ASSL XML-Werts festgelegt werden. Für diese Beschränkung sind die in der folgenden Tabelle aufgeführten Optionen verfügbar.  
  
|Enumerationswert|Zulässig für \<Alter>|BESCHREIBUNG|  
|-----------------------|---------------------------|-----------------|  
|*ReferenceOnly*|nein|Gibt nur den Namen, die ID und den Timestamp für das angeforderte Objekt und alle enthaltenen Hauptobjekte rekursiv zurück.|  
|*ObjectProperties*|ja|Erweitert das angeforderte Objekt und die enthaltenen Nebenobjekte, aber gibt keine enthaltenen Hauptobjekte zurück.|  
|*ExpandObject*|nein|Wie *ObjectProperties*, gibt jedoch auch den Namen, die ID und den Timestamp für enthaltene Hauptobjekte zurück.|  
|*ExpandFull*|ja|Erweitert das angeforderte Objekt und alle enthaltenen Objekte vollständig und rekursiv.|  
  
 In diesem ASSL-Verweisabschnitt wird die *ExpandFull* -Darstellung beschrieben. Alle anderen `ObjectExpansion`-Ebenen werden von dieser Ebene abgeleitet.  
  
## <a name="object-processing"></a>Objektverarbeitung  
 ASSL enthält schreibgeschützte Elemente oder Eigenschaften (z. B. `LastProcessed`), die von der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz gelesen werden können, jedoch nicht angegeben werden, wenn Befehlsskripts an die Instanz übermittelt werden. 
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignoriert geänderte Werte für schreibgeschützte Elemente, ohne eine Warnung oder einen Fehler auszugeben.  
  
 
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignoriert auch unpassende oder irrelevante Eigenschaften, ohne Überprüfungsfehler auszulösen. Beispielsweise sollte das X-Element nur vorhanden sein, wenn das Y-Element einen besonderen Wert aufweist. Die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz ignoriert das X-Element, anstatt es in Bezug auf den Wert des Y-Elements zu überprüfen.  
  
  
