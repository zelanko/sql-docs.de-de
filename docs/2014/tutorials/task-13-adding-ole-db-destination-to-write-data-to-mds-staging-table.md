---
title: 'Aufgabe 13: Hinzufügen von OLE DB-Ziels zum Schreiben von Daten in MDS-Stagingtabelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7c5fc9d863c23c1cae08c04fef7810aeda446762
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476988"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>Aufgabe 13: Hinzufügen von OLE DB-Zielen zum Schreiben von Daten in die MDS-Stagingtabelle
  Nun, da Sie hinzugefügt haben, **ImportType** und **BatchTag** Werte für alle Datensätze, Sie sind bereit, um sie an MDS für das Staging senden. In dieser Aufgabe verwenden Sie das OLE DB-Ziel zum Schreiben der Daten in **supplier_leaf** Stagingtabelle.  
  
1.  Ziehen Sie **OLE DB-Ziel** aus **andere Ziele** im Abschnitt der **SSIS-Toolbox** auf die **Datenfluss** Registerkarte, und legen Sie es unter  **Hinzufügen von MDS erforderliche Spalten**.  
  
2.  Mit der rechten Maustaste **OLE DB-Ziel** in die **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Write Supplier Data to MDS Staging Table** , und drücken Sie **EINGABETASTE**.  
  
3.  Verbinden der **Add Columns Required by MDS** zu **Write Supplier Data to MDS Staging Table** mithilfe des blauen Konnektors.  
  
4.  Doppelklicken Sie auf **Write Supplier Data to MDS Staging Table** in die **Datenfluss** Registerkarte.  
  
5.  In der **Ziel-Editor für OLE DB** Dialogfeld Feld, stellen Sie sicher, dass **(lokal). MDS** (oder **"localhost". MDS**) ausgewählt ist, für die **OLE DB-Verbindungs-Manager** Feld.  
  
6.  Wählen Sie **stg. Supplier_Leaf** Tabelle aus der Liste der **Name, der in der Tabelle oder Sicht**.  
  
     ![Ziel-Editor für OLE DB](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLE DB-Ziel-Editor")  
  
7.  Wechseln Sie zu der **Zuordnungen** Seite, indem Sie auf **Zuordnung** im Menü auf der linken Seite.  
  
8.  Zuordnung **Eingabe** und **Ziel** Spalten wie in der folgenden Tabelle gezeigt.  
  
     ![OLE DB-Ziel-Editor - Zuordnungen](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLE DB-Ziel-Editor - Zuordnungen")  
  
9. Vergewissern Sie sich die Verwendung von **_ausgabe** -Spalten für Eingabespalten, nicht die **_Status** oder **_quelle** Spalten. **_Ausgabe** Spalten enthalten die Ausgabewerte der DQS-Bereinigung.  
  
10. Klicken Sie auf **OK** schließen die **Ziel-Editor für OLE DB** Dialogfeld.  
  
11. Der Datenfluss sollte wie in folgendem Bild aussehen.  
  
     ![Abgeschlossen-Datenfluss](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Datenfluss abgeschlossen")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 14: Hinzufügen von Execute SQL Task zur Ablaufsteuerung, um die gespeicherte Prozedur für MDS auszuführen](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
