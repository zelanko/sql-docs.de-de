---
title: Dimensions Beziehungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- relationships [Analysis Services]
- member groups [Analysis Services]
- regular dimensions [Analysis Services]
- many-to-many relationships [Analysis Services]
- cubes [Analysis Services], relationships
- reference dimensions
- dimensions [Analysis Services], relationships
- fact dimensions [Analysis Services]
- relationships [Analysis Services], dimensions
ms.assetid: de54c059-cb0f-4f66-bd70-8605af05ec4f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e1fe1521f2eebaa4413b49c315f17a6b1b6a5914
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887936"
---
# <a name="dimension-relationships"></a>Dimensionsbeziehungen
  Durch die Dimensionsverwendung werden die Beziehungen zwischen Cubedimensionen und den Measuregruppen in einem Cube definiert. Bei einer Cubedimension handelt es sich um eine Instanz einer Datenbankdimension, die in einem bestimmten Cube verwendet wird. Ein Cube kann über Cubedimensionen verfügen (und verfügt oft über solche), die nicht direkt mit einer Measuregruppe verknüpft sind, die jedoch möglicherweise über eine andere Dimension oder Measuregruppe indirekt mit der Measuregruppe verknüpft sind. Wenn Sie einem Cube eine Datenbankdimension oder Measuregruppe hinzufügen, versucht [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Dimensionsverwendung zu bestimmen, indem die Beziehungen zwischen den Dimensionstabellen und Faktentabellen in der Datenquellensicht des Cubes sowie die Beziehungen zwischen Attributen einer Dimension untersucht werden. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legt die Einstellungen für die Dimensionsverwendung für die erkannten Beziehungen automatisch fest.  
  
 Eine Beziehung zwischen einer Dimension und einer Measuregruppe besteht aus den an der Beziehung teilnehmenden Dimensions- und Faktentabellen und einem Granularitätsattribut, das die Granularität der Dimension in der jeweiligen Measuregruppe angibt.  
  
## <a name="regular-dimension-relationships"></a>Reguläre Dimensionsbeziehungen  
 Eine reguläre Dimensionsbeziehung zwischen einer Cubedimension und einer Measuregruppe ist vorhanden, wenn die Schlüsselspalte der Dimension direkt mit der Faktentabelle verknüpft ist. Diese direkte Beziehung basiert auf einer Primärschlüssel-Fremdschlüssel-Beziehung in der zugrunde liegenden relationalen Datenbank, kann jedoch auch auf einer in der Datenquellen Sicht definierten logischen Beziehung basieren. Eine reguläre Dimensionsbeziehung stellt die Beziehung zwischen Dimensionstabellen und einer Faktentabelle in einem traditionellen Sternschemaentwurf dar. Weitere Informationen zu regulären Beziehungen finden Sie unter [Definieren einer regulären Beziehung und regulärer Beziehungs Eigenschaften](../multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).  
  
## <a name="reference-dimension-relationships"></a>Bezugsdimensionsbeziehungen  
 Eine Bezugsdimensionsbeziehung zwischen einer Cubedimension und einer Measuregruppe ist vorhanden, wenn die Schlüsselspalte für die Dimension über einen Schlüssel in einer anderen Dimensionstabelle indirekt mit der Faktentabelle verknüpft ist, wie in der folgenden Abbildung gezeigt.  
  
 ![Logisches Diagramm, referenzierte Dimensions Beziehung] (https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-refdimension1.gif "Logisches Diagramm, referenzierte Dimensions Beziehung")  
  
 Eine Bezugsdimensionsbeziehung stellt die Beziehung zwischen Dimensionstabellen und einer Faktentabelle in einem Schneeflocken-Schemaentwurf dar. Wenn Dimensionstabellen in einem Schneeflockenschema verbunden sind, können Sie eine einzelne Dimension mithilfe von Spalten aus mehreren Tabellen definieren, oder Sie können separate Dimensionen basierend auf den separaten Dimensionstabellen definieren und anschließend mithilfe der Einstellung für die Bezugsdimensionsbeziehung einen Link zwischen ihnen definieren. Die folgende Abbildung zeigt eine Faktentabelle namens **InternetSales**und zwei Dimensionstabellen namens **Customer** und **Geography**in einem Schneeflockenschema.  
  
 ![Logisches Schema, referenzierte Dimensions Beziehung] (https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-refdim-schema1.gif "Logisches Schema, referenzierte Dimensions Beziehung")  
  
 Sie können eine Dimension mit der **Customer** -Tabelle als Haupttabelle der Dimension erstellen und die **Geography** -Tabelle als verknüpfte Tabelle einschließen. Anschließend wird eine reguläre Beziehung zwischen der Dimension und der InternetSales-Measuregruppe definiert.  
  
 Alternativ können Sie zwei mit der InternetSales-Measuregruppe verknüpfte Dimensionen erstellen: eine auf der **Customer** -Tabelle basierende Dimension und eine auf der **Geography** -Tabelle basierende Dimension. Anschließend können Sie die Geography-Dimension mit einer Bezugsdimensionsbeziehung mithilfe der Customer-Dimension mit der InternetSales-Measuregruppe verknüpfen. In diesem Fall werden die Fakten in der InternetSales-Measuregruppe, wenn sie durch die Geography-Dimension dimensioniert werden, nach Kunde und nach Geografie dimensioniert. Wenn der Cube eine zweite Measuregruppe namens Reseller Sales enthalten würde, können Sie die Fakten in der Reseller Sales-Measuregruppe nicht durch Geography dimensionieren, da keine Beziehung zwischen Reseller Sales und Geography vorhanden wäre.  
  
 Es gibt keine Begrenzung der Anzahl der Bezugsdimensionen, die miteinander verkettet werden können, wie in der folgenden Abbildung gezeigt.  
  
 ![Logisches Diagramm, referenzierte Dimensions Beziehung] (https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-refdimension2.gif "Logisches Diagramm, referenzierte Dimensions Beziehung")  
  
 Weitere Informationen zu referenzierten Beziehungen finden Sie unter [Definieren einer referenzierten Beziehung und Eigenschaften der referenzierten Beziehung](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md).  
  
## <a name="fact-dimension-relationships"></a>Faktendimensionsbeziehungen  
 Faktendimensionen, die häufig als degenerierte Dimensionen bezeichnet werden, sind Standarddimensionen, die aus Attributspalten in Faktentabellen statt aus Attributspalten in Dimensionstabellen erstellt werden. Nützliche Dimensionsdaten werden manchmal in einer Faktentabelle gespeichert, um die Duplizierung zu reduzieren. Im folgenden Diagramm wird z. B. die **FactResellerSales** -Faktentabelle aus der [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] -Beispieldatenbank angezeigt.  
  
 ![Spalten in der Fakten Tabelle können Dimensionen unterstützen](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-factdim.gif "Spalten in der Fakten Tabelle können Dimensionen unterstützen") .  
  
 Die Tabelle enthält Attributinformationen nicht nur für jede Zeile einer von einem Wiederverkäufer aufgegebenen Bestellung, sondern auch zu der Bestellung selbst. Die im vorherigen Diagramm eingekreisten Attribute identifizieren die Informationen in der **FactResellerSales** -Tabelle, die als Attribute in einer Dimension verwendet werden können. In diesem Fall werden zwei zusätzliche Informationen, die Transporteurkennung und die vom Wiederverkäufer ausgegebene Nummer der Bestellung, durch die Attributspalten CarrierTrackingNumber und CustomerPONumber dargestellt. Diese Informationen sind interessant, z. b. sind die Benutzer definitiv daran interessiert, aggregierte Informationen, z. b. die Gesamtproduktkosten, für alle Bestellungen zu sehen, die unter einer einzigen nach Verfolgungs Nummer ausgeliefert werden. Aber ohne eine Dimension gibt es keine Möglichkeit, Daten für diese beiden Attribute zu organisieren oder zu aggregieren.  
  
 Theoretisch können Sie eine Dimensionstabelle erstellen, die die gleichen Schlüsselinformationen verwendet wie die FactResellerSales-Tabelle, und die anderen beiden Attributspalten, CarrierTrackingNumber und CustomerPONumber, in jene Dimensionstabelle verschieben. Sie würden jedoch einen wesentlichen Teil der Daten duplizieren und dem Data Warehouse unnötige Komplexität hinzufügen, um lediglich zwei Attribute als separate Dimension darzustellen.  
  
> [!NOTE]  
>  Faktendimensionen werden häufig zur Unterstützung von Drillthroughaktionen verwendet. Weitere Informationen zu Aktionstypen finden Sie unter [Aktionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Faktendimensionen müssen nach jedem Update der Measuregruppe, auf die durch die Faktenbeziehung verwiesen wird, inkrementell aktualisiert werden. Wenn es sich bei der Faktendimension um eine ROLAP-Dimension handelt, löscht die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Verarbeitungs-Engine alle Caches und verarbeitet die Measuregruppe inkrementell.  
  
 Weitere Informationen zu Fakten Beziehungen finden Sie unter [Definieren von Fakten Beziehungen und Fakten Beziehungs Eigenschaften](../multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).  
  
## <a name="many-to-many-dimension-relationships"></a>m:n-Dimensionsbeziehungen  
 In den meisten Dimensionen ist jedes Faktum mit einem und nur einem Dimensionselement verknüpft, und ein einzelnes Dimensionselement kann mehreren Fakten zugeordnet sein. In der Terminologie von relationalen Datenbanken wird dies als 1:n-Beziehung bezeichnet. Es ist jedoch oft nützlich, ein einzelnes Faktum mit mehreren Dimensionselementen zu verknüpfen. Ein Bankkunde verfügt z. B. möglicherweise über mehrere Konten (Giro-, Sparbuch-, Kreditkarten- und Investmentkonten), und ein Konto kann auch über gemeinsame oder mehrere Besitzer verfügen. Die aus diesen Beziehungen erstellte Customer-Dimension hätte dann mehrere Elemente, die mit einer einzelnen Kontotransaktion verknüpft sind.  
  
 ![Logische Schema/] m:n-Dimensionsbeziehung (https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-many-dimension1.gif "Logische Schema/") m:n-Dimensionsbeziehung  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht es Ihnen, eine m:n-Beziehung zwischen einer Dimension und einer Fakten Tabelle zu definieren.  
  
> [!NOTE]  
>  Zur Unterstützung einer m:n-Dimensionsbeziehung muss in der Datenquellensicht eine Fremdschlüsselbeziehung zwischen allen beteiligten Tabellen eingerichtet worden sein, wie in der vorherigen Abbildung dargestellt ist. Andernfalls können Sie beim Einrichten der Beziehung auf der Registerkarte **Dimensionsverwendung** des Dimensions-Designers nicht die richtige Zwischenmeasuregruppe auswählen.  
  
 Weitere Informationen zu m:n-Beziehungen finden Sie unter Definieren einer m:n-Beziehung [und m:n-Beziehungseigenschaften](../multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
