---
title: Berichtsdaten Bereich (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a77024e62402cea0a37b945e0539274fee9a3c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78173329"
---
# <a name="report-data-pane-report-builder"></a>Berichtsdatenbereich (Berichts-Generator)
  Verwenden Sie den Bereich **Berichtsdaten** , um die aktuell definierten Parameter, Datenquellen, Datasets, Feldauflistungen und Bilder in Ihrem Bericht anzuzeigen. Die Berichtsdaten zeigen eine hierarchische Ansicht der Elemente an, die Daten im Bericht darstellen. Die Knoten der obersten Ebene stellen integrierte Felder, Parameter, Bilder und Datenquellenverweise dar. Erweitern Sie jeden Knoten, um die Datenelemente anzuzeigen. Wenn Sie z. B. einen Datenquellenknoten erweitern, werden die für diese Datenquelle definierten Datasets angezeigt. Wenn Sie ein Dataset erweitern, wird seine Feldauflistung angezeigt. Ziehen Sie Elemente in die Berichtsoberfläche oder den Gruppierungsbereich, um Daten mit den gewählten Berichtselementen auf der Berichtsseite zu verknüpfen. Weitere Informationen finden Sie unter [Berichtsentwurfsansicht (Berichts-Generator)](report-builder/report-design-view-report-builder.md).

## <a name="options"></a>Optionen
 **Integrierte Felder** Stellt häufig verwendete Felder in einem Bericht dar, z. b. der Berichts Name oder die Seitenzahl. Weitere Informationen finden Sie unter [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md).

 **Parameter** Stellt die Auflistung von Berichts Parametern dar, von denen jeder einwertig oder mehr wertig sein kann. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)" basiert.

 **Bilder** Stellt den Bildersatz dar, der im Bericht verwendet wird. Weitere Informationen finden Sie unter [Bilder &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md).

 **Datenquellen** Stellt eine eingebettete Datenquelle oder einen Verweis auf eine freigegebene Datenquelle dar. Eine Datenquelle stellt die Quelle für die Daten des Berichts dar. Eine Datenquelle ist der übergeordnete Knoten für die Auflistung der Datasets, die sie verwenden. Weitere Informationen finden Sie unter [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md) und [Datenverbindungen, Datenquellen und Verbindungs](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)Zeichenfolgen in Berichts-Generator.

 **DataSets** Stellt die Daten dar, die aus einer Datenquelle abgerufen werden, indem ein Befehl ausgeführt wird, [!INCLUDE[tsql](../includes/tsql-md.md)] z. b. eine Abfrage, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Daten aus einer Datenbank abruft. Ein Dataset ist der übergeordnete Knoten für die Auflistung von Feldern, die von der Abfrage angegeben werden. Es umfasst auch berechnete Felder. Berichts-Generator unterstützt Abfrage-Designer, die Ihnen das Angeben einer Abfrage erleichtern. Weitere Informationen finden Sie unter [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md).

## <a name="see-also"></a>Weitere Informationen
 Die [Datasetfeldauflistung &#40;Berichts-Generator und SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) zum Gruppieren von Bereichen [&#40;](report-design/grouping-pane-report-builder.md) Berichts-Generator&#41;&#40;Berichts-Generator [und SSRS](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) &#41;


