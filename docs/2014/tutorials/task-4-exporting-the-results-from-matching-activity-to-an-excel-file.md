---
title: 'Aufgabe 4: Exportieren der Ergebnisse aus der abgleichsaktivität in eine Excel-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4ed1d29af328a162eafadb1ce7a160c262bdcba3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177248"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>Aufgabe 4: Exportieren der Ergebnisse der Abgleichaktivität in eine Excel-Datei
  In dieser Aufgabe exportieren Sie die Ergebnisse aus der Abgleichsaktivität in eine Excel-Datei.

1.  Wählen Sie auf der Seite **exportieren** für den **Zieltyp**die Option **Excel-Datei** aus.

2.  Wählen Sie die Option **Survivorship results** aus. Im Survivorship-Prozess bestimmt DQS basierend auf der ausgewählten **Survivorship-Regel** einen Survivor-Datensatz für jeden Cluster.

3.  Klicken Sie auf **Durchsuchen** , und navigieren Sie zu dem Ordner, in dem Sie die Ausgabedatei speichern möchten.

4.  Geben Sie für den Namen **bereinigt und den entsprechenden Lieferanten. xls** ein, und klicken Sie auf **Öffnen**.

5.  Vergewissern Sie sich, dass **Pivot-Datensatz** für die **Survivorship-Regel**ausgewählt ist. Wenn Sie diese Option wählen, wird der Pivotdatensatz für jeden Cluster für die Ausgabe aus einem Cluster ausgewählt. Die anderen Optionen für die Survivorship-Regel sind:

    1.  **Vollständiger Datensatz:** Der Survivor-Datensatz ist der Datensatz mit der größten Anzahl ausgefüllten Felder.

    2.  **Längster Datensatz:** Der Survivor-Datensatz ist der Datensatz mit der größten Anzahl von Begriffen in den Quell Feldern.

    3.  **Vollständigster und Längster Datensatz:** Der Survivor-Datensatz ist der Datensatz mit der größten Anzahl von ausgefüllten Feldern, und er verfügt über die größte Anzahl von Begriffen in jedem Feld.

     ![Exportieren von Ergebnissen von der Seite "Übereinstimmend"](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Exportieren von Ergebnissen von der Seite "Übereinstimmend"")

6.  Klicken Sie auf **exportieren** , um die Ergebnisse in eine Excel-Datei zu exportieren.

7.  Klicken Sie auf **Schließen** , um das Dialogfeld **übereinstimmende Exporte** zu schließen

8.  Klicken Sie zum Abschließen der abgleichsaktivität auf **Fertig** stellen

9. Öffnen Sie die **gebereinigt und übereinstimmende Datei Suppliers. xlsx** , und vergewissern Sie sich, dass keine Duplikate (SupplierID) angezeigt werden.

 Nun verfügen Sie über Lieferantendaten, die bereinigt und abgeglichen wurden, um Duplikate zu entfernen.

## <a name="next-step"></a>Nächster Schritt
 [Lektion 4: Speichern von Lieferantendaten in MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


