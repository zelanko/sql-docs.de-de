---
title: Erweitern von OLAP durch personalisierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf7785c3acd3815f78e656951e8ae3f05e125245
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280356"
---
# <a name="extending-olap-through-personalizations"></a>Erweitern von OLAP durch Personalisierungen
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] stellt viele systeminterne Funktionen bereit, die mit den Sprachen Multidimensional Expressions (MDX) und Data Mining Extensions (DMX) verwendet werden können. Diese Funktionen sind ebenso für herkömmliche statistische Berechnungen wie zum Durchlaufenden der Elemente einer Hierarchie geeignet. Wie bei jedem anderen komplexen und robusten Produkt, ist es jedoch immer die Notwendigkeit, die die Funktionalität des Produkts zu erweitern.  
  
 Deshalb können Sie einer Instanz des Diensts mithilfe der Analysis Services Assemblys und Personalisierungserweiterungen hinzufügen, um die Geschäftsanforderungen zu erfüllen, wenn die Standardfunktionalität einmal nicht ausreichen sollte.  
  
## <a name="assemblies"></a>Assemblys  
 Assemblys können Sie die Geschäftsfunktionalität von MDX und DMX erweitern. Sie integrieren die gewünschte Funktionalität in eine Bibliothek, z. B. eine DLL (Dynamic Link Library), und fügen dann die Bibliothek als Assembly einer Instanz von Analysis Services oder einer Analysis Services-Datenbank hinzu. Die öffentlichen Methoden in der Bibliothek werden dann als benutzerdefinierte Funktionen für MDX- und DMX-Ausdrücke, Prozeduren, Berechnungen, Aktionen und Clientanwendungen verfügbar gemacht.  
  
## <a name="personalized-extensions"></a>Personalisierungserweiterungen  
 SQL Server Analysis Services-Personalisierungserweiterungen sind die Grundlage für das Konzept der Implementierung einer Plug-In-Architektur. Analysis Services-Personalisierungserweiterungen stellen eine einfache und elegante Modifikation der vorhandenen Architektur der verwalteten Assembly dar. Sie werden im Analysis Services-<xref:Microsoft.AnalysisServices.AdomdServer>-Objektmodell, in der MDX-Syntax (Multidimensional Expressions) und in den Schemarowsets zur Verfügung gestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-model-assemblies-management.md)   
 [Personalisierungserweiterungen für Analysis Services](analysis-services-personalization-extensions.md)  
  
  
