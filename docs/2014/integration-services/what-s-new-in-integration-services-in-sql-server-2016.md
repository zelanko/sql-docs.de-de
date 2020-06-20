---
title: Neuerungen&#39;s (Integration Services) | Microsoft-Dokumentation
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
ms.openlocfilehash: 1d17451c8706722b0dac21d777f35a17fe319799
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972470"
---
# <a name="what39s-new-integration-services"></a>Neues&#39;s (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]ist gegenüber der vorherigen Version unverändert.  
  
 Weitere Informationen zu anderen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Produkten und Technologien finden Sie unter [What es New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Weitere Informationen zu Änderungen im Zusammenhang mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence finden Sie unter [Neues in Analysis Services und Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services).  
  
##  <a name="rich-xml-validation-output-in-the-xml-task"></a><a name="ValidateXML"></a> Umfangreiche Ausgabe der XML-Validierung im XML-Task  
 Validieren Sie XML-Dokumente und erhalten Sie eine umfangreiche Fehlerausgabe durch die Aktivierung der Eigenschaft `ValidationDetails` des XML-Tasks. Bevor die Eigenschaft `ValidationDetails` verfügbar war, gab die XML-Validierung durch den XML-Task nur „true“ oder „false“ als Ergebnis zurück, ohne Informationen zu Fehlern oder wo diese auftraten. Wenn Sie jetzt die Eigenschaft `ValidationDetails` auf „true“ festlegen, enthält die Ausgabedatei ausführliche Informationen zu jedem Fehler, einschließlich der Zeilennummer und der Position. Sie können diese Informationen verwenden, um Fehler in XML-Dokumenten zu verstehen, zu finden und zu beheben. Weitere Informationen finden Sie unter [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] führte die Eigenschaft `ValidationDetails` im [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2 ein. Diese neue Eigenschaft wurde zu diesem Zeitpunkt nicht angekündigt oder dokumentiert. Die Eigenschaft `ValidationDetails` ist auch in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und in SQL Server 2016 verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von den Editionen von SQL Server 2014 unterstützte Features](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
