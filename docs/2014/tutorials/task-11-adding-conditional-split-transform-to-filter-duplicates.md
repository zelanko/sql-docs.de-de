---
title: 'Aufgabe 11: Hinzufügen von bedingter Transformation, um Duplikate zu filtern Teilen | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7f61fa706659a6f71b2c69f18bcf7b694993ed00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060841"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>Aufgabe 11: Hinzufügen der Transformation 'Bedingtes Teilen', um Duplikate zu filtern
  In dieser Aufgabe fügen Sie die Transformation für bedingtes Teilen zum Datenfluss hinzu. Mit dieser Transformation können Sie Duplikate aus dem eingehenden Recordset filtern. Die Transformation für Fuzzygruppierung gruppiert die gefundenen übereinstimmenden Datensätze und wählt einen der Datensätze als Pivotdatensatz aus. Alle Datensätze in einer Gruppe verfügen über denselben _key_out-Wert. Für den Pivotdatensatz in der Gruppe sind der _key_in-Wert und der _key_out-Wert gleich. Für die anderen Datensätze in der Gruppe sind die Werte für _key_in und _key_out unterschiedlich. Wenn Sie mit condition _key_in==_key_out filtern, erhalten Sie daher nur die Pivotzeile in der Gruppe.  
  
1.  Drag & Drop **bedingtes Teilen** transformiert aus **allgemeine** im Abschnitt der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte.  
  
2.  Mit der rechten Maustaste **Transformation für bedingtes Teilen** in der **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Filterduplikate+++** , und drücken Sie **EINGABETASTE**.  
  
3.  Verbinden **Gruppe Lieferanten mit übereinstimmenden IDs** auf **Filtern Duplikate**.  
  
4.  Doppelklicken Sie auf **Filterduplikate+++** zum Starten der **bedingte Split Transformation Editor** (Dialogfeld).  
  
5.  Erweitern Sie **Spalten** in der linken oberen Bereich.  
  
6.  Drag & Drop **_key_in** auf die **Bedingung** Spalte.  
  
7.  Typ (gleich) neben == **_key_in** und Drag & Drop **_key_out**.  
  
8.  Klicken Sie auf **Fall 1** in der **Ausgabename** Geben Sie die Spalte **eindeutige Datensätze**, und drücken Sie die **EINGABETASTE**.  
  
     ![Transformations-Editor für bedingtes Teilen](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Transformations-Editor für bedingtes Teilen")  
  
9. Klicken Sie auf **OK** schließen die **Transformations-Editor für bedingtes Teilen** (Dialogfeld).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 12: Hinzufügen der Transformation „Abgeleitete Spalten“, um für MDS erforderliche Spalten hinzuzufügen](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  