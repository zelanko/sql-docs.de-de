---
title: Einführung in Dimensionen (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e1a78735cd5aee5ebc87adaac6fab48bb4e183d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81387900"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>Einführung in Dimensionen (Analysis Services &ndash; Mehrdimensionale Daten)
  Alle Dimensionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] von Microsoft sind Gruppen von Attributen auf der Grundlage von Spalten aus Tabellen oder Sichten in einer Datenquellen Sicht. Dimensionen sind unabhängig von einem Cube vorhanden, können sowohl in mehreren Cubes als auch mehrfach in einem einzelnen Cube verwendet und zwischen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanzen verknüpft werden. Eine unabhängig von einem Cube vorhandene Dimension wird als Datenbankdimension bezeichnet und eine innerhalb eines Cubes verwendete Instanz einer Datenbankdimension als Cubedimension.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Dimension auf Basis eines Sternschemaentwurfs  
 Die Struktur einer Dimension hängt größtenteils von der Struktur der zugrunde liegenden Dimensionstabellen ab. Die einfachste Struktur ist das Sternschema, bei dem jede Dimension auf einer einzelnen Dimensionstabelle basiert, die über einen Primärschlüssel direkt mit der Faktentabelle verknüpft ist - Fremdschlüsselbeziehung.  
  
 Das folgende Diagramm veranschaulicht einen unter Abschnitt der- [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] Beispieldatenbank, in der die **faktresellersales** -Fakten Tabelle mit zwei Dimensions Tabellen, **DimReseller** und **DimPromotion**, verknüpft ist. Die **ResellerKey** -Spalte in der **faktresellersales** -Fakten Tabelle definiert eine Fremdschlüssel Beziehung mit der **ResellerKey** -Primärschlüssel Spalte in der **DimReseller** -Dimensions Tabelle. Entsprechend definiert die **PromotionKey** -Spalte in der **faktresellersales** -Fakten Tabelle eine Fremdschlüssel Beziehung mit der **PromotionKey** -Primärschlüssel Spalte in der **DimPromotion** -Dimensions Tabelle.  
  
 ![Logisches Schema für Faktendimensionsbeziehung](../../analysis-services/dev-guide/media/dimfactrelationship.gif "Logisches Schema für Faktendimensionsbeziehung")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Dimension auf Basis eines Schneeflocken-Schemaentwurfs  
 In vielen Fällen ist eine komplexere Struktur erforderlich, da zum Definieren der Dimension Informationen aus mehreren Tabellen erforderlich sind. In dieser Struktur, die als Schneeflockenschema bezeichnet wird, basieren die einzelnen Dimensionen auf Attributen aus Spalten mehrerer Tabellen, die über Primärschlüssel-Fremdschlüssel-Beziehungen miteinander und letztendlich mit der Faktentabelle verknüpft sind. Das folgende Diagramm veranschaulicht beispielsweise die Tabellen, die erforderlich sind, um die Product-Dimension im **AdventureWorksDW** -Beispiel Projekt vollständig zu beschreiben:  
  
 ![Tabellen für die AdventureWorksAS-Dimension für Product](../../analysis-services/dev-guide/media/dimproduct.gif "Tabellen für die AdventureWorksAS-Dimension für Product")  
  
 Um ein Produkt vollständig beschreiben zu können, müssen Kategorie und Unterkategorie des Produkts in der Product-Dimension enthalten sein. Diese Informationen befinden sich jedoch nicht direkt in der Haupttabelle für die **DimProduct** -Dimension. Eine Fremdschlüssel Beziehung zwischen **DimProduct** und **DimProductSubcategory**, die wiederum über eine Fremdschlüssel Beziehung zur **DimProductCategory** -Tabelle verfügt, ermöglicht das Einschließen der Informationen für Produktkategorien und Unterkategorien in die Product-Dimension.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Schneeflockenschema im Vergleich zur Bezugsdimensionsbeziehung  
 Manchmal haben Sie die Wahl, ob Sie Attribute in einer Dimension mithilfe eines Schneeflockenschemas aus mehreren Tabellen erstellen oder ob Sie zwei separate Dimensionen definieren und eine auf dem Konzept der Bezugsdimension basierende Beziehung zwischen ihnen festlegen. Das folgende Diagramm veranschaulicht dieses Szenario.  
  
 ![Logisches Schema für Beispielverweisdimension](../../analysis-services/dev-guide/media/dimindirect.gif "Logisches Schema für Beispielverweisdimension")  
  
 Im vorherigen Diagramm hat die **faktresellersales** -Fakten Tabelle keine Fremdschlüssel Beziehung mit der **DimGeography** -Dimensions Tabelle. Die **faktresellersales** -Fakten Tabelle verfügt jedoch über eine Fremdschlüssel Beziehung mit der **DimReseller** -Dimensions Tabelle, die wiederum über eine Fremdschlüssel Beziehung mit der **DimGeography** -Dimensions Tabelle verfügt. Zum Definieren einer Reseller-Dimension, die geography-Informationen zu den einzelnen Wiederverkäufern enthält, müssten Sie diese Attribute aus den Dimensions Tabellen **DimGeography** und **DimReseller** abrufen. In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erzielen Sie dasselbe Ergebnis, wenn Sie zwei separate Dimensionen erstellen und diese innerhalb einer Measuregruppe verknüpfen, indem Sie eine auf dem Konzept der Bezugsdimension basierende Beziehung zwischen beiden Dimensionen definieren. Weitere Informationen zu Bezugs Dimensions Beziehungen finden Sie unter [Dimensions Beziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Ein Vorteil der Verwendung von Bezugsdimensionsbeziehungen in diesem Szenario liegt darin, dass Sie eine einzelne Geography-Dimension und anschließend mehrere darauf basierende Cubedimensionen erstellen können, ohne zusätzlichen Speicherplatz zu benötigen. Sie können z. B. eine der Geography-Cubedimensionen mit einer Reseller-Dimension verknüpfen und eine andere mit einer Customer-Dimension. **Verwandte Themen:**[Dimensions Beziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Definieren einer referenzierten Beziehung und Eigenschaften der referenzierten Beziehung](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Verarbeiten einer Dimension  
 Wenn Sie eine Dimension erstellt haben, müssen Sie diese verarbeiten, bevor Sie die Elemente der Attribute und Hierarchien in der Dimension anzeigen können. Wenn sich die Struktur einer Dimension geändert hat oder die Informationen in den zugrunde liegenden Tabellen aktualisiert wurden, müssen Sie die Dimension erneut verarbeiten, bevor Sie die Änderungen anzeigen können. Beim Verarbeiten einer Dimension nach einer strukturellen Änderung müssen sämtliche Cubes, die die Dimension enthalten, ebenfalls verarbeitet werden. Andernfalls kann der Cube nicht angezeigt werden.  
  
## <a name="security"></a>Sicherheit  
 Alle untergeordneten Objekte einer Dimension, einschließlich Hierarchien, Ebenen und Elementen, werden mithilfe von Rollen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gesichert. Die Dimensionssicherheit kann für alle Cubes in der Datenbank angewendet werden, die die Dimension verwenden, oder nur für einen bestimmten Cube. Weitere Informationen zur Dimensions Sicherheit finden Sie unter [Grant-Berechtigungen für eine Dimension &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Speicher](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Dimensions Übersetzungen](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
