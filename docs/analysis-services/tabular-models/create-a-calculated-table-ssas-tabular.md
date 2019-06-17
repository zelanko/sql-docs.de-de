---
title: Erstellen einer berechneten Tabelle in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 12/19/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 199096efcdf9212e19e1055f1276079eddfb1a75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62469370"
---
# <a name="create-a-calculated-table"></a>Erstellen einer berechneten Tabelle 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Eine *berechnete Tabelle* ist ein berechnetes Objekt, basierend entweder auf einer DAX-Abfrage oder einem -Ausdruck, abgeleitet aus ganzen oder Teilen anderer Tabellen im gleichen Modell.  
  
 Ein weit verbreitetes Entwurfsproblem, das berechnete Tabellen lösen können, ist das Hervorholen einer Dimension mit unterschiedlichen Rollen in einem bestimmten Kontext, damit Sie diese als eine Abfragestruktur in Clientanwendungen anzeigen können.  Möglicherweise erinnern Sie sich daran, dass eine Dimension mit unterschiedlichen Rollen einfach eine Tabelle ist, die in mehreren Kontexten aufgezeigt wird. Ein klassisches Beispiel ist Date-Tabelle, angezeigt als OrderDate, ShipDate, oder DueDate, je nach Fremdschlüsselbeziehung. Indem Sie explizit für „ShipDate“ eine berechnete Tabelle erstellen, erhalten Sie eine eigenständige Tabelle, die für Abfragen zur Verfügung steht und genauso vollständig ausgeführt werden kann wie jede andere Tabelle. Eine weitere Verwendungsmöglichkeit umfasst das Konfigurieren eines gefilterten Rowset, einer Teilmenge oder Obermenge der Spalten aus anderen vorhandenen Tabellen. Dadurch können Sie die ursprüngliche Tabelle intakt halten, während Sie Varianten dieser Tabelle erstellen, um verschiedenen Szenarios zu unterstützen.  
  
 Die Verwendung von berechneten Tabellen zur optimalen Vorteilserzielung erfordert, dass Sie sich zumindest etwas mit DAX auskennen. Wie Sie für die Tabelle mit Ausdrücken arbeiten, ist es möglicherweise hilfreich um zu wissen, dass eine berechnete Tabelle eine einzelne Partition mit DAX-Quelle enthält, in dem der Ausdruck ein DAX-Ausdruck ist.  
Es gibt für jede, vom Ausdruck zurückgegebene Spalte eine CalculatedTableColumn, bei der die SourceColumn der Name der zurückgegebenen Spalte ist (ähnlich zu DataColumns in nicht berechneten Tabellen). 

Mindestens eine Tabelle muss bereits vorhanden sein, bevor Sie eine berechnete Tabelle erstellen können. Wenn Sie eine berechnete Tabelle als eigenständiges Objekt berechnete Tabelle erstellen, können Sie zuerst eine Tabelle erstellen, durch das Importieren aus einer Dateidatenquelle (Csv, Xls, Xml). Die Datei, die importiert werden kann es sich um eine einzelne Spalte und einen einzelnen Wert enthalten. Sie können diese Tabelle ausblenden. 
  
## <a name="how-to-create-a-calculated-table"></a>So erstellen Sie eine berechnete Tabelle  
  
1.  Stellen Sie zunächst sicher, dass das tabellarische Modell einen Kompatibilitätsgrad von 1200 oder höher verfügt. Sie können die **Kompatibilitätsgrad** -Eigenschaft für das Modell in SSDT überprüfen.  
  
2.  Wechseln Sie zur Datensicht. Sie können in der Diagrammansicht keine berechnete Tabelle erstellen.  
  
3.  Wählen Sie **Tabelle** > **Neue berechnete Tabelle**aus.  
  
4.  Geben Sie einen DAX-Ausdruck ein, oder kopieren Sie ihn herein (unten finden Sie ein paar Ideen).  
  
5.  Geben Sie der Tabelle einen Namen.  
  
6.  Erstellen Sie Beziehungen zu anderen Tabellen im Modell. Finden Sie unter [Erstellen einer Beziehung zwischen zwei Tabellen](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md) Wenn Sie Hilfe bei diesem Schritt benötigen.  
  
7.  Verweisen Sie in Berechnungen oder Ausdrücken in Ihrem Modell auf die berechnete Tabelle, oder verwenden Sie **Analysieren in Excel** für das Ad-hoc-Durchsuchen von Daten.  
  
### <a name="replicate-a-role-playing-dimension"></a>Replizieren einer Dimension mit unterschiedlichen Rollen  
 Geben Sie in der Bearbeitungsleiste eine DAX-Formel ein, die eine Kopie einer anderen Tabelle abruft. Geben Sie der berechneten Tabelle, nachdem sie aufgefüllt wurde, einen beschreibenden Namen, und richten Sie dann eine Beziehung ein, die den rollenspezifischen Fremdschlüssel verwendet. Beispielsweise könnten Sie in der AdventureWorks-Datenbank eine berechnete Tabelle für das Fälligkeitsdatum erstellen und den DueDateKey als Grundlage für eine Beziehung mit der Faktentabelle verwenden.  
  
```  
=DimDate  
```  
  
### <a name="summarized-or-filtered-dataset"></a>Zusammengefasstes oder gefiltertes Dataset  
 Geben Sie in der Bearbeitungsleiste einen DAX-Ausdruck ein, der ein Dataset filtert, zusammenfasst oder anderweitig bearbeitet, damit dieses die von Ihnen gewünschten Datenzeilen enthält. Dieses Beispiel gruppiert nach Verkäufen, nach Farbe und nach Währung.  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### <a name="superset-using-columns-from-multiple-tables"></a>Obermenge, die Spalten aus verschiedenen Tabellen verwendet  
 Geben Sie in der Bearbeitungsleiste einen DAX-Ausdruck ein, der Spalten aus mehreren Tabellen kombiniert. In diesem Fall listet die Abfrageausgabe eine Produktkategorie für jede Währung auf.  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Kompatibilitätsgrad](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Data Analysis Expressions &#40;DAX&#41; in Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5)   
 [Grundlegendes zu DAX in tabellarischen Modellen](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  
