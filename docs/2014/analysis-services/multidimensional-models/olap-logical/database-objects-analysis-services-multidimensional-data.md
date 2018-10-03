---
title: Datenbankobjekte (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04f490e5b4305b665fc38793439626e3e5f651c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090760"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a>Datenbankobjekte (Analysis Services - Mehrdimensionale Daten)
  Ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz enthält, Datenbankobjekte und Assemblys für die Verwendung mit der analytischen onlineverarbeitung (OLAP) und Datamining.  
  
-   Datenbanken enthalten OLAP- und Data Mining-Objekte, z.&#160;B. Datenquellen, Datenquellensichten, Cubes, Measures, Measuregruppen, Dimensionen, Attribute, Hierarchien, Miningstrukturen, Miningmodelle und Rollen.  
  
-   Assemblys enthalten benutzerdefinierte Funktionen, die die Funktionalität der mit den Sprachen Multidimensional Expressions (MDX) und Data Mining Extensions (DMX) bereitgestellten systeminternen Funktionen erweitern.  
  
 Die <xref:Microsoft.AnalysisServices.Database> Objekt ist der Container für alle Datenobjekte, die für ein Business Intelligence-Projekt (z. B. ein OLAP-Cubes, Dimensionen und Datamining-Strukturen) erforderlich sind, sowie deren Unterstützungsobjekte (z. B. <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account>, und <xref:Microsoft.AnalysisServices.Role>).  
  
 Ein <xref:Microsoft.AnalysisServices.Database>-Objekt bietet u. a. Zugriff auf folgende Objekte und Attribute:  
  
-   Eine Auflistung aller Cubes, auf die Sie Zugriff haben.  
  
-   Eine Auflistung aller Dimensionen, auf die Sie Zugriff haben.  
  
-   Eine Auflistung aller Miningstrukturen, auf die Sie Zugriff haben.  
  
-   Alle Datenquellen und Datenquellensichten in zwei Auflistungen.  
  
-   Alle Rollen und Datenbankberechtigungen in zwei Auflistungen.  
  
-   Der Sortierungswert der Datenbank.  
  
-   Die geschätzte Größe der Datenbank.  
  
-   Der Sprachwert der Datenbank.  
  
-   Die sichtbare Einstellung der Datenbank.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen werden die Objekte beschrieben, die sowohl von OLAP- als auch von Data Mining-Funktionen in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet werden.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Datenquellen in mehrdimensionalen Modellen](../data-sources-in-multidimensional-models.md)|Beschreibt eine Datenquelle in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Datenquellsichten in mehrdimensionalen Modellen](../data-source-views-in-multidimensional-models.md)|Beschreibt ein logisches Datenmodell, das basierend auf eine oder mehrere Datenquellen in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Cubes in mehrdimensionalen Modellen](../cubes-in-multidimensional-models.md)|Beschreibt Cubes und Cubeobjekte, einschließlich Measures, Measuregruppen, Dimensionsverwendungbeziehungen, Berechnungen, Key Performance Indicators (KPIs), Aktionen, Übersetzungen, Partitionen und Perspektiven.|  
|[Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Beschreibt Dimensionen und Dimensionsobjekte, einschließlich Attribute, Attributbeziehungen, Hierarchien, Ebenen und Elemente.|  
|[Miningstrukturen &#40;Analysis Services – Datamining&#41;](../../data-mining/mining-structures-analysis-services-data-mining.md)|Beschreibt Miningstrukturen und Miningobjekte, einschließlich Miningmodellen.|  
|[Sicherheitsrollen &#40;Analysis Services – mehrdimensionale Daten&#41;](security-roles-analysis-services-multidimensional-data.md)|Beschreibt eine Rolle, den Sicherheitsmechanismus, der zum Steuern des Zugriffs auf Objekte in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-model-assemblies-management.md)|Beschreibt eine Assembly, eine Auflistung von benutzerdefinierten Funktionen, die zum Erweitern der Sprachen MDX und DMX in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Datenquellen &#40;SSAS – mehrdimensional&#41;](../supported-data-sources-ssas-multidimensional.md)   
 [Mehrdimensionale Modelllösungen &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md)   
 [Data Mining-Projektmappen](../../data-mining/data-mining-solutions.md)  
  
  
