---
title: Erweiterte Data Mining-Abfrage-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80b2705920b7793f7f89b323a16fa2f3618e4d1c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62635632"
---
# <a name="advanced-data-mining-query-editor"></a>Erweiterter Data Mining-Abfrage-Editor
  Die **erweiterten Data Mining Query Editor** ist ein Tool zum Erstellen benutzerdefinierter Modelle und Abfragen können.  
  
 Der Editor enthält eine Reihe von Vorlagen mit klickbaren Links. Klicken Sie einfach auf die einzelnen Links, und verwenden Sie die Dialogfelder, um Objekte oder Werte auszuwählen und komplexe DMX-Anweisungen (Data Mining Extensions) zu erstellen. Sie können zur Textbearbeitungsmodell-Ansicht wechseln, um die DMX-Anweisung manuell zu ändern.  
  
 Zum Abrufen der **erweiterten Data Mining Query Editor**, klicken Sie auf **Abfrage** , und klicken Sie dann auf **erweitert**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **DMX-Abfrage**  
 Hier ist die aktuelle DMX-Anweisung zu sehen.  
  
 Klicken Sie mit der rechten Maustaste in den Bereich, um die aktuelle DMX-Anweisung zu kopieren.  
  
 Sie können auf einen hervorgehobenen Teil der Anweisung klicken, um spezielle Optionen für die jeweilige Klausel aufzurufen. Um beispielsweise zu löschen, hinzufügen oder bearbeiten die Ausgabe mit der rechten Maustaste die  **\<Ausgabe >** Link.  
  
 **Query-Abfrage-Generator bearbeiten**  
 Verwenden Sie diese Schaltfläche, um den Editor zwischen einem Text-Editor, zu wechseln, in dem Sie DMX-Anweisungen direkt schreiben können; und die **Abfragegenerator**, dessen Hilfe Sie eine DMX-Anweisung erstellen.  
  
> [!NOTE]  
>  **Warnung:** Wenn Sie die Ansichten wechseln, bevor die Abfrage ausgeführt wurde, wird eine Meldung an, die besagt, dass Sie einige Änderungen verloren gehen können. Wenn die DMX-Anweisung gültig ist, in vielen Fällen ist die **Abfragegenerator** diese Änderungen erfolgreich konvertiert. Wenn Sie jedoch eine besonders komplexe DMX-Anweisung erstellt haben, sollten Sie Ihre Arbeit unbedingt speichern, bevor Sie die Ansicht wechseln.  
  
 **DMX-Vorlagen**  
 Klicken Sie auf diese Option, und wählen Sie aus einer Liste von Vorlagen aus, die DMX-Beispiele enthalten. Die Vorlagen stellen praktisch alle Modell- oder Vorhersageabfragetypen bereit, die Sie benötigen, einschließlich Abfragen, die geschachtelte Tabellen verwenden, und DMX-Anweisungen zur Verwaltung von Modellen. Auch wenn Sie mit der Verwendung von DMX vertraut sind, können Sie mit den Vorlagen u. U. Zeit sparen, weil Sie direkt die richtige Syntax erhalten.  
  
 **Modell auswählen**  
 Klicken Sie auf diese Option, um eine Liste der über die aktuelle Verbindung verfügbaren Data Mining-Modelle anzuzeigen.  
  
 Sie können auch eine Liste der verfügbaren Modelle anzeigen, indem Sie auf den Modellnamen in der DMX-Anweisung im der **DMX-Abfrage** Bereich. Der Modellname ist in der Regel rot hervorgehoben.  
  
 **Eingabe auswählen**  
 Klicken Sie auf diese Option, um die Daten auszuwählen, die als Eingabe für das Miningmodell verwendet werden sollen. Wenn keine Datenquelle angegeben wurde, können Sie auch klicken die  **\<Eingabe >** Link, der in rot hervorgehoben ist die **DMX-Abfrage** Bereich.  
  
 Wählen Sie **@InputRowset** aus der Dropdownliste aus, öffnen Sie die **Inputrowset1 ersetzen** Dialogfeld ein, und eine vorhandene Eingabe zu ändern.  
  
 Wählen Sie **Eingabe hinzufügen** zum Öffnen der **Eingabe hinzufügen** Dialogfeld Geben Sie eine neue Datenquelle.  
  
 Sie können auch eine vorhandene Eingabe ändern, indem Sie auf die **@InputRowset** Link, der im DMX-Abfragebereich rot hervorgehoben ist.  
  
 **Zuordnen von Spalten**  
 Wählen Sie Spalten aus dem Miningmodell aus, und ordnen Sie sie dann Spalten in der externen Datenquelle zu.  
  
 Sie können auch die hervorgehobene klicken  **\<Zuordnung >** Link im Bereich DMX-Abfrage.  
  
 **Ausgabe hinzufügen**  
 Klicken Sie auf diese Option, um die Spalten auszuwählen, die als Bestandteil einer Vorhersageabfrage ausgegeben werden sollen.  
  
 Sie können auch die hervorgehobene klicken  **\<Ausgabe hinzufügen >** Link im Bereich DMX-Abfrage.  
  
 **Modellspalten**  
 Listet die Spalten im ausgewählten Miningmodell auf. Mit einem Rautenzeichen neben dem Spaltennamen wird angegeben, dass die Spalte vorhersagbar ist.  
  
 **Eingabespalten**  
 Listet die Spalten aus der externen Datenquelle auf, die als Eingaben hinzugefügt wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
  
  
