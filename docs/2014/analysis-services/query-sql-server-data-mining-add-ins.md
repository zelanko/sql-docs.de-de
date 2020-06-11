---
title: Abfrage (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d0f0212795adcaed220806f8cc1349f95c2a6f3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539572"
---
# <a name="query-sql-server-data-mining-add-ins"></a>Abfrage (SQL Server Data Mining-Add-Ins)
  ![Abfragemodell (Schaltfläche auf Data Mining-Menüband)](media/dmc-query.gif "Abfragemodell (Schaltfläche auf Data Mining-Menüband)")  
  
 Der **Abfrage** -Assistent unterstützt Sie bei der Interaktion mit vorhandenen Mining Modellen, um Vorhersagen auf Grundlage von Daten in einer Excel-Tabelle, einem Excel-Bereich oder einer anderen Datenquelle zu treffen. Der Prozess der Anwendung neuer Daten auf ein vorhandenes Modell, um Trends vorherzusagen, wird als *Vorhersage Abfrage*bezeichnet.  
  
 Der **Abfrage** -Assistent bietet auch einen erweiterten Editor zum Erstellen oder Ändern von Data Mining Modellen, zum Erstellen von benutzerdefinierten Abfragen oder zum Arbeiten mit Strukturen, die in anderen Tools nicht unterstützt werden, z. b. in Form von geclusterte Datasets.  
  
-   Verwenden Sie den Text-Editor, um die DMX-Anweisungen (Data Mining Extensions) einzugeben oder einzufügen, die Sie an anderer Stelle erstellt haben.  
  
-   Verwenden Sie den interaktiven Abfrage-Generator, um eine benutzerdefinierte DMX-Anweisung mithilfe von Vorlagen und Dialogfeldern zusammenzustellen.  
  
-   Erstellen Sie DMX-Anweisungen zum Verwalten oder Sichern von Miningmodellen und -strukturen.  
  
## <a name="using-the-query-wizard"></a>Verwenden des Abfrage-Assistenten  
  
1.  Geben Sie zunächst die Datenquelle für die Eingabe an. Sie können Daten aus einer vorhandenen Excel-Tabelle oder einem vorhandenen Excel-Bereich verwenden, oder Sie können eine SQL-Anweisung angeben, um die Daten abzurufen.  
  
2.  Anschließend wird vom Assistenten eine Liste mit Data Mining-Modellen angezeigt, die sich auf dem Server befinden, mit dem Sie verbunden sind. Wenn Sie das gewünschte Modell kennen und mit Data Mining vertraut sind, können Sie auch auf **erweitert** klicken, um den **erweiterten Data Mining-Abfrage-Editor**zu öffnen.  
  
3.  Abhängig von dem von Ihnen ausgewählten Modelltyp müssen Sie die Spalte angeben, in der sich die auszuwertenden Daten befinden, und die Zuordnungen zwischen den Eingabedatenspalten und den Modellspalten definieren. Abhängig von dem von Ihnen ausgewählten Algorithmus können Sie weitere Eigenschaften für das Modell festlegen.  
  
4.  Schließlich können Sie im Assistenten eine oder mehrere Vorhersagen auswählen und angeben, wo die Ergebnisse gespeichert werden sollen.  
  
 Sie können jederzeit auf **erweitert** klicken, um zum **erweiterten Data Mining-Abfrage-Editor**zu wechseln. Dadurch erhalten Sie mehr Kontrolle über die einzelnen Teile der DMX-Anweisung. Weitere Informationen zur Verwendung der erweiterten Tools zur Abfrage Bearbeitung finden Sie unter Erweiterter [Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md).  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Wenn Sie den **Abfrage** -Assistenten verwenden möchten, müssen Sie mit einer Instanz von verbunden sein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Außerdem muss der Server mindestens ein Data Mining-Modell eines geeigneten Typs enthalten. Wenn keine Miningmodelle verfügbar sind, können Sie mithilfe der im Data Mining-Client für Excel bereitgestellten Assistenten ein Modell erstellen. Informationen zum Erstellen eines neuen Mining Modus mithilfe eines Assistenten finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen und Skalieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   
 [Data Mining-Client für Excel &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
