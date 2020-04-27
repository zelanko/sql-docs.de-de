---
title: 'Aufgabe 8: Hinzufügen der Transformation für bedingtes Teilen zum Aufteilen der Bereinigungs Ausgabe Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d5a55f0694094e6fe88a42946bcff34f420210f4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489669"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a>Aufgabe 8: Hinzufügen der Transformation „Bedingtes Teilen“ zur Teilung der Bereinigungsausgabe
  In dieser Aufgabe fügen Sie eine Transformation "Bedingtes Teilen" zum Datenfluss hinzu. Die Transformation "Bedingtes Teilen" kann Zeilen je nach Dateninhalt an andere Ausgaben routen. In diesem Tutorial verwenden Sie die Ausgabe Spalte für den **Daten Satz Status** aus der Transformation für die DQS-Bereinigung. Sie laden in diesem Lernprogramm nur richtige oder korrigierte Datensätze zu MDS-Server hoch. Daher überprüfen Sie, ob der **Status des Datensatzes** **korrekt** oder **korrigiert**ist, und kombinieren die Datensätze, bevor Sie die Datensätze in MDS hochladen.  
  
1.  Ziehen Sie die **Transformation für bedingtes Teilen** aus **Common** section in der **SSIS-Toolbox** in die Registerkarte **Datenfluss** unter Bereinigen von **Lieferantendaten**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **bedingtes Teilen**, und klicken **Sie auf** Geben Sie **richtige und korrigierte Datensätze auswählen** ein, und drücken **Sie Eingabe**  
  
3.  Verbinden Sie **Lieferantendaten** , und **Wählen Sie richtige und korrigierte Datensätze** mit dem blauen Connector aus.  
  
     ![Lieferantendaten bereinigen-> Auswahl korrigieren & korrigiert](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Lieferantendaten bereinigen -> Richtige auswählen & Korrigiert")  
  
4.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf **richtige und korrigierte Datensätze auswählen** .  
  
5.  Ändern Sie den **standardmäßigen Ausgabe Namen** unten auf dem Bildschirm, um ihn zu **korrigieren**.  
  
6.  Erweitern Sie im **linken oberen**Bereich die Option **Spalten** .  
  
     ![Transformations-Editor für bedingtes Teilen](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Transformations-Editor für bedingtes Teilen")  
  
7.  Ziehen Sie **Daten Satz Status** in die Spalte **Bedingung** .  
  
8.  Geben Sie **= = "korrigiert"** neben **[Daten Satz Status]** für die Spalte **Bedingung** ein.  
  
9. Klicken Sie in der **Spalte Ausgabe Name**auf Groß-/Kleinschreibung **1** , und ändern Sie den Namen in **korrigiert**.  
  
10. Klicken Sie zum Schließen des Dialog Felds **Transformations-Editor für bedingtes Teilen** auf **OK** .  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 9: Hinzufügen der Transformation UNION ALL zur Kombination richtiger und korrigierter Datensätze](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
