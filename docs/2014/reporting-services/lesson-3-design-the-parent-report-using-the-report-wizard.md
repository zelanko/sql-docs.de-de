---
title: 'Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8d47f5480a5e01000b23830d36fb6b0da586dfa4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246470"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>Lektion 3: Entwerfen des übergeordneten Berichts mithilfe des Berichts-Assistenten
  Nachdem Sie eine Datenverbindung und eine Datentabelle für den übergeordneten Bericht erstellt haben, entwerfen Sie im nächsten Schritt den übergeordneten Bericht mithilfe des Berichts-Assistenten im Berichts-Designer. Weitere Informationen zum Berichts-Designer finden Sie unter [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>So entwerfen Sie den übergeordneten Bericht mithilfe des Berichts-Assistenten  
  
1.  Stellen Sie sicher, dass die Website der obersten Ebene im **Projektmappen-Explorer**ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Website, und wählen Sie **Neues Element hinzufügen**aus.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Berichts-Assistent**aus, geben Sie einen Namen für die Berichtsdatei ein, und klicken Sie dann auf **Hinzufügen**.  
  
     Daraufhin wird der Berichts-Assistent gestartet.  
  
4.  Auf der **Dataseteigenschaften** auf der Seite der **Datenquelle** wählen Sie im der **"DataSet1"** Sie erstellt haben, im [Lektion 2: Definieren einer Datenverbindung und einer Datentabelle für Übergeordnete Bericht](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
    Das Feld **Verfügbare Datasets** wird automatisch anhand der oben erstellten **DataTable** aktualisiert.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Gehen Sie auf der Seite **Felder anordnen** wie folgt vor:  
  
    1.  Ziehen Sie **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**und **ReorderLevel** vom Feld **Verfügbare Felder** auf das Feld **Werte** .  
  
    2.  Klicken Sie auf den Pfeil neben **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** und deaktivieren Sie die **Summe** Auswahl.  
  
7.  Klicken Sie zweimal auf **Weiter** , und klicken Sie auf **Fertig stellen** , um den **Berichts-Assistenten**zu schließen.  
  
     Die RDLC-Datei ist jetzt erstellt. Die Datei wird im Berichts-Designer geöffnet. Die entworfene Tablix wird jetzt auf der Entwurfsoberfläche angezeigt.  
  
8.  Speichern Sie die RDLC-Datei.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich den übergeordneten Bericht mithilfe des Berichts-Assistenten entworfen. Als Nächstes erstellen Sie eine Datenverbindung und eine Datentabelle für den untergeordneten Bericht.  
  
  
