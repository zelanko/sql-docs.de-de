---
title: Beispiel Daten (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb8c0f9424c9e817ee482f426b3045e878a9c9c9
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539062"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a>Beispieldaten (SQL Server Data Mining-Add-Ins)
  ![Assistent zum Partitionieren von Daten (Data Mining-Menüband)](media/dmc-partition.gif "Assistent zum Partitionieren von Daten (Data Mining-Menüband)")  
  
 Der Assistent für **Beispiel Daten** erleichtert das Aufteilen der Quelldaten in zwei Sätze, eine zum entwickeln (trainieren) des Modells und eine zum Testen des Modells. Dieser Assistent bietet auch eine Option für die Entnahme neuer Stichproben von den Daten, um ein neues Dataset zu erstellen, das das Ziel besser wiedergibt.  
  
 Das Erstellen der richtigen Daten zum Trainieren und Testen Ihrer Modelle ist ein wichtiger Bestandteil beim Data Mining. Ohne die richtigen Tools kann diese Aufgabe jedoch mühsam sein. Der Assistent führt eine geschichtete Stichprobe aus, um zu überprüfen, ob die Trainings- und Testsätze gut ausgewogen sind.  
  
## <a name="random-sampling-and-oversampling"></a>Zufällige Stichprobenentnahme und Überquotierung  
 . Die zufällige Stichprobenentnahme ist die beste Möglichkeit, sicherzustellen, dass die zum Testen eines Modells verwendeten Daten ziemlich genau den Daten entsprechen, die Sie zum Erstellen des Modells verwenden. Sie können von Beispieldaten, die in Excel oder einer externen Datenquelle gespeichert sind, zufällige Stichproben entnehmen.  
  
 Wenn Sie die Option für die zufällige Stichprobenentnahme verwenden, erstellt der Assistent für **Beispiel Daten** automatisch Trainings-und Test Datasets und gibt Sie zur späteren Referenz in separaten Excel-Arbeitsblättern aus.  
  
 Wenn Ihre Daten in einer Excel-Arbeitsmappe und nicht in einer externen Datenquelle gespeichert sind, haben Sie auch die Möglichkeit, *über Quotierung*zu verwenden. Mit dieser Option geben Sie einen Zielwert an, der in Ihren Daten knapp ist. Der Assistent sammelt einen ausgewogenen Satz, der mehr an diesem Zielwert enthält. Sie können den Assistenten anweisen, einen gezielten Prozentsatz zu erreichen oder eine bestimmte Anzahl von Zeilen zu erstellen.  
  
 Wenn Sie die Option über Quotierung verwenden, erstellt der Assistent für **Beispiel Daten** ein neues Arbeitsblatt, das die neu ausgeglichenen Beispiel Daten enthält.  
  
## <a name="using-the-sample-data-wizard"></a>Verwenden des Assistenten für Beispieldaten  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a>Trennen von Daten in Trainings- und Testsätze  
  
1.  Klicken Sie im **Data Mining** -Menüband auf **Beispiel Daten**.  
  
2.  Geben Sie auf der Seite **Quelldaten auswählen** an, ob sich die **Daten** , die Sie partitionieren möchten, in einem Excel-Bereich oder einer Excel-Tabelle oder in einer externen Datenquelle befinden.  
  
3.  Geben Sie auf der Seite **Samplings auswählen** an, ob Sie Trainings-und Test Datasets durch zufällige Stichproben Erstellung erstellen möchten, oder erstellen Sie ein neues Dataset durch über Quotierung.  
  
    > [!NOTE]  
    >  Wenn Sie eine externe Datenquelle verwenden, ist nur die Option für die zufällige Stichprobenentnahme verfügbar. Wenn Sie für externe Daten die Überquotierung verwenden möchten, können Sie die Daten über eine Excel-Datenverbindung in eine Excel-Arbeitsmappe importieren und dann den Assistenten für Beispieldaten verwenden.  
  
4.  Legen Sie die Optionen für die ausgewählte Stichprobenmethode fest.  
  
    -   Geben Sie bei der zufälligen Stichprobenentnahme entweder einen Prozentsatz der Originaldaten an, der für Tests verwendet werden soll, oder die Gesamtanzahl von Zeilen für das Testdataset.  
  
    -   Wählen Sie für die Überquotierung die Spalte und den Wert aus, die bzw. den Sie hervorheben möchten. Geben Sie dann die Gesamtanzahl von Zeilen im neuen Dataset sowie den Prozentsatz der Zeilen im neuen Dataset, die den Zielwert enthalten sollen, an.  
  
         Der Zielwert für die Überquotierung muss ein diskreter Wert sein. Sie können für die Überquotierung keine kontinuierlichen numerischen Daten verwenden.  
  
5.  Übernehmen Sie auf der **Seite fertig**stellen die Standardnamen für die neuen Datasets, oder geben Sie einen neuen Namen ein.  
  
     Der Assistent erstellt daraufhin neue Arbeitsblätter für jedes Dataset.  
  
 Die meisten Assistenten des Data Mining-Clients für Excel bieten auch eine Option, mit der die Daten nach dem Zufallsprinzip in Trainings- und Testsätze unterteilt werden können. Wenn Sie jedoch die Assistenten verwenden, bleiben die Daten im gleichen Arbeitsblatt (oder in der gleichen sonstigen Datenquelle). Die Informationen darüber, ob es sich bei einer bestimmten Zeile um einen Test- oder einen Trainingsfall handelt, werden intern gespeichert. Im Gegensatz dazu werden bei Verwendung des Assistenten für **Beispiel Daten** die Test-und Trainingsdaten in separate Arbeitsblätter ausgegeben, um eine einfache Referenz zu erhalten.  
  
## <a name="related-options"></a>Zugehörige Optionen  
 Wenn Sie den Assistenten Schritt für Schritt durchgehen, werden diese Optionen aufgeführt:  
  
|Optionen|Kommentare|  
|-------------|--------------|  
|Quelldaten auswählen (Dialogfeld, Data Mining-Client für Excel)|Wählen Sie einen Excel-Bereich oder eine Excel-Tabelle aus, die die Daten enthalten. Wenn Sie die externen Daten verwenden möchten, können die Daten relational sein, aber sie müssen in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle enthalten sein. T|  
|Stichprobentyp auswählen (Seite, Data Mining-Client für Excel)|Wenn Sie eine externe Datenquelle verwenden, können Sie nur die Option für die zufällige Stichprobenentnahme verwenden. Außerdem müssen Sie die Anzahl der Zeilen angeben, die im endgültigen DataSet erstellt werden sollen, indem Sie die Option **Zeilen Anzahl** verwenden. Sie können keinen Prozentsatz der Quelldaten angeben.|  
|Zufällige Stichprobenentnahme (Seite, Data Mining-Client für Excel)|Sie können einen Prozentsatz von Zeilen (aus den Quelldaten) oder eine bestimmte Anzahl von Zeilen kopieren.|  
|Überquotierung (Seite, Data Mining-Client für Excel)|**Ziel Status**<br /><br /> Wählen Sie einen Wert aus der Liste aus, der im ursprünglichen Dataset unterrepräsentiert ist. Die Überquotierung erhöht den Anteil an Datenzeilen mit diesem Status.<br /><br /> **Stichprobengröße**<br /><br /> Wählen Sie die Gesamtanzahl der zu extrahierenden Zeilen aus. Dieser Wert stellt die Größe des endgültigen Datasets dar.|  
  
## <a name="other-sampling-options"></a>Weitere Optionen für Stichprobenentnahme  
 Wenn die Optionen zur Stichprobenentnahme in diesem Assistenten nicht Ihren Anforderungen entsprechen, verwenden Sie die Transformation zur Stichprobenentnahme von SQL Server Integration Services (SSIS), um Stichproben von Zeilen aus mehreren Datenquellen zu entnehmen.  
  
 Weitere Informationen finden Sie unter Transformation für [Zeilen Stichproben](../integration-services/data-flow/transformations/row-sampling-transformation.md) und Transformation für Prozentwert- [Stichproben](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prüfliste der Vorbereitung für Data Mining](checklist-of-preparation-for-data-mining.md)  
  
  
