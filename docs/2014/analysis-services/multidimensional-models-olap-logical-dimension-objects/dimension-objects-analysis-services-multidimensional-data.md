---
title: Dimension-Objekten (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0ef31622b9b158ee55c4f31b437c1fed4679ad19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060834"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Dimensionsobjekte (Analysis Services – Mehrdimensionale Daten)
  Ein einfaches <xref:Microsoft.AnalysisServices.Dimension>-Objekt besteht aus grundlegenden Informationen, Attributen und Hierarchien. Grundlegende Informationen beinhalten den Namen der Dimension, den Typ der Dimension, die Datenquelle, den Speichermodus usw. Attribute definieren die tatsächlichen Daten in der Dimension. Attribute gehören nicht notwendigerweise zu einer Hierarchie, aber Hierarchien werden aus Attributen erstellt. Eine Hierarchie erstellt geordnete Listen von Ebenen und definiert die Arten, wie ein Benutzer die Dimension durchsuchen kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen erhalten Sie weitere Informationen zum Entwerfen und Implementieren von Dimensionsobjekten.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](dimensions-analysis-services-multidimensional-data.md)|In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Dimensionen sind eine wesentliche Komponente von Cubes. Mit Dimensionen werden Daten nach Interessensbereichen geordnet, z. B. nach Kunden, Geschäften oder Angestellten.|  
|[Attribute und Attributhierarchien](attributes-and-attribute-hierarchies.md)|Dimensionen sind Auflistungen von Attributen, die an eine oder mehrere Spalten in einer Tabelle oder Sicht in der Datenquellensicht gebunden sind.|  
|[Attributbeziehungen](attribute-relationships.md)|In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Attributen innerhalb einer Dimension sind immer entweder direkt oder indirekt mit dem Schlüsselattribut verknüpft. Wenn Sie eine Dimension auf Basis eines Sternschemas definieren, in dem sämtliche Dimensionsattribute aus derselben relationalen Tabelle abgeleitet werden, wird automatisch eine Attributbeziehung zwischen dem Schlüsselattribut und den einzelnen Nichtschlüsselattributen definiert. Wenn Sie eine Dimension auf Basis eines Schneeflockenschemas definieren, in dem Dimensionsattribute aus mehreren verknüpften Tabellen abgeleitet werden, wird eine Attributbeziehung automatisch wie folgt definiert:<br /><br /> -Zwischen dem Schlüsselattribut und jedes nichtschlüssel-Attribut, die an Spalten in der Hauptdimensionstabelle gebunden werden.<br />-Zwischen dem Schlüsselattribut und das Attribut für den Fremdschlüssel in der sekundären Tabelle gebunden, die die zugrunde liegenden Dimensionstabellen verknüpft.<br />-Zwischen dem Attribut wird aus der sekundären Tabelle gebunden foreign Key in der sekundären Tabelle und jeder nichtschlüsselattribut an Spalten gebunden.|  
  
  