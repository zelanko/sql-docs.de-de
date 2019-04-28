---
title: 'Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0780636d3bcaecfe0519192bd450bb538d78bbf9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866776"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt
  In dieser Aufgabe importieren Sie während des Bereinigungsprozesses gesammeltes Data Quality-Wissen. Finden Sie unter [Importieren von Bereinigungsprojektwerten in eine Domäne](https://msdn.microsoft.com/library/hh479581.aspx) Weitere Informationen. Sie exportieren auch die Wissensdatenbank in eine DQS-Datei vor dem Veröffentlichen der aktualisierten **Lieferanten** Knowledge Base.  
  
1.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **nach rechts weisenden Pfeil** neben **Lieferanten** unter **zuletzt verwendete Wissensdatenbank** , und klicken Sie auf **Domänenverwaltung**.  
  
2.  Klicken Sie auf **Contact Email** in der Liste der Domänen, und wechseln Sie zu der **Domänenwerte** Registerkarte im rechten Bereich.  
  
3.  Klicken Sie auf **Pfeil nach unten** neben der **Werte importieren** Symbol auf der Symbolleiste, und klicken Sie auf **Importieren von Projektwerten**.  
  
     ![Importieren des Projekts Werte Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "Import Project (Symbolleistenschaltfläche)")  
  
4.  In der **Importieren von Projektwerten** wählen Sie im Dialogfeld die **Cleanse Supplier List** Projekt, und klicken Sie auf **OK**.  
  
5.  Beachten Sie, dass alle E-Mails zusammen mit den beiden Korrekturen importiert werden, die Sie während der interaktiven Bereinigung durchgeführt haben. Führen Sie einen Bildlauf durch, um die beiden Korrekturen anzuzeigen.  
  
    |Wert|Korrigieren in|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  Wiederholen Sie den vorherigen Schritt von projektwerten für die **Land** Domäne, und beachten Sie, dass ein neuer Eintrag hinzugefügt wird, für die Behebung von **United State** zu **USA** (mit " s ").  
  
    |Wert|Korrigieren in|  
    |-----------|----------------|  
    |United State|United States|  
  
7.  Um die alten Domänenwerte anzuzeigen, deaktivieren **nur neue anzeigen** Kontrollkästchen.  
  
8.  Wiederholen Sie den vorherigen Schritt von projektwerten für die **Lieferantenname** Domäne. Standardmäßig werden nach dem Import nur die neuen Werte angezeigt. Um alle Werte anzuzeigen, deaktivieren **nur neue anzeigen** Kontrollkästchen. Sie haben erweitert die **Lieferanten** Wissensdatenbank mit, was Sie aus der bereinigungsaktivität gelernt haben. Je größer die Wissensdatenbank ist, desto besser sind die Bereinigungsergebnisse.  
  
    > [!NOTE]  
    >  Es ist nicht möglich, Werte für eine Verbunddomäne zu importieren.  
  
9. Klicken Sie auf **Wissensdatenbank exportieren** Symbol auf der Symbolleiste, und klicken Sie dann auf **Wissensdatenbank exportieren**.  
  
     ![Exportieren Sie die Wissensdatenbank Menü](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Menü der Wissensdatenbank exportieren")  
  
10. Navigieren Sie zum Lernprogrammordner, geben **Suppliers.dqs** für die **Dateiname**, und klicken Sie auf **speichern**. Sie können diese DQS-Datei verwenden, um eine neue Wissensdatenbank zu erstellen.  
  
11. Klicken Sie auf **OK** schließen die **Wissensdatenbank exportieren – Lieferanten** Meldungsfeld.  
  
12. Klicken Sie auf **Fertig stellen** auf die Aktivität fertig zu stellen.  
  
13. Klicken Sie auf **Veröffentlichen**.  
  
14. Klicken Sie auf **OK** im Meldungsfeld auf.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 3: Abgleich von Daten zu entfernen, um Duplikate aus der Lieferantenliste](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
