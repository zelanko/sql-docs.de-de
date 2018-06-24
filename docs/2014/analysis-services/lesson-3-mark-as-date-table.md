---
title: 'Lektion 4: Markieren als Datumstabelle | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: a283b56c215e51dbdb0df90b9c51c21e232df2f9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057903"
---
# <a name="lesson-4-mark-as-date-table"></a>Lektion 4: Markieren als Datumstabelle
  In "Lektion 2: Hinzufügen von Daten" haben Sie eine Dimensionstabelle mit dem Namen "DimDate" importiert. Dann haben Sie in "Lektion 3: Umbenennen von Spalten" die Tabelle "DimDate" in "Date" umbenannt. In Ihrem Modell lautet der Name dieser Tabelle jetzt „Date“, sie kann jedoch auch als *Datumstabelle* bezeichnet werden, da sie Datums- und Uhrzeitdaten enthält.  
  
 Immer wenn Sie in Berechnungen Zeitintelligenzfunktionen verwenden, z.B. in Kürze beim Erstellen von Measures, müssen Sie Eigenschaften von Datentabellen angeben, die eine *Datumstabelle* und als eindeutigen Bezeichner die *Datumsspalte* in dieser Tabelle enthalten. Sie können dann gültige Beziehungen zwischen anderen Tabellen und der Datumstabelle erstellen. Dies ist für Berechnungen mit DAX-Zeitintelligenzfunktionen erforderlich.  
  
 In dieser Lektion kennzeichnen Sie die importierte und umbenannte Date-Tabelle als *Datumstabelle* und die Date-Spalte (in der Date-Tabelle) als *Datumsspalte* (eindeutiger Bezeichner). Diese Verwendung des Namens "Date" bzw. "Datum" kann verwirrend sein, Sie werden jedoch bald das Prinzip begreifen.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **3 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 3: Umbenennen von Spalten](rename-columns.md).  
  
### <a name="to-set-mark-as-date-table"></a>So legen Sie "Als Datumstabelle markieren" fest  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Date** .  
  
2.  Klicken Sie im Menü **Tabelle** auf **Datum** und anschließend auf **Als Datumstabelle markieren**.  
  
3.  Wählen Sie im Dialogfeld **Als Datumstabelle markieren** im Listenfeld **Datum** die Spalte **Datum** als eindeutigen Bezeichner aus.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 5: Erstellen von Beziehungen](lesson-4-create-relationships.md).  
  
  