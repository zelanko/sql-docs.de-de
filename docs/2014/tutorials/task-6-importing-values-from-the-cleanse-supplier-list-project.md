---
title: 'Aufgabe 6: Importieren von Werten aus dem Projekt zum Bereinigen der Lieferantenliste | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cb3e7a85254cac96b8b8541de57b494e96b8928f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061064"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt
  In dieser Aufgabe importieren Sie während des Bereinigungsprozesses gesammeltes Data Quality-Wissen. Weitere Informationen finden Sie im Thema Importieren von Bereinigungs [Projekt Werten in eine Domäne](https://msdn.microsoft.com/library/hh479581.aspx) . Sie exportieren die Wissensdatenbank auch in eine DQS-Datei, bevor Sie die aktualisierte Wissensdatenbank **Suppliers** veröffentlichen.  
  
1.  Klicken Sie auf der **DQS-Client**-Hauptseite auf den **Pfeil nach rechts** neben **Suppliers** unter **zuletzt verwendete Wissensdatenbanken** , und klicken Sie dann auf **Domänen Verwaltung**.  
  
2.  Klicken Sie in der Liste der Domänen auf **Kontakt-e-Mail** , und wechseln Sie im rechten Bereich zur Registerkarte **Domänen Werte** .  
  
3.  Klicken Sie auf der Symbolleiste neben dem Symbol **Werte importieren** auf den **Pfeil nach unten** , und klicken Sie auf **Projektwerte importieren**.  
  
     ![Projektwerte importieren (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "Projektwerte importieren (Symbolleistenschaltfläche)")  
  
4.  Wählen Sie im Dialogfeld **Projektwerte importieren** das Projekt " **Lieferantenliste** bereinigen" aus, und klicken Sie auf **OK**.  
  
5.  Beachten Sie, dass alle E-Mails zusammen mit den beiden Korrekturen importiert werden, die Sie während der interaktiven Bereinigung durchgeführt haben. Führen Sie einen Bildlauf durch, um die beiden Korrekturen anzuzeigen.  
  
    |Wert|Korrigieren in|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  Wiederholen Sie den vorherigen Schritt zum Importieren von Projekt Werten für die Domäne **Country** , und beachten Sie, dass ein neuer Eintrag für die Korrektur von **United State** in **USA** (mit "s") hinzugefügt wurde.  
  
    |Wert|Korrigieren in|  
    |-----------|----------------|  
    |United State|USA|  
  
7.  Um die alten Domänen Werte anzuzeigen, deaktivieren Sie das Kontrollkästchen **nur neue anzeigen** .  
  
8.  Wiederholen Sie den vorherigen Schritt zum Importieren von Projekt Werten für die Domäne **Supplier Name** . Standardmäßig werden nach dem Import nur die neuen Werte angezeigt. Um alle Werte anzuzeigen, deaktivieren Sie das Kontrollkästchen **nur neue anzeigen** . Sie haben die Wissensdatenbank **Suppliers** mit den von der Bereinigungs Aktivität gewonnenen Informationen erweitert. Je größer die Wissensdatenbank ist, desto besser sind die Bereinigungsergebnisse.  
  
    > [!NOTE]  
    >  Es ist nicht möglich, Werte für eine Verbunddomäne zu importieren.  
  
9. Klicken Sie auf der Symbolleiste auf **Wissensdatenbank exportieren** , und klicken Sie dann auf **Wissensdatenbank exportieren**.  
  
     ![Wissensdatenbank exportieren (Menü)](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Wissensdatenbank exportieren (Menü)")  
  
10. Navigieren Sie zum Tutorial-Ordner, geben Sie **Suppliers. DQS** als **Dateiname**ein, und klicken Sie auf **Speichern**. Sie können diese DQS-Datei verwenden, um eine neue Wissensdatenbank zu erstellen.  
  
11. Klicken Sie auf **OK** , um das Meldungs Feld **Wissensdatenbank exportieren-Suppliers** zu schließen.  
  
12. Klicken Sie auf **Fertig** stellen, um die Aktivität abzuschließen.  
  
13. Klicken Sie auf **Veröffentlichen**.  
  
14. Klicken Sie im Meldungs Feld auf **OK** .  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 3: Abgleich von Daten zur Entfernung von Duplikaten aus der Lieferantenliste](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  
