---
title: Berichtsdatenbereich
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fc09c100cc8391bb1fd025b4bb5ac5f3b5e4379a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67413135"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a>Berichtsdatenbereich in SQL Server Reporting Services (SSRS)

  Verwenden Sie den Bereich **Berichtsdaten** , um die aktuell definierten Parameter, Datenquellen, Datasets, Feldauflistungen und Bilder in Ihrem Bericht anzuzeigen. Die Berichtsdaten zeigen eine hierarchische Ansicht der Elemente an, die Daten im Bericht darstellen. Die Knoten der obersten Ebene stellen integrierte Felder, Parameter, Bilder und Datenquellenverweise dar. Erweitern Sie jeden Knoten, um die Datenelemente anzuzeigen. Wenn Sie z. B. einen Datenquellenknoten erweitern, werden die für diese Datenquelle definierten Datasets angezeigt. Wenn Sie ein Dataset erweitern, wird seine Feldauflistung angezeigt. Ziehen Sie Elemente in die Berichtsentwurfsoberfläche, um Daten mit Berichtselementen auf der Berichtsseite zu verknüpfen.  
  
## <a name="options"></a>Tastatur

 **Integrierte Felder**  
 Stellt Felder dar, die von Reporting Services bereitgestellt und in einem Bericht häufig verwendet werden, beispielsweise den Berichtsnamen oder Seitennummern. Weitere Informationen finden Sie unter [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Parameter**  
 Stellt die Auflistung der Berichtsparameter dar, von denen jeder einwertig oder mehrwertig sein kann. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)" basiert.  
  
 **Images**  
 Stellt den Bildersatz dar, der im Bericht verwendet wird. Weitere Informationen finden Sie unter [Bilder &#40;Berichts-Generator und SSRS&#41;](../report-design/images-report-builder-and-ssrs.md).  
  
 **Datenquelle**  
 Stellt einen einzelnen Datenquellenverweis auf eine eingebettete Datenquelle oder eine freigegebene Datenquelle dar. In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]werden freigegebene Datenquellen im Projektmappen-Explorer im Ordner Freigegebene Datenquellen angezeigt. Eine Datenquelle gibt einen der Datenquellentypen an, der von Reporting Services unterstützt wird. Eine Datenquelle ist der übergeordnete Knoten für die Auflistung der Datasets, die darauf basieren. Weitere Informationen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) Zeichenfolgen in Reporting Services.  
  
 **Dataset**  
 Stellt ein einzelnes Dataset dar. Ein Dataset ist der übergeordnete Knoten für die Auflistung von Feldern, die durch die Abfrage und bestimmte berechnete Felder angegeben werden. Reporting Services unterstützt Abfrage-Designer, die Ihnen das Angeben einer Abfrage erleichtern. Weitere Informationen finden Sie unter [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md) und [Abfrage Entwurfs Tools in Berichts-Designer SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md).  
  
## <a name="next-steps"></a>Nächste Schritte

 - [Datasetfelder-Sammlung &#40;Berichts-Generator und SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)
 - [Gruppierungsbereich](../tools/grouping-pane.md)