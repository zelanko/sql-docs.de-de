---
title: 'Lektion 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 661b4f3cc63eb0c19fddb53f872e940d1f9976e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108440"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>Lektion 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten
  Nachdem Sie eine Datenverbindung und eine Datentabelle für den untergeordneten Bericht erstellt haben, entwerfen Sie im nächsten Schritt den untergeordneten Bericht mithilfe des Berichts-Assistenten im Berichts-Designer. Weitere Informationen zum Berichts-Designer finden Sie unter [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>So entwerfen Sie den untergeordneten Bericht mithilfe des Berichts-Assistenten  
  
1.  Stellen Sie sicher, dass die Website der obersten Ebene im **Projektmappen-Explorer**ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Website, und wählen Sie **Neues Element hinzufügen**aus.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Berichts-Assistent**, geben Sie einen Namen für die Berichtsdatei ein, und klicken Sie dann auf **Hinzufügen**.  
  
     Daraufhin wird der Berichts-Assistent gestartet.  
  
4.  Klicken Sie auf der Seite **Dataseteigenschaften** im Feld **Datenquelle** auf **DataSet2**.  
  
     Das Feld **Verfügbare Datasets** wird automatisch anhand der erstellen DataTable aktualisiert.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Gehen Sie auf der Seite **Felder anordnen** wie folgt vor:  
  
    1.  Ziehen Sie **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**und **StockedQty** aus **Verfügbare Felder** in das Feld **Werte** .  
  
    2.  Klicken Sie auf den Pfeil neben **Sum(ProductID)** , **Sum(PurchaseOrderID)** , **Sum(PurchaseOrderDetailID)** , **Sum(OrderQty)** ,  **SUM(ReceivedQty)** , **Sum(RejectedQty)** , und **Sum(StockedQty)** und deaktivieren Sie die **Summe** Auswahl.  
  
7.  Klicken Sie zweimal auf **Weiter** , und klicken Sie auf **Fertig stellen** , um den **Berichts-Assistenten**zu schließen.  
  
     Die RDLC-Datei ist jetzt erstellt. Die Datei wird im Berichts-Designer geöffnet. Die entworfene Tablix wird jetzt auf der Entwurfsoberfläche angezeigt.  
  
8.  Fügen Sie bei geöffneter RDLC-Datei auf folgende Weise einen Parameter hinzu:  
  
    1.  Klicken Sie im **Berichtsdatenbereich** auf **Parameter** , und klicken Sie dann auf **Parameter hinzufügen**.  
  
    2.  Geben Sie im Feld **Name** die Zeichenfolge **productid** ein.  
  
    3.  Vergewissern Sie sich, dass im Listenfeld **Datentyp** der Eintrag **Integer** ausgewählt ist.  
  
    4.  Klicken Sie auf **OK**.  
  
9. Speichern Sie die RDLC-Datei.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich den untergeordneten Bericht mit dem Berichts-Assistenten entworfen. Als Nächstes fügen Sie der Websiteanwendung ein ReportViewer-Steuerelement hinzu.  
  
  
