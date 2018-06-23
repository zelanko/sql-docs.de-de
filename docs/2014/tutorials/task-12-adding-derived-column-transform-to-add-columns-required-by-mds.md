---
title: 'Aufgabe 12: Hinzufügen von abgeleiteten Spalte Transformation an, die von MDS erforderliche Spalten hinzuzufügen | Microsoft Docs'
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
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b81dd18f0ba79167a66b5cdd09c2059fcd0e0a96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159886"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>Aufgabe 12: Hinzufügen der Transformation 'Abgeleitete Spalten', um für MDS erforderliche Spalten hinzuzufügen
  In dieser Aufgabe fügen Sie die Transformation "Abgeleitete Spalte" zum Datenfluss hinzu. Sie fügen zwei abgeleitete Spalten, **ImportType** und **BatchTag**in die Datensätze an diese Transformation übergeben. Sie sollten diese Spalten hinzufügen, bevor Sie die Daten in Stagingtabellen in MDS hochladen. Diese beiden Spalten sind für die Stagingtabellen in MDS erforderliche Spalten. Finden Sie unter [Stagingtabellen für Blattelemente](http://msdn.microsoft.com/library/ee633854.aspx) Weitere Details.  
  
1.  Drag & Drop **Transformation für abgeleitete Spalten** aus **allgemeine** im Abschnitt der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte.  
  
2.  Mit der rechten Maustaste **abgeleitete Spalten** transformieren Sie der **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Add Columns Required by MDS** , und drücken Sie **EINGABETASTE**.  
  
3.  Verbinden **Filterduplikate+++** auf **Add Columns Required by MDS** mithilfe des blauen Konnektors. Daraufhin sollte die **Eingabe/Ausgabe-Auswahl** (Dialogfeld).  
  
4.  In der **Eingabe/Ausgabe-Auswahl** wählen Sie im Dialogfeld **eindeutige Datensätze**, und klicken Sie auf **OK**.  
  
     ![Geben Sie die Ausgabe-Auswahl (Dialogfeld)](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Eingabe Ausgabe Benutzerauswahl (Dialogfeld)")  
  
5.  Klicken Sie auf **SSIS** auf der Menüleiste und auf **Variablen**.  
  
6.  In der **Variablen** Fenster, klicken Sie auf **Variable hinzufügen** auf der Symbolleiste.  
  
     ![SSIS-Variablen (Fenster)](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS-Variablen (Fenster)")  
  
7.  Typ **ImportType** für die **Namen** und **2** für die **Wert**. Sie geben den Wert 2 an, da Sie einer Entität in MDS neue Elemente hinzufügen möchten. Einzelheiten zu diesem Parameter finden Sie unter [Stagingtabelle für Blattelemente](http://msdn.microsoft.com/library/ee633854.aspx).  
  
8.  Klicken Sie auf **Variable hinzufügen** Symbolleisten-Schaltfläche erneut aus.  
  
9. Typ **BatchTag** für die **Namen**Option **Zeichenfolge** für die **Datentyp**, und **EIMBatch** für die **Wert**. **BatchTag** ist nur ein eindeutiger Name für den Batch, die Sie an MDS senden werden.  
  
10. In der **Datenfluss** Registerkarte, doppelklicken Sie auf **Add Columns Required by MDS**.  
  
11. In der **Transformations-Editor für abgeleitete Spalte** Dialogfeld die **Listenfeld im unteren Bereich**, Typ **ImportType** für die **Name der abgeleiteten Spalte**.  
  
12. Erweitern Sie **Variablen und Parametern** in der linken oberen Bereich Drag & Drop **User:: importtype** auf die **Ausdruck** Spalte.  
  
     ![Transformations-Editor für abgeleitete](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "abgeleitete Spalte Transformations-Editor")  
  
13. Typ **BatchTag** in der nächsten Zeile für die **Name der abgeleiteten Spalte**.  
  
14. Drag & Drop **User:: batchtag** aus **Variablen und Parametern** auf die **Ausdruck** Spalte.  
  
15. Klicken Sie auf **OK** schließen die **Derived Column Transformation** (Dialogfeld).  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 13: Hinzufügen von OLE DB-Ziels, um Daten in die MDS-Stagingtabelle zu schreiben](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  