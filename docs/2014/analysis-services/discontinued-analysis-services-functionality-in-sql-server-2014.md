---
title: Nicht mehr unterstützte Analysis Services-Funktionalität in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 616c39d03ff8081c209a80dcca912d831bcef1ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081677"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a>Nicht mehr unterstützte Analysis Services-Funktionalität in SQL Server 2014
  In diesem Thema werden die Funktionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]nicht mehr verfügbar sind.  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Nicht mehr unterstützte Funktionen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
  
|Kategorie|Als veraltet markierte Funktion|Ersatz|  
|--------------|------------------------|-----------------|  
|Lokale Cubes|InsertInto (Verbindungszeichenfolgen-Eigenschaft)|Ursprüngliche Verbindungszeichenfolgensyntax zum Auffüllen lokaler Cubes wird durch die Anweisung zum Erstellen globaler Cubes ersetzt. Weitere Informationen finden Sie unter [globalen CUBE-Anweisung CREATE &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).|  
|Lokale Cubes|CreateCube (Verbindungszeichenfolgen-Eigenschaft)|Ursprüngliche Verbindungszeichenfolgensyntax zum Auffüllen lokaler Cubes wird durch die Anweisung zum Erstellen globaler Cubes ersetzt. Weitere Informationen finden Sie unter [globalen CUBE-Anweisung CREATE &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).|  
|Data Mining|SQL Server 2000 PMML|Die PMML-Funktion von SQL Server 2000 hat eine Form von PMML mit proprietären Erweiterungen erstellt, um von Data Mining-Algorithmen bereitgestellte eindeutige Funktionen zu unterstützen, die in der PMML-Spezifikation nicht verfügbar waren. In SQL Server 2005 wurde durch Analysis Services die PMML-Funktion auf den neueren PMML 2.1-Standard aktualisiert. Als Ergebnis werden die in SQL Server 2000 hinzugefügten proprietären Erweiterungen nicht mehr benötigt, obwohl sie in dieser Version noch unterstützt werden.|  
|MDX-Anweisung|CREATE ACTION-Anweisung|Diese Anweisung wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. Sie wird vom Action-Objekt ersetzt. Weitere Informationen zum Erstellen von Aktionen in früheren Versionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], finden Sie unter [Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).|  
  
## <a name="discontinued-features-in-previous-releases"></a>Nicht mehr unterstützte Funktionen in früheren Versionen  
 Der für die Migration von SQL Server 2000 Analysis Services-Datenbanken zu neueren Versionen verwendete Migrations-Assistent wird nicht mehr unterstützt, da SQL Server 2000 nicht mehr unterstützt wird.  
  
 Die DSO-Bibliothek (Decision Support Objects) für die Kompatibilität mit SQL Server 2000 Analysis Services-Datenbanken wird ebenfalls nicht mehr unterstützt und ist nicht mehr Teil von SQL Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Backward Compatibility](analysis-services-backward-compatibility.md)  
  
  
