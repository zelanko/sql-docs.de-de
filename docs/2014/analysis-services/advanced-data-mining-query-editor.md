---
title: Erweiterte Data Mining-Abfrage-Editor | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 430a9263b15b385dd6e5f8f7aa24be15a54edffd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048394"
---
# <a name="advanced-data-mining-query-editor"></a>Editor für erweiterte Data Mining
  Die **Data Mining erweiterten Abfrage-Editor** ist ein Tool, das Sie Erstellen benutzerdefinierter Modelle und Abfragen können.  
  
 Der Editor enthält eine Reihe von Vorlagen mit klickbaren Links. Klicken Sie einfach auf die einzelnen Links, und verwenden Sie die Dialogfelder, um Objekte oder Werte auszuwählen und komplexe DMX-Anweisungen (Data Mining Extensions) zu erstellen. Sie können zur Textbearbeitungsmodell-Ansicht wechseln, um die DMX-Anweisung manuell zu ändern.  
  
 Um auf die **Data Mining erweiterten Abfrage-Editor**, klicken Sie auf **Abfrage** , und klicken Sie dann auf **erweitert**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **DMX-Abfrage**  
 Hier ist die aktuelle DMX-Anweisung zu sehen.  
  
 Klicken Sie mit der rechten Maustaste in den Bereich, um die aktuelle DMX-Anweisung zu kopieren.  
  
 Sie können auf einen hervorgehobenen Teil der Anweisung klicken, um spezielle Optionen für die jeweilige Klausel aufzurufen. Z. B. hinzufügen, löschen oder bearbeiten eine Ausgabe mit der rechten Maustaste die  **\<Ausgabe >** Link.  
  
 **Query-Abfrage-Generator bearbeiten**  
 Verwenden Sie diese Schaltfläche, um Editor zwischen einem Text-Editor zu wechseln, in dem Sie DMX-Anweisungen direkt schreiben können; und die **Abfragegenerator**, dessen Hilfe Sie eine DMX-Anweisung erstellen.  
  
> [!NOTE]  
>  **Warnung:** , wenn Sie die Ansichten wechseln, bevor die Abfrage ausgeführt wurde, eine Meldung angezeigt, die besagt, dass Sie einige Änderungen verloren gehen können. Wenn die DMX-Anweisung gültig ist, in vielen Fällen ist die **Abfragegenerator** diese Änderungen erfolgreich konvertiert. Wenn Sie jedoch eine besonders komplexe DMX-Anweisung erstellt haben, sollten Sie Ihre Arbeit unbedingt speichern, bevor Sie die Ansicht wechseln.  
  
 **DMX-Vorlagen**  
 Klicken Sie auf diese Option, und wählen Sie aus einer Liste von Vorlagen aus, die DMX-Beispiele enthalten. Die Vorlagen stellen praktisch alle Modell- oder Vorhersageabfragetypen bereit, die Sie benötigen, einschließlich Abfragen, die geschachtelte Tabellen verwenden, und DMX-Anweisungen zur Verwaltung von Modellen. Auch wenn Sie mit der Verwendung von DMX vertraut sind, können Sie mit den Vorlagen u. U. Zeit sparen, weil Sie direkt die richtige Syntax erhalten.  
  
 **Modell auswählen**  
 Klicken Sie auf diese Option, um eine Liste der über die aktuelle Verbindung verfügbaren Data Mining-Modelle anzuzeigen.  
  
 Sie können auch eine Liste der verfügbaren Modelle anzeigen, indem Sie auf den Modellnamen in der DMX-Anweisung in der **DMX-Abfrage** Bereich. Der Modellname ist in der Regel rot hervorgehoben.  
  
 **Eingabe auswählen**  
 Klicken Sie auf diese Option, um die Daten auszuwählen, die als Eingabe für das Miningmodell verwendet werden sollen. Wenn keine Datenquelle angegeben wurde, Sie können auch klicken Sie auf die  **\<Eingabe >** verknüpfen, die in rot hervorgehoben ist die **DMX-Abfrage** Bereich.  
  
 Wählen Sie **@InputRowset** aus der Dropdownliste aus, öffnen Sie die **ersetzen** Dialogfeld Feld und eine vorhandene Eingabe zu ändern.  
  
 Wählen Sie **Eingabe hinzufügen** So öffnen die **Eingabe hinzufügen** Dialogfeld Feld, und geben Sie eine neue Datenquelle.  
  
 Sie können auch eine vorhandene Eingabe ändern, indem Sie auf die **@InputRowset** verknüpfen, die in DMX-Abfragebereich rot hervorgehoben ist.  
  
 **Ordnen Sie Spalten**  
 Wählen Sie Spalten aus dem Miningmodell aus, und ordnen Sie sie dann Spalten in der externen Datenquelle zu.  
  
 Sie können auch klicken Sie auf den hervorgehobenen  **\<zuordnen >** Link im Bereich DMX-Abfrage.  
  
 **Ausgabe hinzufügen**  
 Klicken Sie auf diese Option, um die Spalten auszuwählen, die als Bestandteil einer Vorhersageabfrage ausgegeben werden sollen.  
  
 Sie können auch klicken Sie auf den hervorgehobenen  **\<Ausgabe hinzufügen >** Link im Bereich DMX-Abfrage.  
  
 **Modellspalten**  
 Listet die Spalten im ausgewählten Miningmodell auf. Mit einem Rautenzeichen neben dem Spaltennamen wird angegeben, dass die Spalte vorhersagbar ist.  
  
 **Eingabespalten**  
 Listet die Spalten aus der externen Datenquelle auf, die als Eingaben hinzugefügt wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
  
  