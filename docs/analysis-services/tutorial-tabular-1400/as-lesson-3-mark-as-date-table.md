---
title: 'Analysis Services-Tutorial – Lektion 3: Markieren als Datumstabelle | Microsoft-Dokumentation'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82b4093aa1a46cf1a7bb14b4c689ba6ba09e4d2b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973167"
---
# <a name="mark-as-date-table"></a>Als Datumstabelle markieren

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In Lektion 2: Abrufen von Daten, importierten eine Dimensionstabelle namens **DimDate**. In Ihrem Modell mit DimDate benannte Tabelle ist, sie können auch bezeichnet werden als eine *Datumstabelle*, darin, dass es sich um Datums-und Uhrzeitdaten enthält.  
  
Bei jeder Verwendung von DAX-zeitintelligenzfunktionen, z. B. Wenn Sie Measures später erstellen Sie müssen Eigenschaften angeben, u.a. ein *Datumstabelle* und eines eindeutigen Bezeichners *Datumsspalte* in dieser Tabelle.
  
In dieser Lektion kennzeichnen Sie die **DimDate** als Tabelle die *Date-Tabelle* und **Datum** Spalte (in der Datumstabelle) als die *Datumsspalte* (eindeutig Bezeichner).  

Bevor Sie die Datumstabelle und Datumsspalte markieren, ist es ein guter Zeitpunkt, führen Sie einige einfache Wartungsaufgaben, um Ihr Modell verständlicher zu machen. Beachten Sie, dass in der Tabelle DimDate eine Spalte namens **FullDateAlternateKey**. Diese Spalte enthält eine Zeile für jeden Tag in jedem Kalenderjahr in der Tabelle. Sie verwenden diese Spalte sehr viel in measureformeln und Berichten. Allerdings ist FullDateAlternateKey kein guter Bezeichner für diese Spalte. Sie benennen Sie sie in **Datum**, um zu identifizieren, und schließen Sie in Formeln zu vereinfachen. Wann immer möglich, ist es eine gute Idee, Umbenennen von Objekten wie Tabellen und Spalten, die sie in SSDT und Client-berichtsanwendungen Identifizierung vereinfachen. 
  
Geschätzte Zeit zum Abschließen dieser Lektion: **drei Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion an, Sie sollten die vorherige Lektion abgeschlossen haben: [Lektion 2: Abrufen von Daten](../tutorial-tabular-1400/as-lesson-2-get-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Zum Umbenennen der Spalte FullDateAlternateKey

1.  Klicken Sie im Modell-Designer auf die **DimDate** Tabelle.

2.  Doppelklicken Sie auf die Kopfzeile für die **FullDateAlternateKey** Spalte, und benennen Sie sie in **Datum**.

  
### <a name="to-set-mark-as-date-table"></a>So legen Sie "Als Datumstabelle markieren" fest  
  
1.  Wählen Sie die **Datum** -Spalte und stellen Sie anschließend im Fenster **Eigenschaften** unter **Datentyp**sicher, dass  **Datum** ausgewählt ist.  
  
2.  Klicken Sie im Menü **Tabelle** auf **Datum**und anschließend auf **Als Datumstabelle markieren**.  
  
3.  Wählen Sie im Dialogfeld **Als Datumstabelle markieren** im Listenfeld **Datum** die Spalte **Datum** als eindeutigen Bezeichner aus. Es ist in der Regel standardmäßig aktiviert. Klicken Sie auf **OK**. 

    ![als-lesson3-Date-Tabelle](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 4: Erstellen von Beziehungen](../tutorial-tabular-1400/as-lesson-4-create-relationships.md).
  
