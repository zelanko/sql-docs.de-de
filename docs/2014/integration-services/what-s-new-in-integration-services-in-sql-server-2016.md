---
title: Was&#39;s neue (Integrationsservices) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6eda4eb4f01819bd569a472df01a276c5f270f31
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766093"
---
# <a name="what39s-new-integration-services"></a>Was&#39;s neue (Integrationsservices)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] wurde gegenüber der Vorgängerversion nicht geändert.  
  
 Weitere Informationen zu anderen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Produkten und Technologien finden Sie unter [Neuigkeiten in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Weitere Informationen zu Änderungen in Bezug auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, finden Sie unter [Neuigkeiten in Analysis Services und Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Umfangreiche Ausgabe der XML-Validierung im XML-Task  
 Validieren Sie XML-Dokumente und erhalten Sie eine umfangreiche Fehlerausgabe durch die Aktivierung der Eigenschaft `ValidationDetails` des XML-Tasks. Bevor die Eigenschaft `ValidationDetails` verfügbar war, gab die XML-Validierung durch den XML-Task nur „true“ oder „false“ als Ergebnis zurück, ohne Informationen zu Fehlern oder wo diese auftraten. Wenn Sie jetzt die Eigenschaft `ValidationDetails` auf „true“ festlegen, enthält die Ausgabedatei ausführliche Informationen zu jedem Fehler, einschließlich der Zeilennummer und der Position. Sie können diese Informationen verwenden, um Fehler in XML-Dokumenten zu verstehen, zu finden und zu beheben. Weitere Informationen finden Sie unter [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] führte die Eigenschaft `ValidationDetails` im [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2 ein. Diese neue Eigenschaft wurde zu diesem Zeitpunkt nicht angekündigt oder dokumentiert. Die Eigenschaft `ValidationDetails` ist auch in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und in SQL Server 2016 verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Von den SQL Server 2014-Editionen unterstützte Funktionen](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
