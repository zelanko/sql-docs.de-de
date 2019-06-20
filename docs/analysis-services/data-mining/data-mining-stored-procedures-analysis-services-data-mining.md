---
title: Datamining-gespeicherte Prozeduren (Analysis Services – Datamining) | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2984927575e6dcd3c8d6c530a94061b1dc0b6c17
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65449940"
---
# <a name="data-mining-stored-procedures-analysis-services---data-mining"></a>Data Mining-gespeicherte Prozeduren (Analysis Services - Data Mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]beginnend, unterstützt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeicherte Prozeduren, die in jeder verwalteten Sprache geschrieben werden können. Die unterstützten verwalteten Sprachen umfassen [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, C# und Managed C++. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie die gespeicherten Prozeduren entweder durch Verwendung einer **CALL** -Anweisung oder im Rahmen einer Data Mining Extensions-Abfrage (DMX) direkt aufrufen.  
  
 Weitere Informationen zum Aufrufen von gespeicherten Prozeduren in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] finden Sie unter [Aufrufen von gespeicherten Prozeduren](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md).  
  
 Allgemeine Informationen zu Programmierung, finden Sie unter [Data Mining-Programmierung](../../analysis-services/data-mining/data-mining-programming.md).  
  
 Weitere Informationen über das Programmieren von Data Mining-Objekten finden Sie in dem Artikel "[SQL Server Data Mining Programmability](http://go.microsoft.com/fwlink/?LinkId=93735)" in der MSDN Library.  
  
> [!NOTE]  
>  Wenn Sie Miningmodelle abfragen, insbesondere beim Testen neuer Data Mining-Lösungen, kann es praktisch sein, die gespeicherten Systemprozeduren aufzurufen, die intern von der Data Mining-Engine verwendet werden. Sie können die Namen dieser gespeicherten Systemprozeduren anzeigen, indem Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] eine Ablaufverfolgung auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server erstellen und dann die Data Mining-Modelle erstellen, durchsuchen und abfragen. Jedoch garantiert [!INCLUDE[msCoName](../../includes/msconame-md.md)] nicht die versionsübergreifende Kompatibilität von gespeicherten Systemprozeduren, und Sie sollten Aufrufen von gespeicherten Systemprozeduren niemals in einem Produktionssystem verwenden. Statt dessen sollten Sie im Hinblick auf Kompatibilität eigene Abfragen mit DMX oder XML/A erstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Kreuzvalidierung &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [Übergreifende Überprüfung &#40;Registerkarte, Mininggenauigkeitsdiagramm-Sicht&#41;](http://msdn.microsoft.com/library/bd215a68-1ad7-4046-9c44-ec8e2be13a64)   
 [Aufrufen von gespeicherten Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  
