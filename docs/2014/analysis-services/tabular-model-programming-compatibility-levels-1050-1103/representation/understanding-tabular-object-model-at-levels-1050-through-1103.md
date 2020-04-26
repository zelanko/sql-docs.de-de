---
title: Grundlegendes zum tabellarischen Objektmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6077b7e8-cb3e-4480-a5de-bb602cf9d69a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dcfd16ae7e49392c9ba0a001ea8d205c4fa88d1c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62795341"
---
# <a name="understanding-the-tabular-object-model"></a>Grundlegendes zum tabellarischen Objektmodell
  Ein tabellarisches Modell ist eine logische Darstellung von Tabellen, Beziehungen, Hierarchien, Perspektiven, Measures und der Schlüsselleistung. In diesem Abschnitt wird die interne Implementierung mithilfe von AMO eingeführt. Wenn Sie AMO noch nicht verwendet haben, finden Sie weitere Informationen [unter Entwickeln mit Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo) .  
  
 Es wird ein Top-Down-Ansatz verwendet. Alle relevanten Objekte im tabellarischen Modell werden den AMO-Objekten logisch zugeordnet, und die erforderliche Interaktion oder der erforderliche Workflow werden erläutert. Ein Quellcodebeispiel für die Erstellung eines tabellarischen Modells mit AMO, AMO2Tabular, ist unter Codeplex verfügbar. Ein wichtiger Hinweis zum Code im Beispiel: Dieser wird nur zur Verdeutlichung der hier erläuterten logischen Konzepte bereitgestellt und sollte nicht in einer Produktionsumgebung verwendet werden. Das Beispiel wird ohne Support oder Garantie bereitgestellt.  
  
