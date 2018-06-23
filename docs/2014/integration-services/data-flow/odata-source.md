---
title: OData-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 14e8cb87d04ff0f929fe88c5755087ead58e0c7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159215"
---
# <a name="odata-source"></a>OData-Quelle
  Sie verwenden die OData-Quellkomponente in einem SSIS-Paket, um Daten aus den OData (Open Data Protocol)-Diensten zu nutzen. Die Komponente unterstützt die OData-Protokolle v2 und v3 sowie die ATOM- und JSON-Datenformate.  
  
> [!NOTE]  
>  Die OData-Quelle kann verwendet werden, um Daten aus SharePoint-Listen zu lesen. Um alle Listen auf dem SharePoint Server anzuzeigen, verwenden Sie die folgende URL: http://\<Server > / _vti_bin/ListData.svc. Weitere Informationen zu den URL-Konventionen in SharePoint finden Sie unter [SharePoint Foundation-REST-Schnittstelle](http://msdn.microsoft.com/library/ff521587.aspx).  
  
## <a name="odata-format"></a>OData-Format  
 Die meisten OData-Dienste geben Ergebnisse in verschiedenen Formaten zurück. Sie können das Format des Resultsets mithilfe der $format-Abfrageoption angeben. Formate wie JSON und JSON Light sind effizienter als ATOM/XML und erzielen bei der Übertragung großer Datenmengen möglicherweise eine bessere Leistung. In der folgenden Tabelle sind Ergebnisse aus Beispieltests dargestellt. Wie Sie erkennen können, ergab der Wechsel von ATOM zu JSON einen Leistungszuwachs von 30-53% und der Wechsel von ATOM zum neuen JSON Light-Format (verfügbar in WCF Data Services 5.1) einen Leistungszuwachs von 67 %.  
  
|||||  
|-|-|-|-|  
|Zeilen|ATOM|JSON|JSON (Light)|  
|10000|113 Sekunden|74 Sekunden|68 Sekunden|  
|1000000|1110 Sekunden|853 Sekunden|665 Sekunden|  
  
> [!NOTE]  
>  Die SSIS OData-Quelle verwendet ODataLib 5.5.0 zum Analysieren von OData-Feeds; sie ist in der Lage, alle von dieser Bibliothek unterstützten Formate zu lesen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Installieren und Deinstallieren der OData-Quellkomponente](../install-and-uninstall-odata-source-component.md)  
  
-   [Lernprogramm: Verwenden der OData-Quelle &#91;SSIS&#93;](tutorial-using-the-odata-source.md)  
  
-   [Ändern einer OData-Quellabfrage zur Laufzeit](modify-odata-source-query-at-runtime.md)  
  
-   [Quellen-Editor für OData &#40;Seite „Verbindung“&#41;](../odata-source-editor-connection-page.md)  
  
-   [Quellen-Editor für OData &#40;Seite Spalten&#41;](../odata-source-editor-columns-page.md)  
  
-   [Quellen-Editor für OData &#40;Seite „Fehlerausgabe“&#41;](../odata-source-editor-error-output-page.md)  
  
-   [OData-Quelleneigenschaften](odata-source-properties.md)  
  
## <a name="see-also"></a>Siehe auch  
 [OData-Verbindungs-Manager](../connection-manager/odata-connection-manager.md)  
  
  