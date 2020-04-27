---
title: Überprüfen von Cube-und Dimensions Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dda922b8-6d75-4662-b09e-8a317c6a1c70
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c95d241d136f290110ac8a2b72540011a3922e24
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079001"
---
# <a name="reviewing-cube-and-dimension-properties"></a>Überprüfen von Cube- und Dimensionseigenschaften
  Nachdem Sie einen Cube definiert haben, können Sie die Ergebnisse mit dem Cube-Designer überprüfen. In der folgenden Aufgabe überprüfen Sie die Struktur des Cubs im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekt.  
  
### <a name="to-review-cube-and-dimension-properties-in-cube-designer"></a>So überprüfen Sie Cube- und Dimensionseigenschaften im Cube-Designer  
  
1.  Zum Öffnen des Cube-Designers doppelklicken Sie auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten des Projektmappen-Explorers.  
  
2.  Erweitern Sie im Cube-Designer auf der Registerkarte **Cubestruktur** im Bereich **Measures** die Measuregruppe **Internet Sales** , um die definierten Measures anzuzeigen.  
  
     Durch Ziehen können Sie die Reihenfolge der Measures ändern. Die Reihenfolge hat Auswirkungen auf die Reihenfolge, in der bestimmte Clientanwendungen diese Measures anordnen. Die Measuregruppe und jedes enthaltene Measure weisen Eigenschaften auf, die Sie im Eigenschaftenfenster bearbeiten können.  
  
3.  Überprüfen Sie im Cube-Designer auf der Registerkarte **Cubestruktur** im Bereich **Dimensionen** die Cubedimensionen des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cubes.  
  
     Zwar wurden auf der Datenbankebene nur drei Dimensionen erstellt, wie im Projektmappen-Explorer angezeigt; der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube enthält jedoch fünf Cubedimensionen. Der Cube enthält mehr Dimensionen als die Datenbank, da die Datenbankdimension "Date" als Grundlage für drei separate datumsbezogene Cubedimensionen verwendet wird, basierend auf unterschiedlichen datumsbezogenen Fakten in der Faktentabelle. Diese datumsbezogenen Dimensionen werden auch *Dimensionen mit unterschiedlichen Rollen*genannt. Mit den drei datumsbezogenen Cubedimensionen können Benutzer den Cube anhand von drei separaten Fakten dimensionieren, die sich auf die einzelnen Produktverkäufe beziehen: das Produktbestelldatum, das Fälligkeitsdatum und das Lieferdatum für die Bestellung. Durch das Wiederverwenden einer einzelnen Datenbankdimension für mehrere Cubedimensionen in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wird die Dimensionsverwaltung vereinfacht sowie die Speicherplatzverwendung und die Gesamtverarbeitungszeit reduziert.  
  
4.  Erweitern Sie im **Dimensionen** -Bereich der Registerkarte **Cubestruktur** die **Customer**-Dimension, und klicken Sie dann auf **Customer bearbeiten** , um die Dimension im Dimensions-Designer zu öffnen.  
  
     Der Dimensions-Designer enthält folgende Registerkarten: **Dimensionsstruktur**, **Attributbeziehungen**, **Übersetzungen**und **Browser**. Die Registerkarte **Dimensionsstruktur** enthält drei Bereiche: **Attribute**, **Hierarchien**und **Datenquellensicht**. Die Attribute, die die Dimension enthält, werden im Bereich **Attribute** angezeigt. Weitere Informationen finden Sie unter [Dimensions Attribut Eigenschaften-Referenz](multidimensional-models/dimension-attribute-properties-reference.md), [Erstellen von benutzerdefinierten Hierarchien](multidimensional-models/user-defined-hierarchies-create.md).  
  
5.  Um zum Cube-Designer zu wechseln, klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten, und klicken Sie anschließend auf **Designer anzeigen**.  
  
6.  Klicken Sie im Cube-Designer auf die Registerkarte **Dimensionsverwendung** .  
  
     In dieser Ansicht des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cubes sehen Sie die von der Internet Sales-Measuregruppe verwendeten Cubedimensionen. Außerdem können Sie den Typ der Beziehung zwischen jeder Dimension und den einzelnen Measuregruppen, in denen sie verwendet wird, definieren.  
  
7.  Klicken Sie auf die Registerkarte **Partitionen** .  
  
     Vom Cube-Assistenten wird eine einzelne Partition für den Cube definiert. Dabei wird der MOLAP-Speichermodus (Multidimensional Online Analytical Processing) ohne Aggregationen verwendet. Mit MOLAP werden alle Daten der Blattebene und alle Aggregationen innerhalb des Cubes gespeichert. Dies optimiert die Leistung. Aggregationen sind im Voraus berechnete Zusammenfassungen von Daten, mit denen die Abfrageantwortzeit verbessert werden kann, da die Antworten schon vorhanden sind, wenn Fragen gestellt werden. Auf der Registerkarte **Partitionen** können Sie zusätzliche Partitionen, Speichereinstellungen und Rück schreibe Einstellungen definieren. Weitere Informationen finden Sie unter [Partitionen &#40;Analysis Services-Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md), [Aggregationen und Aggregations Entwürfe](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
8.  Klicken Sie auf die Registerkarte **Browser** .  
  
     Der Cube kann nicht durchsucht werden, da er noch nicht in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]bereitgestellt wurde. Zum aktuellen Zeitpunkt besteht der Cube im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekt nur aus einer Cubedefinition, die Sie in einer beliebigen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]bereitstellen können. Beim Bereitstellen und Verarbeiten eines Cubes erstellen Sie die definierten Objekte in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und füllen sie mit Daten aus den zugrunde liegenden Datenquellen auf.  
  
9. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Analysis Services Tutorial** im **Cubes** -Knoten und anschließend auf **Code anzeigen**. Sie müssen möglicherweise einen Moment warten.  
  
     Der XML-Code für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] den Tutorial-Cube wird auf der ** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Registerkarte Tutorial. Cube [XML]** angezeigt. Dies ist der tatsächliche Code, der verwendet wird, um den Cube während der bereit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Stellung in einer Instanz von zu erstellen. Weitere Informationen finden Sie unter [Anzeigen des XML für ein Analysis Services-Projekt &#40;SSDT&#41;](multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).  
  
10. Schließen Sie die Registerkarte mit dem XML-Code.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Bereitstellen eines Analysis Services-Projekts](lesson-2-5-deploying-an-analysis-services-project.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Dimensionsdaten im Dimensions-Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)  
  
  
