---
title: 'Aufgabe 8: Hinzufügen von bedingter Transformation aufzuteilende Bereinigung Ausgabe aufgeteilt | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6dc3b98e03a7940841bc97012c1a4e4220bb970d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148300"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>Aufgabe 8: Hinzufügen einer Transformation 'Bedingtes Teilen', um die Bereinigungsausgabe zu teilen
  In dieser Aufgabe fügen Sie eine Transformation "Bedingtes Teilen" zum Datenfluss hinzu. Die Transformation "Bedingtes Teilen" kann Zeilen je nach Dateninhalt an andere Ausgaben routen. Für dieses Lernprogramm verwenden Sie die **Datensatzstatus** Ausgabespalte von der Transformation für DQS-Bereinigung. Sie laden in diesem Lernprogramm nur richtige oder korrigierte Datensätze zu MDS-Server hoch. Daher überprüfen, ob die **Datensatzstatus** ist **richtig** oder **korrigiert**, und kombinieren die Datensätze, bevor Sie die Datensätze in MDS hochladen.  
  
1.  Drag & Drop **Transformation für bedingtes Teilen** aus **allgemeine** im Abschnitt der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte unter **Cleanse Supplier Data**.  
  
2.  Mit der rechten Maustaste **bedingtes Teilen**, und klicken Sie auf **umbenennen**. Typ **Pick Correct and Corrected Records** , und drücken Sie **EINGABETASTE**.  
  
3.  Verbinden **Cleanse Supplier Data** und **Pick Correct and Corrected Records** mithilfe des blauen Konnektors.  
  
     ![Lieferantendaten-> richtige auswählen & korrigiert](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Lieferantendaten-> richtige auswählen & korrigiert")  
  
4.  Doppelklicken Sie auf **Pick Correct and Corrected Records** in der **Datenfluss** Registerkarte.  
  
5.  Ändern der **Standardausgabename** am unteren Rand des Bildschirms **richtig**.  
  
6.  Erweitern Sie **Spalten** in der **linken oberen Bereich**.  
  
     ![Transformations-Editor für bedingtes Teilen](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Transformations-Editor für bedingtes Teilen")  
  
7.  Drag & Drop **Datensatzstatus** auf die **Bedingung** Spalte.  
  
8.  Typ **== "Corrected"** neben **[Datensatzstatus]** für die **Bedingung** Spalte.  
  
9. Klicken Sie auf **Fall 1** in der **Name der Ausgabespalte**, und ändern Sie den Namen in **korrigiert**.  
  
10. Klicken Sie auf **OK** schließen die **Transformations-Editor für bedingtes Teilen** (Dialogfeld).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Hinzufügen der Transformation UNION ALL, um richtige und korrigierte Datensätze zu kombinieren](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  