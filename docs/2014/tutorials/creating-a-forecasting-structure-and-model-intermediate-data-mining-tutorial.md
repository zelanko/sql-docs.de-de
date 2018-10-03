---
title: Erstellen einer Planungserstellungsstruktur und eines Modells (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f762b6c561f96f8ced9f8fe977dceb3b9208d01
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048520"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a>Erstellen einer Struktur und eines Modells zur Planungserstellung (Data Mining-Lernprogramm für Fortgeschrittene)
  Als Nächstes erstellen Sie mit dem Data Mining-Assistenten eine neue Miningstruktur und eine neues Miningmodell, basierend auf der zuvor erstellten Datenquellensicht. In dieser Aufgabe legen Sie fest, dass das Miningmodell den [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmus Zeitreihe verwenden soll.  
  
### <a name="to-create-a-forecasting-mining-structure"></a>So legen Sie eine Forecasting-Miningstruktur an  
  
1.  Im Projektmappen-Explorer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur**.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** überprüfen Sie, ob Seite **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Erstellen von Data Mining-Struktur** Seite **welche Datamining-Technik möchten Sie verwenden?** Option **Microsoft Time Series**, und klicken Sie dann auf  **Nächste**.  
  
5.  Auf der **Datenquellensicht auswählen** Seite **verfügbare Datenquellensichten**Option **SalesByRegion**.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Auf der **Tabellentypen angeben** Seite, stellen Sie sicher, dass das Kontrollkästchen in der **Fall** Spalte für die vTimeSeries-Tabelle ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
8.  Auf der **Trainingsdaten angeben** Seite, wählen Sie die Kontrollkästchen in der **Schlüssel** für die ModelRegion und ReportingDate-Spalten.  
  
     ReportingDate muss in der Standardeinstellung ausgewählt werden, da Sie diese Spalte als logischen primären Schlüssel angegeben, wenn Sie die Datenquellensicht erstellt haben. ModelRegion als sekundären Schlüssel hinzufügen, weisen Sie den Algorithmus eine separate Zeitreihe für jede Kombination aus Modell und Region, die in diesem Feld aufgelistete zu erstellen.  
  
9. Wählen Sie die Kontrollkästchen in der **Eingabe** und **vorhersagbar** Spalten für die Menge, Spalte, und klicken Sie dann auf **Weiter**.  
  
     Durch Auswahl **vorhersagbar**, Sie angeben, dass Sie Vorhersagen für die Daten in diesem Artikel erstellen möchten. Da Sie jedoch die Prognose anhand von vergangenen Daten erstellen möchten, müssen Sie die Spalte auch als Eingabe hinzufügen.  
  
10. Auf der Seite **Inhalt und Datentyp der Spalten angeben**, überprüfen Sie die Auswahl.  
  
     Die ModelRegion-Spalte festgelegt wurde, als eine **Schlüssel** Spalte und die ReportingDate-Spalte wird automatisch festgelegt, als eine **Key Time** Spalte. Es kann von jedem Schlüsseltyp nur jeweils einer vorhanden sein.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Auf der **Abschließen des Assistenten** Seite für **Miningstrukturname**, Typ `Forecasting`.  
  
    > [!NOTE]  
    >  Die Option zum Aktivieren von Drillthroughs ist für Zeitreihenmodelle nicht verfügbar.  
  
13. In **Miningmodellname**, Typ `Forecasting`, und klicken Sie dann auf **Fertig stellen**.  
  
     Data Mining-Designer wird geöffnet und zeigt die `Forecasting` Miningstruktur, die Sie gerade erstellt haben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Ändern der Planungserstellungsstruktur &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
