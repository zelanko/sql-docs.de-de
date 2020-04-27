---
title: Dimensions Objekte (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c0c64f95b0c366453e1099c80d8e40b217fb7801
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702459"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Dimensionsobjekte (Analysis Services – Mehrdimensionale Daten)
  Ein einfaches <xref:Microsoft.AnalysisServices.Dimension>-Objekt besteht aus grundlegenden Informationen, Attributen und Hierarchien. Grundlegende Informationen beinhalten den Namen der Dimension, den Typ der Dimension, die Datenquelle, den Speichermodus usw. Attribute definieren die tatsächlichen Daten in der Dimension. Attribute gehören nicht notwendigerweise zu einer Hierarchie, aber Hierarchien werden aus Attributen erstellt. Eine Hierarchie erstellt geordnete Listen von Ebenen und definiert die Arten, wie ein Benutzer die Dimension durchsuchen kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen erhalten Sie weitere Informationen zum Entwerfen und Implementieren von Dimensionsobjekten.  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](dimensions-analysis-services-multidimensional-data.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]sind Dimensionen eine grundlegende Komponente von Cubes. Mit Dimensionen werden Daten nach Interessensbereichen geordnet, z. B. nach Kunden, Geschäften oder Angestellten.|  
|[Attribute und Attributhierarchien](attributes-and-attribute-hierarchies.md)|Dimensionen sind Auflistungen von Attributen, die an eine oder mehrere Spalten in einer Tabelle oder Sicht in der Datenquellensicht gebunden sind.|  
|[Attributbeziehungen](attribute-relationships.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]sind Attribute innerhalb einer Dimension immer entweder direkt oder indirekt mit dem Schlüssel Attribut verknüpft. Wenn Sie eine Dimension auf Basis eines Sternschemas definieren, in dem sämtliche Dimensionsattribute aus derselben relationalen Tabelle abgeleitet werden, wird automatisch eine Attributbeziehung zwischen dem Schlüsselattribut und den einzelnen Nichtschlüsselattributen definiert. Wenn Sie eine Dimension auf Basis eines Schneeflockenschemas definieren, in dem Dimensionsattribute aus mehreren verknüpften Tabellen abgeleitet werden, wird eine Attributbeziehung automatisch wie folgt definiert:<br /><br /> : Zwischen dem Schlüssel Attribut und den einzelnen nicht Schlüssel Attributen, die an Spalten in der Haupt Dimensions Tabelle gebunden sind.<br />: Zwischen dem Schlüssel Attribut und dem Attribut, das an den Fremdschlüssel in der sekundären Tabelle gebunden ist, die die zugrunde liegenden Dimensions Tabellen verknüpft.<br />: Zwischen dem Attribut, das an den Fremdschlüssel in der sekundären Tabelle gebunden ist, und jedem nicht Schlüssel Attribut, das an Spalten aus der sekundären Tabelle gebunden ist.|  
  
  
