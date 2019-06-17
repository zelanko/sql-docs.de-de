---
title: 'Aufgabe 11: Hinzufügen bedingter Split-Transformation, um Duplikate zu filtern | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 71b050e49440764d355d4658607600c135741f50
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65476749"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>Aufgabe 11: Hinzufügen der Transformation „Bedingtes Teilen“ zur Filterung von Duplikaten
  In dieser Aufgabe fügen Sie die Transformation für bedingtes Teilen zum Datenfluss hinzu. Mit dieser Transformation können Sie Duplikate aus dem eingehenden Recordset filtern. Die Transformation für Fuzzygruppierung gruppiert die gefundenen übereinstimmenden Datensätze und wählt einen der Datensätze als Pivotdatensatz aus. Alle Datensätze in einer Gruppe verfügen über denselben _key_out-Wert. Für den Pivotdatensatz in der Gruppe sind der _key_in-Wert und der _key_out-Wert gleich. Für die anderen Datensätze in der Gruppe sind die Werte für _key_in und _key_out unterschiedlich. Wenn Sie mit condition _key_in==_key_out filtern, erhalten Sie daher nur die Pivotzeile in der Gruppe.  
  
1.  Drag & Drop **für bedingtes Teilen** Transformationen von **allgemeine** im Abschnitt der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte.  
  
2.  Mit der rechten Maustaste **Transformation für bedingtes Teilen** in die **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Filterduplikate+++** , und drücken Sie **EINGABETASTE**.  
  
3.  Connect **Gruppe ' Suppliers ' mit übereinstimmenden IDs** zu **Duplikate zu filtern**.  
  
4.  Doppelklicken Sie auf **Filterduplikate+++** zum Starten der **bedingte Split Transformation Editor** Dialogfeld.  
  
5.  Erweitern Sie **Spalten** in der linken oberen Bereich.  
  
6.  Drag & Drop **_key_in** auf die **Bedingung** Spalte.  
  
7.  Typ == (gleich) neben **_key_in** und Drag & Drop **_key_out**.  
  
8.  Klicken Sie auf **Fall 1** in die **Ausgabename** Spalte, Datentyp **eindeutige Datensätze**, und drücken Sie die **EINGABETASTE**.  
  
     ![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Conditional Split Transformation Editor")  
  
9. Klicken Sie auf **OK** schließen die **Conditional Split Transformation Editor** Dialogfeld.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 12: Hinzufügen der abgeleitete Spalte-Transformation, die von MDS erforderliche Spalten hinzuzufügen](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
