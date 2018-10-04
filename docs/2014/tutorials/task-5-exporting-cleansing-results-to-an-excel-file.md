---
title: 'Aufgabe 5: Exportieren der Bereinigungsergebnisse in eine Exceldatei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2d52304ff9a8dae16e74d9d5aa7324adb2aac4f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138170"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Aufgabe 5: Exportieren der Bereinigungsergebnisse in eine Excel-Datei
  In dieser Aufgabe exportieren Sie Ergebnisse aus der Bereinigungsaktivität in eine Excel-Datei. Finden Sie unter [Exportphase](http://msdn.microsoft.com/library/hh213061.aspx#Export) Weitere Informationen.  
  
1.  Wählen Sie im rechten Bereich **Excel** für die **Zieltyp**.  
  
2.  Klicken Sie auf **Durchsuchen**, geben Sie den Namen der Ausgabedatei als **Cleansed Supplier List.xls**, und klicken Sie dann auf **öffnen**.  
  
3.  Wählen Sie **Data Only** für die **Ausgabe** Format, um nur die bereinigten Daten exportieren. Die zweite Option **Informationen zu Daten und Bereinigung**, können Sie bereinigungsaktivitätsdetails sowie die bereinigten Daten exportieren. Die **Format standardisieren** Option können Sie alle Ausgabeformate anwenden, Sie für eine Domäne für die Werte dieser Domäne definieren. Sie haben kein Ausgabeformat für die Domänen im Lernprogramm definiert.  
  
     ![Bereinigung der Export der Ergebnisse (Seite)](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Export Bereinigung Ergebnisse (Seite)")  
  
4.  Klicken Sie auf **exportieren** zum Exportieren der Daten. Klicken Sie nicht auf **Fertig stellen** noch.  
  
5.  Klicken Sie auf **schließen** auf die **exportieren** Dialogfeld.  
  
6.  Klicken Sie auf **Fertig stellen** auf die Aktivität fertig zu stellen. Wenn Sie vergessen haben, um Ergebnisse zu exportieren, bevor Sie auf **Fertig stellen**, klicken Sie auf **Open Data Quality-Projekt** auf der Hauptseite des **DQS-Client**Option **Cleanse Supplier Liste** aus der Liste der Projekte, und klicken Sie auf **Weiter** am unteren Rand des Bildschirms zum Abrufen der **exportieren** Phase der Bereinigungsprozess noch mal. Sie können auch zum wechseln **verwalten und Anzeigen der Ergebnisse** Registerkarte, indem Sie auf **wieder** Schaltfläche.  
  
7.  Öffnen der **Cleansed Supplier List.xls** und gehen Sie folgendermaßen vor:  
  
    1.  Stellen Sie sicher, dass keine E-Mail-Adressen vorhanden sind, die mit adventure-work.com (ohne "s") enden, indem Sie im Arbeitsblatt nach adventure-work.com suchen.  
  
    2.  Vorhanden ist keine **USA** Wert in der **Land** Spalte.  
  
    3.  Suchen Sie nach **Berlin** und anzuzeigen, die die **Zustand** nastaven NA hodnotu **Zertifizierungsstelle**.  
  
    4.  Bestätigen Sie, dass es keine Ausdrücke sind **Co.**, **Corp.**, und **Inc.**.  
  
    5.  Löschen der **Address Validation** Spalte aus dem Arbeitsblatt, und speichern Sie die Excel-Datei. Diese zusätzliche Spalte entspricht der Verbunddomäne "Address Validation".  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 6: Importieren von Werten aus dem Cleanse Supplier List-Projekt](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
