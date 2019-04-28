---
title: Berichtsdatenbereich
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services-2014, sql-server-2014
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 1ea9335986fa58159bd7bb71fc7d32ac7f655feb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62721438"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a>Berichtsdatenbereich in SQL Server Reporting Services (SSRS)

  Verwenden Sie den Bereich **Berichtsdaten** , um die aktuell definierten Parameter, Datenquellen, Datasets, Feldauflistungen und Bilder in Ihrem Bericht anzuzeigen. Die Berichtsdaten zeigen eine hierarchische Ansicht der Elemente an, die Daten im Bericht darstellen. Die Knoten der obersten Ebene stellen integrierte Felder, Parameter, Bilder und Datenquellenverweise dar. Erweitern Sie jeden Knoten, um die Datenelemente anzuzeigen. Wenn Sie z. B. einen Datenquellenknoten erweitern, werden die für diese Datenquelle definierten Datasets angezeigt. Wenn Sie ein Dataset erweitern, wird seine Feldauflistung angezeigt. Ziehen Sie Elemente in die Berichtsentwurfsoberfläche, um Daten mit Berichtselementen auf der Berichtsseite zu verknüpfen.  
  
## <a name="options"></a>Optionen

 **Integrierte Felder**  
 Stellt Felder dar, die von Reporting Services bereitgestellt und in einem Bericht häufig verwendet werden, beispielsweise den Berichtsnamen oder Seitennummern. Weitere Informationen finden Sie unter [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Parameter**  
 Stellt die Auflistung der Berichtsparameter dar, von denen jeder einwertig oder mehrwertig sein kann. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)" basiert.  
  
 **Bilder**  
 Stellt den Bildersatz dar, der im Bericht verwendet wird. Weitere Informationen finden Sie unter [Bilder &#40;Berichts-Generator und SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).  
  
 **Datenquelle**  
 Stellt einen einzelnen Datenquellenverweis auf eine eingebettete Datenquelle oder eine freigegebene Datenquelle dar. In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]werden freigegebene Datenquellen im Projektmappen-Explorer im Ordner Freigegebene Datenquellen angezeigt. Eine Datenquelle gibt einen der Datenquellentypen an, der von Reporting Services unterstützt wird. Eine Datenquelle ist der übergeordnete Knoten für die Auflistung der Datasets, die darauf basieren. Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) .  
  
 **Dataset**  
 Stellt ein einzelnes Dataset dar. Ein Dataset ist der übergeordnete Knoten für die Auflistung von Feldern, die durch die Abfrage und bestimmte berechnete Felder angegeben werden. Reporting Services unterstützt Abfrage-Designer, die Ihnen das Angeben einer Abfrage erleichtern. Weitere Informationen finden Sie unter [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41; ](report-datasets-ssrs.md) und [Abfrageentwurfstools im Berichts-Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).  
  
## <a name="next-steps"></a>Nächste Schritte

 - [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)
 - [Gruppierungsbereich](../tools/grouping-pane.md)