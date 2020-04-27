---
title: 'Lektion 4: Markieren als Datums Tabelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26877c4892b050cbf9c8dcc6553530dff513f8fc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66078785"
---
# <a name="lesson-4-mark-as-date-table"></a>Lektion 4: Als Datumstabelle markieren
  In "Lektion 2: Hinzufügen von Daten" haben Sie eine Dimensionstabelle mit dem Namen "DimDate" importiert. Dann haben Sie in "Lektion 3: Umbenennen von Spalten" die Tabelle "DimDate" in "Date" umbenannt. In Ihrem Modell lautet der Name dieser Tabelle jetzt „Date“, sie kann jedoch auch als *Datumstabelle* bezeichnet werden, da sie Datums- und Uhrzeitdaten enthält.  
  
 Immer wenn Sie in Berechnungen Zeitintelligenzfunktionen verwenden, z.B. in Kürze beim Erstellen von Measures, müssen Sie Eigenschaften von Datentabellen angeben, die eine *Datumstabelle* und als eindeutigen Bezeichner die *Datumsspalte* in dieser Tabelle enthalten. Sie können dann gültige Beziehungen zwischen anderen Tabellen und der Datumstabelle erstellen. Dies ist für Berechnungen mit DAX-Zeitintelligenzfunktionen erforderlich.  
  
 In dieser Lektion kennzeichnen Sie die importierte und umbenannte Date-Tabelle als *Datumstabelle* und die Date-Spalte (in der Date-Tabelle) als *Datumsspalte* (eindeutiger Bezeichner). Alle Verwendungsmöglichkeiten des Namens Datums können verwirrend sein, aber Sie werden bald die Idee erhalten.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **3 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der richtigen Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 3: Umbenennen von Spalten](rename-columns.md).  
  
### <a name="to-set-mark-as-date-table"></a>Markieren als Datumstabelle  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Date** .  
  
2.  Klicken Sie im Menü **Tabelle** auf **Datum**, und klicken Sie dann auf **als Datums Tabelle markieren**.  
  
3.  Wählen Sie im Dialogfeld **Als Datumstabelle markieren** im Listenfeld **Datum** die Spalte **Datum** als eindeutigen Bezeichner aus.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 5: Erstellen von Beziehungen](lesson-4-create-relationships.md).  
  
  
