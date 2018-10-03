---
title: 'Lektion 4: Markieren als Datumstabelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26eb4f82b97d745f6269d57a76c479d677d6cc2c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177530"
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
  
  