## <a name="database-representation"></a>Datenbankdarstellung  
 Eine Datenbank stellt das Containerobjekt für das tabellarische Modell bereit. Alle Objekte in einem tabellarischen Modell sind in der Datenbank enthalten. Im Hinblick auf AMO-Objekte verfügt eine Datenbankdarstellung über eine 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Database>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Beachten Sie, dass dies nicht bedeutet, dass beim Erstellen von Modellen alle im AMO-Datenbankobjekt enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Daten Bank Darstellung finden Sie unter [Daten Bank Darstellung&#40;tabellarischen&#41;](database-representation-tabular.md) .  
  
## <a name="connection-representation"></a>Verbindungsdarstellung  
 Durch eine Verbindung wird die Beziehung zwischen den Daten, die in eine Projektmappe für tabellarische Modelle aufgenommen werden sollen, und dem Modell selbst hergestellt. Im Hinblick auf AMO-Objekte verfügt eine Verbindung über eine 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.DataSource>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Beachten Sie, dass dies nicht bedeutet, dass beim Erstellen von Modellen alle im AMO-Datenquellenobjekt enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Datenquellen Darstellung finden Sie unter [Verbindungs Darstellung &#40;tabellarischen&#41;](connection-representation-tabular.md) .  
  
## <a name="table-representation"></a>Tabellendarstellung  
 Tabellen sind Datenbankobjekte, die die Daten in der Datenbank enthalten. Im Hinblick auf AMO-Objekte hat eine Tabelle eine 1:n-Zuordnungsbeziehung. Eine Tabelle wird durch die Verwendung der folgenden AMO-Objekte dargestellt: <xref:Microsoft.AnalysisServices.DataSourceView>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.CubeDimension>, <xref:Microsoft.AnalysisServices.MeasureGroup> und <xref:Microsoft.AnalysisServices.Partition> sind die erforderlichen Hauptobjekte. Beachten Sie jedoch, dass dies nicht bedeutet, dass bei der Modellierung alle in den zuvor erwähnten AMO-Objekten enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Tabellen Darstellung finden Sie unter [Tabellen Darstellung &#40;tabellarischen&#41;](tables-representation-tabular.md) .  
  
### <a name="calculated-column-representation"></a>Darstellung einer berechneten Spalte  
 Berechnete Spalten sind ausgewertete Ausdrücke, die eine Spalte in einer Tabelle generieren, wo ein neuer Wert berechnet wird und für jede Zeile in der Tabelle gespeichert wird. Im Hinblick auf AMO-Objekte verfügt eine berechnete Spalte über eine 1:n-Zuordnungsbeziehung. Eine berechnete Spalte wird durch die Verwendung der folgenden AMO-Objekte dargestellt: <xref:Microsoft.AnalysisServices.Dimension> und <xref:Microsoft.AnalysisServices.MeasureGroup> sind die erforderlichen Hauptobjekte. Beachten Sie, dass dies nicht bedeutet, dass beim Modellieren alle in den zuvor erwähnten AMO-Objekten enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Darstellung berechneter Spalten finden Sie unter [berechnete Spalten Darstellung &#40;tabellarischen&#41;](tables-calculated-column-representation.md) .  
  
### <a name="calculated-measure-representation"></a>Darstellung eines berechneten Measures  
 Berechnete Measures sind gespeicherte Ausdrücke, die auf Anfrage ausgewertet werden, sobald das Modell bereitgestellt wird. Im Hinblick auf AMO-Objekte verfügt ein berechnetes Measure über eine 1:n-Zuordnungsbeziehung. Eine berechnete Spalte wird durch die Verwendung der folgenden AMO-Objekte dargestellt: <xref:Microsoft.AnalysisServices.MdxScript.Commands%2A> und <xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A> sind die erforderlichen Hauptobjekte. Beachten Sie, dass dies nicht bedeutet, dass beim Modellieren alle in den zuvor erwähnten AMO-Objekten enthaltenen Objekte verwendet werden können.  
  
> [!NOTE]  
>  Die <xref:Microsoft.AnalysisServices.Measure>-Objekte weisen keine Beziehung zu den berechneten Measures in tabellarischen Modellen auf und werden in tabellarischen Modellen nicht unterstützt.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Darstellung des berechneten Measures finden Sie unter [berechnete Measure-Darstellung &#40;tabellarischen&#41;](tables-calculated-measure-representation.md) .  
  
### <a name="hierarchy-representation"></a>Hierarchiedarstellung  
 Hierarchien sind ein Mechanismus, dem Endbenutzer umfangreichere Drillup- und Drilldownfunktionen bereitzustellen. Im Hinblick auf AMO-Objekte verfügt eine Hierarchiedarstellung über eine 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Hierarchy>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Beachten Sie, dass dies nicht bedeutet, dass beim Erstellen tabellarischer Modelle alle im AMO-Datenbankobjekt enthaltenen Objekte verwendet werden können.  
  
 In der [Hierarchie Darstellung &#40;tabellarischen&#41;](tables-hierarchy-representation.md) finden Sie eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Hierarchie Darstellung.  
  
### <a name="key-performance-indicator--kpi--representation"></a>Key Performance Indicator-KPI-Darstellung  
 Ein KPI misst die Leistung eines Werts, der durch ein Basismeasure definiert wird, anhand eines Zielwerts. Im Hinblick auf AMO-Objekte verfügt eine KPI-Darstellung über eine 1:n-Zuordnungsbeziehung. Ein KPI wird durch die Verwendung der folgenden AMO-Objekte dargestellt: <xref:Microsoft.AnalysisServices.MdxScript.Commands%2A> und <xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A> sind die erforderlichen Hauptobjekte.  Beachten Sie, dass dies nicht bedeutet, dass beim Modellieren alle in den zuvor erwähnten AMO-Objekten enthaltenen Objekte verwendet werden können.  
  
> [!NOTE]  
>  Ein weiterer wichtiger Unterschied besteht darin, dass die <xref:Microsoft.AnalysisServices.Kpi>-Objekte keine Beziehung zu den KPIs in tabellarischen Modellen aufweisen. Außerdem werden sie in tabellarischen Modellen nicht unterstützt.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der KPI-Darstellung finden Sie unter [Key Performance Indicator-Darstellung &#40;tabellarischen&#41;](tables-key-performance-indicator-representation.md) .  
  
### <a name="partition-representation"></a>Partitionsdarstellung  
 Zu Funktionszwecken kann eine Tabelle in verschiedene Teilmengen von Zeilen geteilt werden, die zusammengefasst die Tabelle ergeben. Jede dieser Teilmengen ist eine Partition der Tabelle. Im Hinblick auf AMO-Objekte verfügt eine Partitionsdarstellung über eine 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Partition>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Beachten Sie, dass dies nicht bedeutet, dass beim Erstellen von Modellen alle im AMO-Datenbankobjekt enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Partitions Darstellung finden Sie unter [Partitions Darstellung &#40;tabellarischen&#41;](tables-partition-representation.md) .  
  
## <a name="relationship-representation"></a>Beziehungsdarstellung  
 Eine Beziehung ist eine Verbindung zwischen zwei Tabellen mit Daten. Die Beziehung legt fest, wie die Daten in den beiden Tabellen korreliert werden sollen.  
  
 In tabellarischen Modellen können mehrere Beziehungen zwischen zwei Tabellen definiert werden. Wenn mehrere Beziehungen zwischen zwei Tabellen definiert werden, kann nur eine als aktive Standardbeziehung definiert werden. Alle anderen Beziehungen sind inaktiv.  
  
 Im Hinblick auf AMO-Objekte verfügen alle inaktiven Beziehungen über eine Darstellung einer 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Relationship>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Für die aktive Beziehung gelten andere Anforderungen, und es ist zusätzlich eine Zuordnung zu <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension> erforderlich. Beachten Sie, dass dies nicht bedeutet, dass beim Modellieren alle in der AMO-Beziehung oder dem referenceMeasureGroupDimension-Objekt enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der Beziehungs Darstellung finden Sie unter [Beziehungs Darstellung &#40;tabellarischen&#41;](relationship-representation-tabular.md) .  
  
## <a name="perspective-representation"></a>Perspektivendarstellung  
 Eine Perspektive ist ein Mechanismus, um den Modus zu vereinfachen oder zu fokussieren. Im Hinblick auf AMO-Objekte verfügt eine Beziehungsdarstellung über eine 1:1-Zuordnungsbeziehung zu <xref:Microsoft.AnalysisServices.Perspective>, und es sind keine weiteren AMO-Hauptobjekte erforderlich. Beachten Sie, dass dies nicht bedeutet, dass beim Erstellen tabellarischer Modelle alle im AMO-Perspektivenobjekt enthaltenen Objekte verwendet werden können.  
  
 Eine ausführliche Erläuterung zum Erstellen und Bearbeiten der perspektivischen Darstellung finden Sie unter [Perspektiven Darstellung &#40;tabellarischen&#41;](perspective-representation-tabular.md) .  
  
> [!WARNING]  
>  Perspektiven sind kein Sicherheitsmechanismus; auf Objekte außerhalb der Perspektive kann immer noch vom Benutzer über andere Schnittstellen zugegriffen werden.  
  
  
