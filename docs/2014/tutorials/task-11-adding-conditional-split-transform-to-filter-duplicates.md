---
title: 'Aufgabe 11: Hinzufügen der Transformation für bedingtes Teilen zum Filtern von Duplikaten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad925c543cefaf7aed5a0ef355029312b3de7140
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064801"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>Aufgabe 11: Hinzufügen der Transformation „Bedingtes Teilen“ zur Filterung von Duplikaten
  In dieser Aufgabe fügen Sie die Transformation für bedingtes Teilen zum Datenfluss hinzu. Mit dieser Transformation können Sie Duplikate aus dem eingehenden Recordset filtern. Die Transformation für Fuzzygruppierung gruppiert die gefundenen übereinstimmenden Datensätze und wählt einen der Datensätze als Pivotdatensatz aus. Alle Datensätze in einer Gruppe verfügen über denselben _key_out-Wert. Für den Pivotdatensatz in der Gruppe sind der _key_in-Wert und der _key_out-Wert gleich. Für die anderen Datensätze in der Gruppe sind die Werte für _key_in und _key_out unterschiedlich. Wenn Sie mit condition _key_in==_key_out filtern, erhalten Sie daher nur die Pivotzeile in der Gruppe.  
  
1.  Ziehen Sie die Transformation für **bedingtes Teilen** aus **Common** section in der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** .  
  
2.  Klicken Sie **mit der rechten** Maustaste auf die **Transformation für bedingtes Teilen** , und klicken Sie dann auf **Umbenennen**. Geben Sie **Filter Duplikate** ein, und drücken **Sie Eingabe**.  
  
3.  Verbinden Sie **Gruppen Lieferanten mit übereinstimmenden IDs** , um **Duplikate zu filtern**.  
  
4.  Doppelklicken Sie auf **Filter Duplikate** , um das Dialogfeld **Transformations-Editor für bedingtes Teilen aufzurufen** .  
  
5.  Erweitern Sie im linken oberen Bereich die Option **Spalten** .  
  
6.  Ziehen Sie **_key_in** in die Spalte **Bedingung** .  
  
7.  Geben Sie = = (entspricht) neben **_key_in** ein, und ziehen Sie **_key_out**.  
  
8.  Klicken Sie in der Spalte **Ausgabe Name** auf **Fall 1** , geben Sie **eindeutige Datensätze**ein, und drücken **Sie Eingabe**Taste.  
  
     ![Transformations-Editor für bedingtes Teilen](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Transformations-Editor für bedingtes Teilen")  
  
9. Klicken Sie zum Schließen des Dialog Felds **Transformations-Editor für bedingtes Teilen** auf **OK** .  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 12: Hinzufügen der Transformation „Abgeleitete Spalten“ zum Hinzufügen der für MDS erforderlichen Spalten](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
