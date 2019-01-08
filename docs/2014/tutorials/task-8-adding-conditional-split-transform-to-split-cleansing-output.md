---
title: 'Aufgabe 8: Hinzufügen von bedingter Split Transformation zum Aufteilen der Bereinigung der Ausgabe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa9f529e286951aab08bb2d29f8dcc06f837e8c2
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52408965"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>Aufgabe 8: Hinzufügen einer Transformation 'Bedingtes Teilen', um die Bereinigungsausgabe zu teilen
  In dieser Aufgabe fügen Sie eine Transformation "Bedingtes Teilen" zum Datenfluss hinzu. Die Transformation "Bedingtes Teilen" kann Zeilen je nach Dateninhalt an andere Ausgaben routen. In diesem Tutorial verwenden Sie die **Datensatzstatus** Ausgabespalte von der DQS-bereinigungstransformation. Sie laden in diesem Lernprogramm nur richtige oder korrigierte Datensätze zu MDS-Server hoch. Aus diesem Grund Sie überprüfen, ob die **Datensatzstatus** ist **richtig** oder **korrigiert**, und kombinieren die Datensätze vor dem die Datensätze in MDS hochladen.  
  
1.  Drag & Drop **Transformation für bedingtes Teilen** aus **allgemeine** im Abschnitt der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte unter **Lieferantendaten Bereinigen**.  
  
2.  Mit der rechten Maustaste **für bedingtes Teilen**, und klicken Sie auf **umbenennen**. Typ **Pick Correct and Corrected Records** , und drücken Sie **EINGABETASTE**.  
  
3.  Herstellen einer mit **Cleanse Supplier Data** und **Pick Correct and Corrected Records** mithilfe des blauen Konnektors.  
  
     ![Cleanse Supplier Data -> richtige auswählen & korrigiert](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier Data -> richtige auswählen & korrigiert")  
  
4.  Doppelklicken Sie auf **Pick Correct and Corrected Records** in die **Datenfluss** Registerkarte.  
  
5.  Ändern der **Standardausgabename** am unteren Rand des Bildschirms **richtig**.  
  
6.  Erweitern Sie **Spalten** in die **linken oberen Bereich**.  
  
     ![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Conditional Split Transformation Editor")  
  
7.  Drag & Drop **Datensatzstatus** auf die **Bedingung** Spalte.  
  
8.  Typ **== "Corrected"** neben **[Datensatzstatus]** für die **Bedingung** Spalte.  
  
9. Klicken Sie auf **Fall 1** in die **Name der Ausgabespalte**, und ändern Sie den Namen in **korrigiert**.  
  
10. Klicken Sie auf **OK** schließen die **Conditional Split Transformation Editor** Dialogfeld.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Hinzufügen der Union aller Transformation um richtige und korrigierte Datensätze zu kombinieren.](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
