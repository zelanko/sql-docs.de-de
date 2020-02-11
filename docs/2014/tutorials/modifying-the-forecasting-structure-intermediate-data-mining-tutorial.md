---
title: Ändern der Planungsstruktur (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a86ddf0a715fc3a2313f555e898b3bd94cf66d8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63301303"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Ändern der Planungserstellungsstruktur (Data Mining-Lernprogramm für Fortgeschrittene)
  Die Miningstruktur, die Sie in der vorherigen Aufgabe angelegt haben, umfasst ein Forecasting-Modell. Bevor Sie das Modell verarbeiten und prüfen, müssen Sie noch die Struktur leicht verändern sowie eine der Eigenschaften modifizieren.  
  
## <a name="modifying-the-mining-structure"></a>Ändern der Miningstruktur  
 Die Miningstruktur ändern Sie im Data Mining-Designer auf der Registerkarte **Miningstruktur** . Wenn Sie das Modell mit dem Data Mining-Assistenten erstellt haben, haben Sie drei Spalten verwendet: ReportingDate, ModelRegion und Menge. Die **Vorhersage** Tabelle enthält jedoch auch eine Spalte Amount, mit der Sie die Menge der Verkäufe prognostizieren können. Auf der Registerkarte **Miningstruktur** können Sie diese Spalte aus der Datenquellensicht der Miningstruktur hinzufügen.  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>So fügen Sie der Forecasting-Miningstruktur die Spalte Amount hinzu  
  
1.  Wählen Sie im Data Mining-Designer auf der Registerkarte **Mining Struktur** im Bereich **Datenquellen Sicht** die Spalte Betrag in der Tabelle vTimeSeries aus.  
  
2.  Ziehen Sie die Spalte Betrag aus dem Bereich **Datenquellen Sicht** in die Liste der Spalten für **die Planungs** Struktur.  
  
     Die Amount-Spalte ist nun in der Mining Struktur für die **Vorhersage** enthalten.  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>Ändern der Spalten im Miningmodell  
 Sie haben der Struktur eine neue Spalte hinzugefügt. Jetzt müssen Sie noch angeben, wie die Spalte im Modell verwendet werden soll. Dies legen Sie im Data Mining-Designer auf der Registerkarte **Miningmodelle** fest.  
  
 Auf der Registerkarte **Miningmodelle** werden die Spalten aufgelistet, welche die Miningstruktur in der Spalte **Struktur** des Rasters umfasst. Außerdem werden die Spalten aufgelistet, welche in der Spalte des Miningmodells enthalten sind, die den Namen des Modells trägt; in diesem Fall ist das **Forecasting**. Wenn Sie Änderungen vornehmen möchten, klicken Sie auf die Namen der Spalten. Im Mining Modell für die **Vorhersage** wird die Spalte Amount als Eingabe Spalte verwendet und auch zum Vorhersagen zukünftiger Umsätze verwendet. Deshalb müssen Sie die Eigenschaften für die Spalte so festlegen, dass sie sowohl als Eingabespalte als auch als vorhersagbare Spalte verwendet werden kann.  
  
> [!NOTE]  
>  Auf der Registerkarte **Miningmodelle** können Sie neue Modelle auf der Grundlage derselben Struktur anlegen. Darüber hinaus können Sie den Algorithmus und die Spalteneigenschaften für jedes Modell anpassen. Änderungen treten jedoch erst nach der Verarbeitung des Modells in Kraft.  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>So definieren Sie die Verwendung der Spalte Amount  
  
1.  Klicken Sie in der Spalte **vorher** sagen des Rasters auf der Registerkarte **Mining Modelle** auf die Zelle in der Zeile Amount.  
  
2.  Wählen Sie **Vorhersagen** in der Liste aus.  
  
     Damit ist die Spalte Amount eine Eingabespalte sowie eine vorhersagbare Spalte.  
  
 Sie können auch die Eigenschaften einzelner Spalten ändern, indem Sie die betreffende Spalte auswählen und dann das Fenster **Eigenschaften** öffnen. Zum Öffnen des Fensters **Eigenschaften** klicken Sie mit der rechten Maustaste auf den Namen der Spalte und wählen dann **Eigenschaften**. Wenn Sie für ein einzelnes Modell eine Eigenschaft innerhalb der Spalte ändern, werden die Eigenschaften nur für dieses Modell geändert. Wenn Sie jedoch eine Eigenschaft innerhalb der Spalte **Struktur** ändern, wirkt sich die Änderung auf jedes Modell aus, das mit der Struktur verknüpft ist. Bei jeder Änderung am Modell oder an der Struktur muss eine erneute Verarbeitung durchgeführt werden, um die Auswirkungen anzuzeigen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Anpassen und Verarbeiten des Vorhersagemodells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Mining Modelle &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
