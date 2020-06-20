---
title: 'Aufgabe 3: Erstellen und Ausführen eines Data Quality-Projekts für den Abgleich | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8de716da5a7f845f68bd50fa09b04594bf883ad6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85035405"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>Aufgabe 3: Erstellen und Ausführen eines Data Quality-Projekts für Abgleiche
  In dieser Aufgabe erstellen Sie ein Data Quality-Projekt für die Abgleichsaktivität, und führen den Abgleichsprozess für bereinigte Lieferantendaten durch, um Duplikate in den Daten zu entfernen.

1.  Klicken Sie auf der Hauptseite des **DQS-Clients**auf **Neues Data Quality-Projekt**.

2.  Geben Sie **Lieferanten Duplikate entfernen** aus dem **Namen des Projekts**ein.

3.  Wählen Sie **Suppliers** aus der Liste der KSB für das Feld **Wissensdatenbank verwenden** aus. Sie haben eine Abgleichsrichtlinie in dieser Wissensdatenbank in der vorherigen Lektion erstellt.

4.  Wählen Sie in der **Liste der Aktivitäten** aus dem unteren rechten Bereich **übereinstimmende überein** Stimmungen aus.

     ![Neues Data Quality-Projekt – "Abgleich" ausgewählt](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "Neues Data Quality-Projekt – "Abgleich" ausgewählt")

5.  Klicken Sie auf **Weiter**.

6.  Wählen Sie auf der Seite **Zuordnen** für **Datenquelle** die Option **Excel-Datei**aus.

7.  Klicken Sie auf **Durchsuchen** , und wählen Sie bereinigten Lieferanten List.xlsaus. Dies ist die Ausgabedatei der **Bereinigungs **Aktivität.

8.  Ordnen Sie die Spalte **SupplierID** Source **der Lieferanten-ID** -Domäne, der Spalte **Lieferanten Name** in der Domäne **Lieferanten Name** und der Spalte **contactemailaddress** an die Domäne **Contact Email** zu.

9. Klicken Sie auf **weiter** , um **zur Seite** Abgleich zu wechseln.

10. Klicken Sie zum Starten des abgleichsprozesses auf **Start** . Es sollten Ergebnisse angezeigt werden, die denen aus der vorherigen Aufgabe ähneln, da Sie dieselbe Eingabedatei zur Definition der Abgleichsrichtlinie verwendet haben.

11. Prüfen Sie alle übereinstimmenden Datensätze und ihre Treffergenauigkeit im Listenfeld. Die Ergebnisse sollten denen aus der vorherigen Aufgabe entsprechen. Analysieren Sie die Ergebnisse aus dieser Abgleichsaktivität anhand der Schritte in der vorherigen Aufgabe.

12. Klicken Sie auf **weiter** , um zur Seite **exportieren** zu wechseln.

## <a name="next-step"></a>Nächster Schritt
 [Aufgabe 4: Exportieren der Ergebnisse der Abgleichaktivität in eine Excel-Datei](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


