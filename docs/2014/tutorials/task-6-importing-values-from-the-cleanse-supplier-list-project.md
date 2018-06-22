---
title: 'Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt | Microsoft Docs'
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
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7a915013d779392d585bd5609384fab7bffd2800
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049814"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt
  In dieser Aufgabe importieren Sie während des Bereinigungsprozesses gesammeltes Data Quality-Wissen. Finden Sie unter [Importieren von Bereinigungsprojektwerten in eine Domäne](http://msdn.microsoft.com/library/hh479581.aspx) Weitere Informationen. Sie exportieren auch die Wissensdatenbank in eine DQS-Datei vor dem Veröffentlichen die aktualisierte **Lieferanten** Knowledge Base.  
  
1.  Auf der Hauptseite des **DQS-Client**, klicken Sie auf **Pfeil nach rechts** neben **Lieferanten** unter **zuletzt verwendete Wissensdatenbank** , und klicken Sie auf **Domänenverwaltung**.  
  
2.  Klicken Sie auf **Contact Email** in der Liste der Domänen, und wechseln Sie in der **Domänenwerte** Registerkarte im rechten Bereich.  
  
3.  Klicken Sie auf **Pfeil nach unten** neben der **Werte importieren** Symbol auf der Symbolleiste, und klicken Sie auf **Projektwerte**.  
  
     ![Import-Projekt Werte Symbolleisten-Schaltfläche](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "importieren (Symbolleistenschaltfläche)")  
  
4.  In der **Projektwerte** wählen Sie im Dialogfeld die **Cleanse Supplier List** Projekt, und klicken Sie auf **OK**.  
  
5.  Beachten Sie, dass alle E-Mails zusammen mit den beiden Korrekturen importiert werden, die Sie während der interaktiven Bereinigung durchgeführt haben. Führen Sie einen Bildlauf durch, um die beiden Korrekturen anzuzeigen.  
  
    |value|Korrigieren in|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  Wiederholen Sie den vorherigen Schritt importieren von projektwerten für die **Land** Domänen- und beachten Sie, dass ein neuer Eintrag, für die Korrektur von hinzugefügt wird **United State** auf **United States** (mit " s ").  
  
    |value|Korrigieren in|  
    |-----------|----------------|  
    |United State|United States|  
  
7.  Um die alten Domänenwerte anzuzeigen, deaktivieren Sie **nur neue anzeigen** Kontrollkästchen.  
  
8.  Wiederholen Sie den vorherigen Schritt importieren von projektwerten für die **Lieferantenname** Domäne. Standardmäßig werden nach dem Import nur die neuen Werte angezeigt. Um alle Werte anzuzeigen, deaktivieren Sie **nur neue anzeigen** Kontrollkästchen. Sie haben erweitert die **Lieferanten** Wissensdatenbank mit aus der bereinigungsaktivität erworbenen. Je größer die Wissensdatenbank ist, desto besser sind die Bereinigungsergebnisse.  
  
    > [!NOTE]  
    >  Es ist nicht möglich, Werte für eine Verbunddomäne zu importieren.  
  
9. Klicken Sie auf **Wissensdatenbank exportieren** Symbol auf der Symbolleiste, und klicken Sie dann auf **Wissensdatenbank exportieren**.  
  
     ![Exportieren Sie die Wissensdatenbank im Menü](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Menü Wissensdatenbank exportieren")  
  
10. Navigieren Sie zum Lernprogrammordner, geben **Suppliers.dqs** für die **Dateiname**, und klicken Sie auf **speichern**. Sie können diese DQS-Datei verwenden, um eine neue Wissensdatenbank zu erstellen.  
  
11. Klicken Sie auf **OK** schließen die **Wissensdatenbank exportieren – Lieferanten** Meldungsfeld.  
  
12. Klicken Sie auf **Fertig stellen** auf die Aktivität fertig zu stellen.  
  
13. Klicken Sie auf **Veröffentlichen**.  
  
14. Klicken Sie auf **OK** im Meldungsfeld.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 3: Abgleich von Daten, um Duplikate aus der Lieferantenliste zu entfernen](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  