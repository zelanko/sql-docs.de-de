---
title: Beispieldaten (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
manager: craigg
ms.openlocfilehash: 72579d679b0ced1fd3c260098bc68237f2980a3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209890"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a>Beispieldaten (SQL Server Data Mining-Add-Ins)
  ![Partition--Assistenten im Data Mining-Menüband](media/dmc-partition.gif "Partitionieren von Daten-Assistenten im Data Mining-Menüband")  
  
 Die **Beispieldaten** Assistent erleichtert Ihnen die Quelldaten in zwei Gruppen, eine zum Erstellen (Schulung) zu unterteilen. das Modell und eine zum Testen des Modells. Dieser Assistent bietet auch eine Option für die Entnahme neuer Stichproben von den Daten, um ein neues Dataset zu erstellen, das das Ziel besser wiedergibt.  
  
 Das Erstellen der richtigen Daten zum Trainieren und Testen Ihrer Modelle ist ein wichtiger Bestandteil beim Data Mining. Ohne die richtigen Tools kann diese Aufgabe jedoch mühsam sein. Der Assistent führt eine geschichtete Stichprobe aus, um zu überprüfen, ob die Trainings- und Testsätze gut ausgewogen sind.  
  
## <a name="random-sampling-and-oversampling"></a>Zufällige Stichprobenentnahme und Überquotierung  
 . Die zufällige Stichprobenentnahme ist die beste Möglichkeit, sicherzustellen, dass die zum Testen eines Modells verwendeten Daten ziemlich genau den Daten entsprechen, die Sie zum Erstellen des Modells verwenden. Sie können von Beispieldaten, die in Excel oder einer externen Datenquelle gespeichert sind, zufällige Stichproben entnehmen.  
  
 Wenn Sie die Option zur zufälligen Stichprobenentnahme verwenden die **Beispieldaten** Assistenten automatisch erstellt Trainings-und testdatasets und gibt sie in einem getrennten Excel-Arbeitsblatt zur späteren Bezugnahme.  
  
 Wenn Ihre Daten in einer Excel-Arbeitsmappe und nicht mit einer externen Datenquelle gespeichert ist, haben Sie auch die Möglichkeit, verwenden Sie *überquotierung*. Mit dieser Option geben Sie einen Zielwert an, der in Ihren Daten knapp ist. Der Assistent sammelt einen ausgewogenen Satz, der mehr an diesem Zielwert enthält. Sie können den Assistenten anweisen, einen gezielten Prozentsatz zu erreichen oder eine bestimmte Anzahl von Zeilen zu erstellen.  
  
 Wenn Sie die Option zur überquotierung verwenden die **Beispieldaten** -Assistent erstellt ein neues Arbeitsblatt, das die neu ausgeglichenen Beispieldaten enthält.  
  
## <a name="using-the-sample-data-wizard"></a>Verwenden des Assistenten für Beispieldaten  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a>Trennen von Daten in Trainings- und Testsätze  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **Beispieldaten**.  
  
2.  Auf der **Quelldaten auswählen** Seite, ob die **Daten** ist, dass Sie partitionieren möchten, in eine Excel-Bereich oder eine Tabelle oder in einer externen Datenquelle.  
  
3.  Auf der **Stichprobentyp auswählen** an, ob Sie zum Erstellen von Trainings- und testdatasets durch zufällige Stichprobenentnahme oder überquotierung ein neues Dataset erstellen möchten.  
  
    > [!NOTE]  
    >  Wenn Sie eine externe Datenquelle verwenden, ist nur die Option für die zufällige Stichprobenentnahme verfügbar. Wenn Sie für externe Daten die Überquotierung verwenden möchten, können Sie die Daten über eine Excel-Datenverbindung in eine Excel-Arbeitsmappe importieren und dann den Assistenten für Beispieldaten verwenden.  
  
4.  Legen Sie die Optionen für die ausgewählte Stichprobenmethode fest.  
  
    -   Geben Sie bei der zufälligen Stichprobenentnahme entweder einen Prozentsatz der Originaldaten an, der für Tests verwendet werden soll, oder die Gesamtanzahl von Zeilen für das Testdataset.  
  
    -   Wählen Sie für die Überquotierung die Spalte und den Wert aus, die bzw. den Sie hervorheben möchten. Geben Sie dann die Gesamtanzahl von Zeilen im neuen Dataset sowie den Prozentsatz der Zeilen im neuen Dataset, die den Zielwert enthalten sollen, an.  
  
         Der Zielwert für die Überquotierung muss ein diskreter Wert sein. Sie können für die Überquotierung keine kontinuierlichen numerischen Daten verwenden.  
  
5.  Auf der **Abschlussseite**, akzeptieren Sie die Standardnamen für die neuen Datasets oder einen neuen Namen eingeben.  
  
     Der Assistent erstellt daraufhin neue Arbeitsblätter für jedes Dataset.  
  
 Die meisten Assistenten des Data Mining-Clients für Excel bieten auch eine Option, mit der die Daten nach dem Zufallsprinzip in Trainings- und Testsätze unterteilt werden können. Wenn Sie jedoch die Assistenten verwenden, bleiben die Daten im gleichen Arbeitsblatt (oder in der gleichen sonstigen Datenquelle). Die Informationen darüber, ob es sich bei einer bestimmten Zeile um einen Test- oder einen Trainingsfall handelt, werden intern gespeichert. Im Gegensatz dazu bei Verwendung der **Beispieldaten** -Assistenten, die Tests und Trainingsdaten in gesonderte Arbeitsblätter können leicht eingesehen ausgegeben werden.  
  
## <a name="related-options"></a>Zugehörige Optionen  
 Wenn Sie den Assistenten Schritt für Schritt durchgehen, werden diese Optionen aufgeführt:  
  
|Tastatur|Kommentare|  
|-------------|--------------|  
|Quelldaten auswählen (Dialogfeld, Data Mining-Client für Excel)|Wählen Sie einen Excel-Bereich oder eine Excel-Tabelle aus, die die Daten enthalten. Wenn Sie die externen Daten verwenden möchten, können die Daten relational sein, aber sie müssen in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle enthalten sein. T|  
|Stichprobentyp auswählen (Seite, Data Mining-Client für Excel)|Wenn Sie eine externe Datenquelle verwenden, können Sie nur die Option für die zufällige Stichprobenentnahme verwenden. Sie müssen außerdem angeben, die Anzahl der Zeilen in der endgültigen Dataset erstellen, indem die **Zeilenanzahl** Option. Sie können keinen Prozentsatz der Quelldaten angeben.|  
|Zufällige Stichprobenentnahme (Seite, Data Mining-Client für Excel)|Sie können einen Prozentsatz von Zeilen (aus den Quelldaten) oder eine bestimmte Anzahl von Zeilen kopieren.|  
|Überquotierung (Seite, Data Mining-Client für Excel)|**Zielstatus**<br /><br /> Wählen Sie einen Wert aus der Liste aus, der im ursprünglichen Dataset unterrepräsentiert ist. Die Überquotierung erhöht den Anteil an Datenzeilen mit diesem Status.<br /><br /> **Stichprobengröße**<br /><br /> Wählen Sie die Gesamtanzahl der zu extrahierenden Zeilen aus. Dieser Wert stellt die Größe des endgültigen Datasets dar.|  
  
## <a name="other-sampling-options"></a>Weitere Optionen für Stichprobenentnahme  
 Wenn die Optionen zur Stichprobenentnahme in diesem Assistenten nicht Ihren Anforderungen entsprechen, verwenden Sie die Transformation zur Stichprobenentnahme von SQL Server Integration Services (SSIS), um Stichproben von Zeilen aus mehreren Datenquellen zu entnehmen.  
  
 Weitere Informationen finden Sie unter [Transformation für Zeilenstichproben](../integration-services/data-flow/transformations/row-sampling-transformation.md) und [Percentage Sampling Transformation](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste der Vorbereitung für Data Mining](checklist-of-preparation-for-data-mining.md)  
  
  
