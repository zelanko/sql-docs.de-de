---
title: 'Aufgabe 12: Hinzufügen der Transformation für abgeleitete Spalten zum Hinzufügen von für MDS benötigten Spalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 18789f5bc1d97e1531588d50e2430829f95912b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65485240"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a>Aufgabe 12: Hinzufügen der Transformation 'Abgeleitete Spalten', um für MDS erforderliche Spalten hinzuzufügen
  In dieser Aufgabe fügen Sie die Transformation "Abgeleitete Spalte" zum Datenfluss hinzu. Sie fügen den Datensätzen, die an diese Transformation übermittelt werden, zwei abgeleitete Spalten, **importtype** und **batchtag**, hinzu. Sie sollten diese Spalten hinzufügen, bevor Sie die Daten in Stagingtabellen in MDS hochladen. Diese beiden Spalten sind für die Stagingtabellen in MDS erforderliche Spalten. Weitere Informationen finden Sie unter [Stagingtabellen für Blatt](../master-data-services/leaf-member-staging-table-master-data-services.md) Elemente.  
  
1.  Ziehen Sie die **Transformation für abgeleitete Spalten** von **Common** section in der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Transformation für **abgeleitete Spalten** auf der Registerkarte **Datenfluss** , und **Klicken Sie** Geben **Sie Add Columns required by MDS** ein, und drücken **Sie die Eingabe**Taste  
  
3.  Verbindungs **Filter Duplikate** zum **Hinzufügen von Spalten, die von MDS** mit dem blauen Connector benötigt werden. Das Dialogfeld **Eingabe Ausgabe Auswahl** sollte angezeigt werden.  
  
4.  Wählen Sie im Dialogfeld **Eingabe Ausgabe Auswahl** die Option **eindeutige Datensätze**aus, und klicken Sie auf **OK**.  
  
     ![Eingabe-/Ausgabe-Auswahl (Dialogfeld)](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Eingabe-/Ausgabe-Auswahl (Dialogfeld)")  
  
5.  Klicken Sie in der Menüleiste auf **SSIS** , und klicken Sie auf **Variablen**.  
  
6.  Klicken Sie im Fenster **Variablen** auf der Symbolleiste auf die Schaltfläche **Variable hinzufügen** .  
  
     ![SSIS-Variablen (Fenster)](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS-Variablen (Fenster)")  
  
7.  Geben Sie **importtype** als **Name** und **2** für den **Wert**ein. Sie geben den Wert 2 an, da Sie einer Entität in MDS neue Elemente hinzufügen möchten. Ausführliche Informationen zu diesem Parameter finden Sie unter [Stagingtabelle für Blatt](../master-data-services/leaf-member-staging-table-master-data-services.md)Elemente.  
  
8.  Klicken Sie erneut auf die Schaltfläche **Variable hinzufügen** .  
  
9. Geben Sie **batchtag** als **Name**ein, wählen Sie **Zeichenfolge** für den **Datentyp**aus, und geben Sie für den **Wert** **eimbatch** ein. **Batchtag** ist nur ein eindeutiger Name für den Batch, den Sie an MDS senden.  
  
10. Doppelklicken Sie auf der Registerkarte **Datenfluss** auf **Spalten hinzufügen, die von MDS benötigt**werden.  
  
11. Geben Sie im Dialogfeld **Transformations-Editor für abgeleitete Spalte** im **Listenfeld im unteren**Bereich **importtype** als Namen der **abgeleiteten Spalte**ein.  
  
12. Erweitern Sie **Variablen und Parameter** im oberen linken Bereich, und ziehen Sie **User:: importtype** in die Spalte **Ausdruck** .  
  
     ![Transformations-Editor für abgeleitete Spalte](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "Transformations-Editor für abgeleitete Spalte")  
  
13. Geben Sie **batchtag** in der nächsten Zeile für den **Namen der abgeleiteten Spalte**ein.  
  
14. Ziehen Sie **User:: batchtag** aus **Variablen und Parametern** in die Spalte **Ausdruck** .  
  
15. Klicken Sie auf **OK** , um die **Transformation für abgeleitete Spalten** zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 13: Hinzufügen von OLE DB-Ziels, um Daten in die MDS-Stagingtabelle zu schreiben](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
