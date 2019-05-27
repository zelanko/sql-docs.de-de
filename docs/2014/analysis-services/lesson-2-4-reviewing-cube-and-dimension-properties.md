---
title: Überprüfen von Cube- und Dimensionseigenschaften | Microsoft-Dokumentation
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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
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
  
     Dimensions-Designer enthält folgende Registerkarten: **Dimensionsstruktur**, **Attributbeziehungen**, **Übersetzungen**, und **Browser**. Beachten Sie, dass die **Dimensionsstruktur** Registerkarte enthält drei Bereiche: **Attribute**, **Hierarchien**, und **Datenquellensicht**. Die Attribute, die die Dimension enthält, werden im Bereich **Attribute** angezeigt. Weitere Informationen finden Sie unter [Dimensionsattributeigenschaftenverweis](multidimensional-models/dimension-attribute-properties-reference.md), [benutzerdefinierter Hierarchien](multidimensional-models/user-defined-hierarchies-create.md).  
  
5.  Um zum Cube-Designer zu wechseln, klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den **Analysis Services Tutorial** -Cube im **Cubes** -Knoten, und klicken Sie anschließend auf **Designer anzeigen**.  
  
6.  Klicken Sie im Cube-Designer auf die Registerkarte **Dimensionsverwendung** .  
  
     In dieser Ansicht des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cubes sehen Sie die von der Internet Sales-Measuregruppe verwendeten Cubedimensionen. Außerdem können Sie den Typ der Beziehung zwischen jeder Dimension und den einzelnen Measuregruppen, in denen sie verwendet wird, definieren.  
  
7.  Klicken Sie auf die Registerkarte **Partitionen** .  
  
     Vom Cube-Assistenten wird eine einzelne Partition für den Cube definiert. Dabei wird der MOLAP-Speichermodus (Multidimensional Online Analytical Processing) ohne Aggregationen verwendet. Mit MOLAP werden alle Daten der Blattebene und alle Aggregationen innerhalb des Cubes gespeichert. Dies optimiert die Leistung. Aggregationen sind im Voraus berechnete Zusammenfassungen von Daten, mit denen die Abfrageantwortzeit verbessert werden kann, da die Antworten schon vorhanden sind, wenn Fragen gestellt werden. Auf der Registerkarte **Partitionen** können Sie zusätzliche Partitionen, Speichereinstellungen und Rückschreibeeinstellungen definieren. Weitere Informationen zu Partitionen finden Sie unter [Partitionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) und [Aggregationen und Aggregationsentwürfe](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
8.  Klicken Sie auf die Registerkarte **Browser** .  
  
     Der Cube kann nicht durchsucht werden, da er noch nicht in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]bereitgestellt wurde. Zum aktuellen Zeitpunkt besteht der Cube im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekt nur aus einer Cubedefinition, die Sie in einer beliebigen Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]bereitstellen können. Beim Bereitstellen und Verarbeiten eines Cubes erstellen Sie die definierten Objekte in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und füllen sie mit Daten aus den zugrunde liegenden Datenquellen auf.  
  
9. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Analysis Services Tutorial** im **Cubes** -Knoten und anschließend auf **Code anzeigen**. Sie müssen möglicherweise einen Moment warten.  
  
     Der XML-Code für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube wird auf der Registerkarte **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.cube [XML]** angezeigt. Es handelt sich um den tatsächlichen Code, mit dem der Cube bei der Bereitstellung in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] erstellt wird. Weitere Informationen finden Sie unter [Anzeigen des XML für ein Analysis Services-Projekt &#40;SSDT&#41;](multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).  
  
10. Schließen Sie die Registerkarte mit dem XML-Code.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Bereitstellen eines Analysis Services-Projekts](lesson-2-5-deploying-an-analysis-services-project.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Dimensionsdaten im Dimensions-Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)  
  
  
