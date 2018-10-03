---
title: Ändern der Planungserstellungsstruktur (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 559f6aa6b31b8998703a93e84dc100ce375cbda8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139530"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Ändern der Planungserstellungsstruktur (Data Mining-Lernprogramm für Fortgeschrittene)
  Die Miningstruktur, die Sie in der vorherigen Aufgabe angelegt haben, umfasst ein Forecasting-Modell. Bevor Sie das Modell verarbeiten und prüfen, müssen Sie noch die Struktur leicht verändern sowie eine der Eigenschaften modifizieren.  
  
## <a name="modifying-the-mining-structure"></a>Ändern der Miningstruktur  
 Die Miningstruktur ändern Sie im Data Mining-Designer auf der Registerkarte **Miningstruktur** . Wenn Sie das Modell mit dem Data Mining-Assistenten erstellt haben, werden drei Spalten verwendet: ReportingDate, ModelRegion und Menge. Allerdings die **Forecasting** Tabelle enthält auch eine Mengenspalte, die Sie auf die Vorhersage der Umsatzbeträge verwenden können. Auf der Registerkarte **Miningstruktur** können Sie diese Spalte aus der Datenquellensicht der Miningstruktur hinzufügen.  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>So fügen Sie der Forecasting-Miningstruktur die Spalte Amount hinzu  
  
1.  Auf der **Miningstruktur** -Registerkarte des Data Mining-Designers in der **Datenquellensicht** Bereich, wählen Sie die Spalte "Amount" in die vTimeSeries-Tabelle.  
  
2.  Ziehen Sie die Menge-Spalte aus der **Datenquellensicht** Bereich in der Liste der Spalten für die **Forecasting** Struktur.  
  
     Die Spalte "Amount" befindet sich jetzt der **Forecasting** Mining-Struktur.  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>Ändern der Spalten im Miningmodell  
 Sie haben der Struktur eine neue Spalte hinzugefügt. Jetzt müssen Sie noch angeben, wie die Spalte im Modell verwendet werden soll. Dies legen Sie im Data Mining-Designer auf der Registerkarte **Miningmodelle** fest.  
  
 Auf der Registerkarte **Miningmodelle** werden die Spalten aufgelistet, welche die Miningstruktur in der Spalte **Struktur** des Rasters umfasst. Außerdem werden die Spalten aufgelistet, welche in der Spalte des Miningmodells enthalten sind, die den Namen des Modells trägt; in diesem Fall ist das **Forecasting**. Wenn Sie Änderungen vornehmen möchten, klicken Sie auf die Namen der Spalten. In der **Forecasting** Miningmodell der Spalte "Amount" wird als eine Eingabespalte verwendet und wird auch zur Vorhersage zukünftiger Umsätze verwendet. Deshalb müssen Sie die Eigenschaften für die Spalte so festlegen, dass sie sowohl als Eingabespalte als auch als vorhersagbare Spalte verwendet werden kann.  
  
> [!NOTE]  
>  Auf der Registerkarte **Miningmodelle** können Sie neue Modelle auf der Grundlage derselben Struktur anlegen. Darüber hinaus können Sie den Algorithmus und die Spalteneigenschaften für jedes Modell anpassen. Änderungen treten jedoch erst nach der Verarbeitung des Modells in Kraft.  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>So definieren Sie die Verwendung der Spalte Amount  
  
1.  In der **Forecasting** Spalte des Rasters auf die **Miningmodelle** Registerkarte, klicken Sie auf die Zelle in der Menge Zeile.  
  
2.  Wählen Sie **Vorhersagen** in der Liste aus.  
  
     Die Spalte "Amount" ist jetzt eine Eingabespalte sowie eine vorhersagbare Spalte.  
  
 Sie können auch die Eigenschaften einzelner Spalten ändern, indem Sie die betreffende Spalte auswählen und dann das Fenster **Eigenschaften** öffnen. Zum Öffnen des Fensters **Eigenschaften** klicken Sie mit der rechten Maustaste auf den Namen der Spalte und wählen dann **Eigenschaften**. Wenn Sie für ein einzelnes Modell eine Eigenschaft innerhalb der Spalte ändern, werden die Eigenschaften nur für dieses Modell geändert. Wenn Sie jedoch eine Eigenschaft innerhalb der Spalte **Struktur** ändern, wirkt sich die Änderung auf jedes Modell aus, das mit der Struktur verknüpft ist. Bei jeder Änderung am Modell oder an der Struktur muss eine erneute Verarbeitung durchgeführt werden, um die Auswirkungen anzuzeigen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Anpassen und Verarbeiten des Forecasting-Modells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Miningstrukturen &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Miningmodelle &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
