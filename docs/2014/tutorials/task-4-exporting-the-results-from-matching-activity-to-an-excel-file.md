---
title: 'Aufgabe 4: Exportieren Sie die Ergebnisse der Abgleichsaktivität in eine Excel-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: abded209f6367308c23e548962e1d4a5362791f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127630"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>Aufgabe 4: Exportieren der Ergebnisse der Abgleichsaktivität in eine Excel-Datei
  In dieser Aufgabe exportieren Sie die Ergebnisse aus der Abgleichsaktivität in eine Excel-Datei.  
  
1.  In der **exportieren** Seite **Excel-Datei** für die **Zieltyp**.  
  
2.  Wählen Sie **Survivorship-Ergebnisse** Option. Im Survivorship-Prozess legt DQS einen Survivor-Datensatz für jeden Cluster basierend auf den **Survivorship-Regel** Sie ausgewählt haben.  
  
3.  Klicken Sie auf **Durchsuchen** , und navigieren Sie zu dem Ordner, in dem Sie die Ausgabedatei speichern möchten.  
  
4.  Typ **Cleansed and Matched Suppliers.xls** ein, und klicken Sie auf **öffnen**.  
  
5.  Überprüfen Sie, ob **Pivotdatensatz** ausgewählt ist, für die **Survivorship-Regel**. Wenn Sie diese Option wählen, wird der Pivotdatensatz für jeden Cluster für die Ausgabe aus einem Cluster ausgewählt. Die anderen Optionen für die Survivorship-Regel sind:  
  
    1.  **Vollständigster Datensatz:** Survivor-Datensatz ist der Datensatz mit der größten Anzahl ausgefüllter Felder.  
  
    2.  **Längster Datensatz:** Survivor-Datensatz ist der Datensatz mit der größten Anzahl von Begriffen in Quellfeldern.  
  
    3.  **Vollständigster und Längster Datensatz:** Survivor-Datensatz ist der Datensatz mit der größten Anzahl ausgefüllter Felder und verfügt über die größte Anzahl von Begriffen in jedem Feld.  
  
     ![Exportieren von Ergebnissen aus der Seite "übereinstimmend"](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Exportieren von Ergebnissen aus der Seite \"übereinstimmend\"")  
  
6.  Klicken Sie auf **exportieren** die Ergebnisse in einer Excel-Datei exportieren.  
  
7.  Klicken Sie auf **schließen** schließen die **Export wird abgeglichen** Dialogfeld.  
  
8.  Klicken Sie auf **Fertig stellen** um die abgleichsaktivität fertigzustellen.  
  
9. Öffnen der **Cleansed and Matched Suppliers.xlsx** Datei, und bestätigen Sie, dass keine Duplikate (SupplierID) angezeigt wird.  
  
 Nun verfügen Sie über Lieferantendaten, die bereinigt und abgeglichen wurden, um Duplikate zu entfernen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 4: Speichern von Lieferantendaten in MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  
