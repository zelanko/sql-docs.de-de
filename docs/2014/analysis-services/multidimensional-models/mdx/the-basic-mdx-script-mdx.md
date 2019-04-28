---
title: Grundlegendes MDX-Skript (Multidimensional Expressions) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default MDX scripts
- statements [MDX]
- expressions [MDX], scripts
- scripts [MDX], about scripts
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e557807f2371b933896a7855c92ef0241ef3af37
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725364"
---
# <a name="the-basic-mdx-script-mdx"></a>Grundlegendes MDX-Skript (MDX)
  Ein MDX-Skript (Multidimensional Expressions, mehrdimensionale Ausdrücke) definiert den Berechnungsprozess für einen Cube in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Es gibt zwei Arten von MDX-Skripts:  
  
 **Das MDX-Standardskript**  
 In dem Moment, in dem Sie einen Cube erstellen, erstellt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ein MDX-Standardskript für den Cube. In diesem Skript ist ein Berechnungsdurchlauf für den gesamten Cube definiert.  
  
 **Benutzerdefiniertes MDX-Skript**  
 Nachdem Sie einen Cube erstellt haben, können Sie benutzerdefinierte MDX-Skripts hinzufügen, um die Berechnungsmöglichkeiten für den Cube zu erweitern.  
  
## <a name="the-default-mdx-script"></a>Das MDX-Standardskript  
 Das MDX-Standardskript, das [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] erstellt, wenn Sie einen Cube definieren, enthält eine einzige CALCULATE-Anweisung. Diese einzige CALCULATE-Anweisung befindet sich am Anfang des MDX-Standardskripts und gibt an, dass beim ersten Berechnungsdurchlauf der gesamte Cube berechnet werden soll.  
  
 Das MDX-Standardskript enthält außerdem die Skriptbefehle, die benannte Mengen, Zuweisungen und berechnete Elemente erstellen, die im Cube-Designer erstellt wurden:  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fügt dem MDX-Standardskript Skriptbefehle direkt hinzu.  
  
-   Für jede benannte Menge im Cube gibt es im MDX-Standardskript eine entsprechende CREATE SET-Anweisung.  
  
-   Für jedes berechnete Element, das im Cube definiert ist, gibt es im MDX-Standardskript eine entsprechende CREATE MEMBER-Anweisung.  
  
 Die Reihenfolge, die die Skriptbefehle, benannten Mengen und berechneten Elemente im MDX-Standardskript haben, können Sie im Cube-Designer über die Registerkarte **Berechnungen** festlegen. Weitere Informationen zum Definieren von Berechnungen, die im MDX-Standardskript gespeichert werden, finden Sie unter [Berechnungen in mehrdimensionalen Modellen](../calculations-in-multidimensional-models.md).  
  
 Ist einem Cube kein MDX-Skript zugeordnet, nimmt der Cube das MDX-Standardskript an. Einem Cube muss mindestens ein MDX-Skript zugeordnet sein, weil ein Cube anhand des MDX-Skripts das Berechnungsverhalten ermittelt. Dies bedeutet, dass ein Cube, dem kein oder ein leeres MDX-Skript zugeordnet wurde, keine Zellen berechnen kann. Wenn Sie Cubes programmgesteuert erstellen, entweder mit ASSL-Befehlen (Analysis Services Scripting Language) oder mit Analysis Management Objects (AMO), empfiehlt es sich, dass Sie ein MDX-Standardskript erstellen, das eine einzige CALCULATE-Anweisung für den Cube enthält.  
  
## <a name="mdx-script-content"></a>Inhalt eines MDX-Skripts  
 Ein MDX-Skript kann die folgenden Anweisungen und Ausdrücke enthalten:  
  
 Alle MDX-Skriptanweisungen  
 In einem MDX-Skript steuern MDX-Skriptbefehle den Kontext und den Gültigkeitsbereich von Berechnungen und verwalten das Verhalten anderer Anweisungen im MDX-Skript. Zu dieser Kategorie gehören die folgenden Anweisungen:  
  
-   [CALCULATE](/sql/mdx/mdx-scripting-calculate)  
  
-   [FREEZE](/sql/mdx/mdx-scripting-freeze)  
  
-   [SCOPE](/sql/mdx/mdx-scripting-scope)  
  
 Weitere Informationen zu MDX-Skriptanweisungen finden Sie unter [MDX-Skriptanweisungen &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx).  
  
 [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member)  
 Die CREATE MEMBER-Anweisung erstellt berechnete Elemente. Weitere Informationen zum Erstellen berechneter Elemente finden Sie unter [Erstellen von berechneten Elementen in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
 [CREATE SET](/sql/mdx/mdx-data-definition-create-set)  
 Die CREATE SET-Anweisung erstellt benannte Mengen. Weitere Informationen zum Erstellen von benannten Mengen finden Sie unter [Erstellen von benannten Mengen in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).  
  
 Bedingte Anweisungen  
 Bedingte Anweisungen erweitern MDX-Skripts um logische Befehle mit Bedingungen. Zu dieser Kategorie gehören die Anweisungen [CASE](/sql/mdx/case-statement-mdx) und [IF](/sql/mdx/mdx-scripting-if) .  
  
 Zuweisungsausdrücke  
 Ein Zuweisungsausdruck weist einem eingeschränkten Teilcube einen Ausdruck (z. B. einen Wert) zu. Ein eingeschränkter Teilcubeausdruck ist eine Auflistung eingeschränkter Mengenausdrücke, die in einem MDX-Skript die "Kanten" eines Teilcubes definieren. Der folgende Code zeigt die Syntax für einen eingeschränkten Teilcubeausdruck:  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Sprachreferenz &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Grundlegendes zu MDX-Skripts &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  
