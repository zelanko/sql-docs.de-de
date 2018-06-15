---
title: 'Lektion 4: Markieren als Datumstabelle | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77f29250621485f5606a0bf33615e8d15eb7d80b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019697"
---
# <a name="lesson-3-mark-as-date-table"></a>Lektion 3: Markieren Sie als Date-Tabelle
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In "Lektion 2: Hinzufügen von Daten" haben Sie eine Dimensionstabelle mit dem Namen "DimDate" importiert. Während in Ihrem Modell in dieser Tabelle DimDate heißt, sie können auch bekannt sein als eine *Datumstabelle*, insofern, dass es sich um Datums-und Uhrzeitdaten enthält.  
  
Jedes Mal, wenn Sie DAX-zeitintelligenzfunktionen in Berechnungen, wie Sie ausführen müssen, wenn Sie Measures etwas später erstellen, müssen Sie angeben, dass Datum Tabelleneigenschaften, darunter eine *Datumstabelle* und einen eindeutigen Bezeichner *Datum Spalte* in dieser Tabelle.
  
In dieser Lektion fügen Sie die DimDate-Tabelle als kennzeichnen die *Datumstabelle* und die Spalte "Date" (in der Date-Tabelle) als die *Datumsspalte* (unique Identifier).  

Bevor wir die Datumstabelle und Datumsspalte kennzeichnen, muss ein wenig Wartungsaufgaben um unserem Modell verständlicher zu erledigen. Sie werden bemerken in der Tabelle DimDate eine Spalte mit dem Namen **FullDateAlternateKey**. Es enthält eine Zeile für jeden Tag in jedes Kalenderjahr in der Tabelle enthalten. Diese Spalte viele wird in measureformeln und in Berichten verwendet werden. Allerdings FullDateAlternateKey ist kein wirklich gute Bezeichner für diese Spalte. Fügen wir benennen Sie sie um **Datum**, leichter zu identifizieren und in Formeln enthalten. Wann immer möglich, ist es eine gute Idee, Umbenennen von Objekten wie Tabellen und Spalten, um sie zu vereinfachen, Clientanwendungen zur berichterstellung wie Power BI und Excel zu ermitteln. 
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **3 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion, Sie sollten haben die vorherige Lektion abgeschlossen: [Lektion 2: Hinzufügen von Daten](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Umbenennen der FullDateAlternateKey-Spalte

1.  Klicken Sie im Modell-Designer auf die **DimDate** Tabelle.

2.  Klicken Sie mit der Doppelklicken auf die Kopfzeile für die **FullDateAlternateKey** Spalte, und benennen Sie sie um **Datum**.

  
### <a name="to-set-mark-as-date-table"></a>So legen Sie "Als Datumstabelle markieren" fest  
  
1.  Wählen Sie die **Datum** -Spalte und stellen Sie anschließend im Fenster **Eigenschaften** unter **Datentyp**sicher, dass  **Datum** ausgewählt ist.  
  
2.  Klicken Sie im Menü **Tabelle** auf **Datum**und anschließend auf **Als Datumstabelle markieren**.  
  
3.  Wählen Sie im Dialogfeld **Als Datumstabelle markieren** im Listenfeld **Datum** die Spalte **Datum** als eindeutigen Bezeichner aus. Es wird in der Regel standardmäßig ausgewählt. Klicken Sie auf **OK**. 

    ![als tabellarische-lesson3-Date-Tabelle](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 4: Erstellen von Beziehungen](../analysis-services/lesson-4-create-relationships.md).
  
