---
title: 'Aufgabe 13: Hinzufügen OLE DB Ziels zum Schreiben von Daten in die MDS-Stagingtabelle | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65476988"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a>Aufgabe 13: Hinzufügen von OLE DB-Zielen zum Schreiben von Daten in die MDS-Stagingtabelle
  Nachdem Sie die Werte für " **importtype** " und " **batchtag** " allen Datensätzen hinzugefügt haben, können Sie Sie für das Staging an MDS senden. In dieser Aufgabe verwenden Sie das OLE DB Ziel, um die Daten in die **Stagingtabelle "STG. supplier_Leaf** " zu schreiben.  
  
1.  Ziehen Sie **OLE DB Ziel** aus dem Abschnitt **andere Ziele** in der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** , und legen Sie Sie unter für **MDS erforderliche Spalten hinzufügen**fest.  
  
2.  Klicken Sie mit der rechten Maustaste auf **OLE DB Ziel** auf der Registerkarte **Datenfluss** , und klicken Sie auf **Umbenennen** Geben Sie **Daten in MDS-Stagingtabelle schreiben ein,** und drücken **Sie die Eingabe**Taste  
  
3.  Verbinden Sie die **von MDS benötigten Add-Spalten** , um Lieferantendaten mit dem blauen Connector **in die MDS-Stagingtabelle zu schreiben** .  
  
4.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf **Lieferantendaten in MDS-Stagingtabelle schreiben** .  
  
5.  Stellen Sie im Dialog Feld **Ziel-Editor für OLE DB** sicher, dass **(local). MDS** (oder **localhost. MDS**) für das Feld **OLE DB Verbindungs-Manager** ausgewählt.  
  
6.  Wählen Sie **STG aus. Supplier_Leaf** Tabelle aus der Liste der **Namen der Tabelle oder Sicht**.  
  
     ![Ziel-Editor für OLE DB](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "Ziel-Editor für OLE DB")  
  
7.  Wechseln Sie zur Seite Zuordnungen, indem Sie im Menü **auf der linken** Seite auf **Zuordnung** klicken.  
  
8.  Ordnen Sie die **Eingabe** -und **Ziel** Spalten zu, wie in der folgenden Tabelle gezeigt.  
  
     ![Ziel-Editor für OLE DB – Zuordnungen](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "Ziel-Editor für OLE DB – Zuordnungen")  
  
9. Vergewissern Sie sich, dass Sie **_Output** Spalten für Eingabe Spalten verwenden, nicht die **_Status** -oder **_Source** Spalten. **_Output** Spalten enthalten die Ausgabewerte der DQS-Bereinigung.  
  
10. Klicken Sie auf **OK** , um das Dialogfeld **Ziel-Editor OLE DB** zu schließen.  
  
11. Der Datenfluss sollte wie in folgendem Bild aussehen.  
  
     ![Abgeschlossener Datenfluss](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Abgeschlossener Datenfluss")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 14: Hinzufügen des Tasks „SQL ausführen“ zur Ablaufsteuerung, um die gespeicherte Prozedur für MDS auszuführen](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
