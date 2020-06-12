---
title: Importieren aus einer mehrdimensionalen Datenquelle (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c062bab47317d121a2b1895742d70c79048413d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544232"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a>Importieren von einer mehrdimensionalen Datenquelle (SSAS – tabellarisch)
  Sie können eine Analysis Services-Cubedatenbank als Datenquelle für ein tabellarisches Modell verwenden. Um Daten aus einem Analysis Services-Cube zu importieren, müssen Sie eine MDX-Abfrage zur Auswahl der zu importierenden Daten definieren.  
  
 Alle Daten, die in einer SQL Server Analysis Services-Datenbank enthalten sind, können in ein Modell importiert werden. Sie können die gesamte oder einen Teil einer Dimension extrahieren oder Slices und Aggregate aus dem Cube abrufen, z. B. die Summe der monatlichen Verkäufe für das aktuelle Jahr usw. Beachten Sie jedoch, dass alle Daten, die Sie aus einem Cube importieren, vereinfacht werden. Wenn Sie eine Abfrage definieren, die Measures aus mehreren Dimensionen abruft, werden die Daten daher für jede Dimension in eine separate Spalte importiert.  
  
 Analysis Services-Cubes müssen die Version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]oder [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]aufweisen.  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a>So importieren Sie Daten aus einem Analysis Services-Cube  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf das Menü **Modell** und dann auf **Aus Datenquelle importieren**.  
  
2.  Wählen Sie auf der Seite **Mit einer Datenquelle verbinden** die Option **Microsoft Analysis Services**aus, und klicken Sie dann auf **Weiter**.  
  
3.  Führen Sie die Schritte im Tabellenimport-Assistenten aus. Auf der Seite **MDX-Abfrage angeben** können Sie eine MDX-Abfrage angeben. Zur Verwendung des MDX-Abfrage-Designers klicken Sie auf der Seite **MDX-Abfrage angeben**auf Entwurf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Importieren von Daten &#40;tabellarischen SSAS-&#41;](import-data-ssas-tabular.md)   
 [Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
