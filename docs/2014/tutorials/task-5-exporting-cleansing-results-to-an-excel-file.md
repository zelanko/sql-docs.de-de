---
title: 'Aufgabe 5: Exportieren der Bereinigungs Ergebnisse in eine Excel-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 44c926d2429a0d9842e9e9202568f73f72c89d9a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064750"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Aufgabe 5: Exportieren der Bereinigungsergebnisse in eine Excel-Datei
  In dieser Aufgabe exportieren Sie Ergebnisse aus der Bereinigungsaktivität in eine Excel-Datei. Weitere Informationen finden Sie im Thema [Exportieren von Stufen](https://msdn.microsoft.com/library/hh213061.aspx#Export) .  
  
1.  Wählen Sie im rechten Bereich für den **Zieltyp**die Option **Excel** aus.  
  
2.  Klicken Sie auf **Durchsuchen**, geben Sie den Namen der Ausgabedatei als **bereinigten Lieferanten #b0 **an, und klicken Sie dann auf **Öffnen**  
  
3.  Wählen Sie **Daten nur** für das **Ausgabe** Format aus, um nur die bereinigten Daten zu exportieren. Mit der zweiten Option ( **Daten-und**Bereinigungs Informationen) können Sie Bereinigungs Aktivitäts Details zusammen mit den bereinigten Daten exportieren. Mit der Option **Format standardisieren** können Sie alle Ausgabeformate, die Sie für eine Domäne definieren, auf die Werte dieser Domäne anwenden. Sie haben kein Ausgabeformat für die Domänen im Lernprogramm definiert.  
  
     ![Bereinigungsergebnisse exportieren (Seite)](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Bereinigungsergebnisse exportieren (Seite)")  
  
4.  Klicken Sie auf **exportieren** , um die Daten zu exportieren. Klicken Sie noch nicht auf **Fertig** stellen.  
  
5.  Klicken Sie im Dialogfeld **exportieren** auf **Schließen** .  
  
6.  Klicken Sie auf **Fertig** stellen, um die Aktivität abzuschließen. Wenn Sie vergessen haben, die Ergebnisse zu exportieren, bevor Sie auf **Fertig**stellen klicken, klicken Sie auf der Hauptseite des **DQS-Clients**auf **Data Quality-Projekt öffnen** , wählen Sie **Lieferantenliste** bereinigen aus der Liste der Projekte aus, und klicken Sie unten auf dem Bildschirm auf **weiter** , um die **Export** Phase des Bereinigungs Prozesses erneut Sie können auch zur Registerkarte **Ergebnisse verwalten und anzeigen** wechseln, indem Sie auf die Schaltfläche **zurück** klicken.  
  
7.  Öffnen Sie den **bereinigten Lieferanten List.xls** , und führen Sie die folgenden Schritte aus:  
  
    1.  Stellen Sie sicher, dass keine e-Mail-Adressen vorhanden sind, die mit Adventure-work.com (ohne Zeichen ') enden, indem Sie im Arbeitsblatt nach Adventure-work.com suchen.  
  
    2.  Sehen Sie, dass in der Spalte **Country** kein Wert für **USA** vorhanden ist.  
  
    3.  Suchen Sie nach **Los Angeles** , und sehen Sie, dass der **Status** auf **ca**festgelegt ist.  
  
    4.  Vergewissern Sie sich, dass keine Begriffe **Co.**, **Corp.** und **Inc.** vorhanden sind.  
  
    5.  Löschen Sie die Spalte **Adressvalidierung** aus der Tabelle, und speichern Sie die Excel-Datei. Diese zusätzliche Spalte entspricht der Verbunddomäne "Address Validation".  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
