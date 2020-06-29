---
title: Erweitern von OLAP durch Personalisierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93669980e989b1cb11673f45c111de3609bbe920
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468945"
---
# <a name="extending-olap-through-personalizations"></a>Erweitern von OLAP durch Personalisierungen
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] stellt viele systeminterne Funktionen bereit, die mit den Sprachen Multidimensional Expressions (MDX) und Data Mining Extensions (DMX) verwendet werden können. Diese Funktionen sind ebenso für herkömmliche statistische Berechnungen wie zum Durchlaufenden der Elemente einer Hierarchie geeignet. Wie bei jedem anderen komplexen und robusten Produkt besteht jedoch immer die Notwendigkeit, die Funktionalität eines solchen Produkts weiter zu erweitern.  
  
 Deshalb können Sie einer Instanz des Diensts mithilfe der Analysis Services Assemblys und Personalisierungserweiterungen hinzufügen, um die Geschäftsanforderungen zu erfüllen, wenn die Standardfunktionalität einmal nicht ausreichen sollte.  
  
## <a name="assemblies"></a>Assemblys  
 Mit Assemblys können Sie die Geschäfts Funktionalität von MDX und DMX erweitern. Sie integrieren die gewünschte Funktionalität in eine Bibliothek, z. B. eine DLL (Dynamic Link Library), und fügen dann die Bibliothek als Assembly einer Instanz von Analysis Services oder einer Analysis Services-Datenbank hinzu. Die öffentlichen Methoden in der Bibliothek werden dann als benutzerdefinierte Funktionen für MDX- und DMX-Ausdrücke, Prozeduren, Berechnungen, Aktionen und Clientanwendungen verfügbar gemacht.  
  
## <a name="personalized-extensions"></a>Personalisierte Erweiterungen  
 SQL Server Analysis Services-Personalisierungserweiterungen sind die Grundlage für das Konzept der Implementierung einer Plug-In-Architektur. Analysis Services Personalisierungs Erweiterungen sind eine einfache und elegante Änderung der vorhandenen Architektur der verwalteten Assembly und werden im Analysis Services [Microsoft. AnalysisServices. AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) -Objektmodell, in der MDX-Syntax (Multidimensional Expressions) und in Schemarowsets verfügbar gemacht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellen](../multidimensional-model-assemblies-management.md)   
 [Personalisierungserweiterungen für Analysis Services](analysis-services-personalization-extensions.md)  
  
  
