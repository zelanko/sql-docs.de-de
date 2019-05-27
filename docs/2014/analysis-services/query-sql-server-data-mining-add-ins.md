---
title: Abfrage (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: dcddeb64b14301f08a7dc723ef89737102f257ad
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66070482"
---
# <a name="query-sql-server-data-mining-add-ins"></a>Abfrage (SQL Server Data Mining-Add-Ins)
  ![Schaltfläche "Abfrage-Modell", "Data Mining-Menüband](media/dmc-query.gif "Abfragemodell-Schaltfläche, Data Mining-Menüband")  
  
 Die **Abfrage** Assistenten können Sie die Interaktion mit vorhandenen Miningmodellen zum treffen von Vorhersagen basierend auf Daten in einer Excel-Tabelle, einem Excel-Bereich oder einer anderen Datenquelle. Der Prozess der Anwendung neuer Daten an ein vorhandenes Modell zum Vorhersagen von Trends heißt eine *Vorhersageabfrage*.  
  
 Die **Abfrage** Assistent bietet auch einen erweiterten Editor zum Erstellen oder Ändern von Datamining-Modellen, zum Generieren benutzerdefinierter Abfragen oder zum Arbeiten mit Strukturen, die in den anderen Tools wie z. B. geschachtelte Datasets nicht unterstützt.  
  
-   Verwenden Sie den Text-Editor zu geben oder fügen in den Data Mining Extensions (DMX)-Anweisungen, die Sie an anderer Stelle erstellt haben.  
  
-   Verwenden Sie den interaktiven Abfrage-Generator, um eine benutzerdefinierte DMX-Anweisung mithilfe von Vorlagen und Dialogfeldern zusammenzustellen.  
  
-   Erstellen Sie DMX-Anweisungen zum Verwalten oder Sichern von Miningmodellen und -strukturen.  
  
## <a name="using-the-query-wizard"></a>Verwenden des Abfrage-Assistenten  
  
1.  Geben Sie zunächst die Datenquelle für die Eingabe an. Sie können Daten aus einer vorhandenen Excel-Tabelle oder einem vorhandenen Excel-Bereich verwenden, oder Sie können eine SQL-Anweisung angeben, um die Daten abzurufen.  
  
2.  Anschließend wird vom Assistenten eine Liste mit Data Mining-Modellen angezeigt, die sich auf dem Server befinden, mit dem Sie verbunden sind. Wenn Sie das Modell kennen, Sie möchten, und mit dem Datamining vertraut sind, können Sie auch klicken **erweitert** zum Öffnen der **Erweiterter Editor für Data Mining**.  
  
3.  Abhängig von dem von Ihnen ausgewählten Modelltyp müssen Sie die Spalte angeben, in der sich die auszuwertenden Daten befinden, und die Zuordnungen zwischen den Eingabedatenspalten und den Modellspalten definieren. Abhängig von dem von Ihnen ausgewählten Algorithmus können Sie weitere Eigenschaften für das Modell festlegen.  
  
4.  Schließlich können Sie im Assistenten eine oder mehrere Vorhersagen auswählen und angeben, wo die Ergebnisse gespeichert werden sollen.  
  
 Sie können zu jedem Zeitpunkt klicken **erweitert** So wechseln Sie zu der **erweiterten Data Mining Query Editor**, das bietet Ihnen mehr Kontrolle über die einzelnen Teile der DMX-Anweisung. Weitere Informationen zur Verwendung von Tools für die erweiterten abfragebearbeitung finden Sie unter [erweiterte Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md).  
  
### <a name="requirements"></a>Anforderungen  
 Verwenden der **Abfrage** Assistenten muss eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Außerdem muss der Server mindestens ein Data Mining-Modell eines geeigneten Typs enthalten. Wenn keine Miningmodelle verfügbar sind, können Sie mithilfe der im Data Mining-Client für Excel bereitgestellten Assistenten ein Modell erstellen. Informationen dazu, wie Sie ein neues Miningmodell zu erstellen, indem Sie mithilfe eines Assistenten finden Sie unter [Erstellen von Data Mining-Modells](creating-a-data-mining-model.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen und Skalieren von Miningmodellen &#40;Data Mining-Add-ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   
 [Datamining-Client für Excel &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
