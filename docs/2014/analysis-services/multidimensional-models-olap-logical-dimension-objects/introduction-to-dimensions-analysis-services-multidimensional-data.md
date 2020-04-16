---
title: Einführung in Dimensionen (Analysis Services - Multidimensional Data) | Microsoft Docs
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
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387900"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>Einführung in Dimensionen (Analysis Services &ndash; Mehrdimensionale Daten)
  Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Microsoft-Dimensionen sind Gruppen von Attributen, die auf Spalten aus Tabellen oder Ansichten in einer Datenquellenansicht basieren. Dimensionen sind unabhängig von einem Cube vorhanden, können sowohl in mehreren Cubes als auch mehrfach in einem einzelnen Cube verwendet und zwischen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanzen verknüpft werden. Eine unabhängig von einem Cube vorhandene Dimension wird als Datenbankdimension bezeichnet und eine innerhalb eines Cubes verwendete Instanz einer Datenbankdimension als Cubedimension.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Dimension auf Basis eines Sternschemaentwurfs  
 Die Struktur einer Dimension hängt größtenteils von der Struktur der zugrunde liegenden Dimensionstabellen ab. Die einfachste Struktur ist das Sternschema, bei dem jede Dimension auf einer einzelnen Dimensionstabelle basiert, die über einen Primärschlüssel direkt mit der Faktentabelle verknüpft ist - Fremdschlüsselbeziehung.  
  
 Das folgende Diagramm veranschaulicht einen [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] Unterabschnitt der Beispieldatenbank, in dem sich die **FactResellerSales-Faktentabelle** auf zwei Dimensionstabellen, **DimReseller** und **DimPromotion**, bezieht. Die **Spalte ResellerKey** in der **FactResellerSales-Faktentabelle** definiert eine Fremdschlüsselbeziehung zur **Primärschlüsselspalte ResellerKey** in der **DimReseller-Dimensionstabelle.** In ähnlicher Weise definiert die **Spalte PromotionKey** in der **FactResellerSales-Faktentabelle** eine Fremdschlüsselbeziehung zur **Primärschlüsselspalte PromotionKey** in der **DimPromotion-Dimensionstabelle.**  
  
 ![Logisches Schema für Faktendimensionsbeziehung](../../analysis-services/dev-guide/media/dimfactrelationship.gif "Logisches Schema für Faktendimensionsbeziehung")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Dimension auf Basis eines Schneeflocken-Schemaentwurfs  
 In vielen Fällen ist eine komplexere Struktur erforderlich, da zum Definieren der Dimension Informationen aus mehreren Tabellen erforderlich sind. In dieser Struktur, die als Schneeflockenschema bezeichnet wird, basieren die einzelnen Dimensionen auf Attributen aus Spalten mehrerer Tabellen, die über Primärschlüssel-Fremdschlüssel-Beziehungen miteinander und letztendlich mit der Faktentabelle verknüpft sind. Das folgende Diagramm veranschaulicht beispielsweise die Tabellen, die erforderlich sind, um die Produktdimension im **AdventureWorksDW-Beispielprojekt** vollständig zu beschreiben:  
  
 ![Tabellen für die AdventureWorksAS-Dimension für Product](../../analysis-services/dev-guide/media/dimproduct.gif "Tabellen für die AdventureWorksAS-Dimension für Product")  
  
 Um ein Produkt vollständig beschreiben zu können, müssen Kategorie und Unterkategorie des Produkts in der Product-Dimension enthalten sein. Diese Informationen befinden sich jedoch nicht direkt in der Haupttabelle für die **DimProduct-Dimension.** Eine Fremdschlüsselbeziehung von **DimProduct** zu **DimProductSubcategory**, die wiederum eine Fremdschlüsselbeziehung zur Tabelle **DimProductCategory** hat, ermöglicht es, die Informationen für Produktkategorien und Unterkategorien in die Produktdimension aufzunehmen.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Schneeflockenschema im Vergleich zur Bezugsdimensionsbeziehung  
 Manchmal haben Sie die Wahl, ob Sie Attribute in einer Dimension mithilfe eines Schneeflockenschemas aus mehreren Tabellen erstellen oder ob Sie zwei separate Dimensionen definieren und eine auf dem Konzept der Bezugsdimension basierende Beziehung zwischen ihnen festlegen. Das folgende Diagramm veranschaulicht dieses Szenario.  
  
 ![Logisches Schema für Beispielverweisdimension](../../analysis-services/dev-guide/media/dimindirect.gif "Logisches Schema für Beispielverweisdimension")  
  
 Im vorherigen Diagramm hat die **FactResellerSales-Faktentabelle** keine Fremdschlüsselbeziehung mit der **DimGeography-Dimensionstabelle.** Die **FactResellerSales-Faktentabelle** weist jedoch eine Fremdschlüsselbeziehung mit der **DimReseller-Dimensionstabelle** auf, die wiederum eine Fremdschlüsselbeziehung mit der **DimGeography-Dimensionstabelle** hat. Um eine Reseller-Dimension zu definieren, die Geographieinformationen zu jedem Wiederverkäufer enthält, müssen Sie diese Attribute aus den **DimGeography-** und **dimReseller-Dimensionstabellen** abrufen. In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erzielen Sie dasselbe Ergebnis, wenn Sie zwei separate Dimensionen erstellen und diese innerhalb einer Measuregruppe verknüpfen, indem Sie eine auf dem Konzept der Bezugsdimension basierende Beziehung zwischen beiden Dimensionen definieren. Weitere Informationen zu Referenzdimensionsbeziehungen finden Sie unter [Dimensionsbeziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Ein Vorteil der Verwendung von Bezugsdimensionsbeziehungen in diesem Szenario liegt darin, dass Sie eine einzelne Geography-Dimension und anschließend mehrere darauf basierende Cubedimensionen erstellen können, ohne zusätzlichen Speicherplatz zu benötigen. Sie können z. B. eine der Geography-Cubedimensionen mit einer Reseller-Dimension verknüpfen und eine andere mit einer Customer-Dimension. **Zugehörige Themen:**[Dimensionsbeziehungen](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Definieren einer referenzierten Beziehung und Referenzbeziehungseigenschaften](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Verarbeiten einer Dimension  
 Wenn Sie eine Dimension erstellt haben, müssen Sie diese verarbeiten, bevor Sie die Elemente der Attribute und Hierarchien in der Dimension anzeigen können. Wenn sich die Struktur einer Dimension geändert hat oder die Informationen in den zugrunde liegenden Tabellen aktualisiert wurden, müssen Sie die Dimension erneut verarbeiten, bevor Sie die Änderungen anzeigen können. Beim Verarbeiten einer Dimension nach einer strukturellen Änderung müssen sämtliche Cubes, die die Dimension enthalten, ebenfalls verarbeitet werden. Andernfalls kann der Cube nicht angezeigt werden.  
  
## <a name="security"></a>Sicherheit  
 Alle untergeordneten Objekte einer Dimension, einschließlich Hierarchien, Ebenen und Elementen, werden mithilfe von Rollen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gesichert. Die Dimensionssicherheit kann für alle Cubes in der Datenbank angewendet werden, die die Dimension verwenden, oder nur für einen bestimmten Cube. Weitere Informationen zur Dimensionssicherheit finden Sie unter [Gewähren von Berechtigungen für eine Dimension &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensionsspeicherung](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Dimensionsübersetzungen](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
