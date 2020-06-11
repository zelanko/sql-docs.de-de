---
title: Erweiterter Data Mining-Abfrage-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90a64369c76e254e509f5f57b1da29ededeed08f
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528196"
---
# <a name="advanced-data-mining-query-editor"></a>Erweiterter Data Mining-Abfrage-Editor
  Die **Data Mining-Abfrage Erweiterter Editor** ist ein Tool, das Sie beim Erstellen von benutzerdefinierten Modellen und Abfragen unterstützt.  
  
 Der Editor enthält eine Reihe von Vorlagen mit klickbaren Links. Klicken Sie einfach auf die einzelnen Links, und verwenden Sie die Dialogfelder, um Objekte oder Werte auszuwählen und komplexe DMX-Anweisungen (Data Mining Extensions) zu erstellen. Sie können zur Textbearbeitungsmodell-Ansicht wechseln, um die DMX-Anweisung manuell zu ändern.  
  
 Um die **Erweiterter Editor Data Mining-Abfrage**zu erhalten, klicken Sie auf **Abfrage** , und klicken Sie dann auf **erweitert**.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **DMX-Abfrage**  
 Hier ist die aktuelle DMX-Anweisung zu sehen.  
  
 Klicken Sie mit der rechten Maustaste in den Bereich, um die aktuelle DMX-Anweisung zu kopieren.  
  
 Sie können auf einen hervorgehobenen Teil der Anweisung klicken, um spezielle Optionen für die jeweilige Klausel aufzurufen. Wenn Sie z. b. eine Ausgabe löschen, hinzufügen oder bearbeiten möchten, klicken Sie mit der rechten Maustaste auf den **\<Output>** Link.  
  
 **Abfrage bearbeiten/Abfrage-Generator**  
 Verwenden Sie diese Schaltfläche, um den Editor zwischen einem Text-Editor zu wechseln, in dem Sie DMX-Anweisungen direkt schreiben können. und die **Abfrage-Generator**, die Sie beim Erstellen einer DMX-Anweisung unterstützt.  
  
> [!NOTE]  
>  **Warnung:** Wenn Sie Ansichten wechseln, bevor die Abfrage ausgeführt wurde, wird eine Meldung mit dem Hinweis angezeigt, dass einige Änderungen verloren gehen können. Wenn die DMX-Anweisung gültig ist, können die **Abfrage-Generator** in vielen Fällen diese Änderungen erfolgreich konvertieren. Wenn Sie jedoch eine besonders komplexe DMX-Anweisung erstellt haben, sollten Sie Ihre Arbeit unbedingt speichern, bevor Sie die Ansicht wechseln.  
  
 **DMX-Vorlagen**  
 Klicken Sie auf diese Option, und wählen Sie aus einer Liste von Vorlagen aus, die DMX-Beispiele enthalten. Die Vorlagen stellen praktisch alle Modell- oder Vorhersageabfragetypen bereit, die Sie benötigen, einschließlich Abfragen, die geschachtelte Tabellen verwenden, und DMX-Anweisungen zur Verwaltung von Modellen. Auch wenn Sie mit der Verwendung von DMX vertraut sind, können Sie mit den Vorlagen u. U. Zeit sparen, weil Sie direkt die richtige Syntax erhalten.  
  
 **Modell auswählen**  
 Klicken Sie auf diese Option, um eine Liste der über die aktuelle Verbindung verfügbaren Data Mining-Modelle anzuzeigen.  
  
 Sie können auch eine Liste der verfügbaren Modelle anzeigen, indem Sie im **DMX-Abfrage** Bereich in der DMX-Anweisung auf den Modellnamen klicken. Der Modellname ist in der Regel rot hervorgehoben.  
  
 **Auswählen der Eingabe**  
 Klicken Sie auf diese Option, um die Daten auszuwählen, die als Eingabe für das Miningmodell verwendet werden sollen. Wenn keine Datenquelle angegeben wurde, können Sie auch auf den **\<Input>** Link klicken, der im Bereich **DMX-Abfrage** rot hervorgehoben ist.  
  
 Wählen Sie in der Dropdown Liste ** \@ InputRowset** aus, um das Dialogfeld **InputRowset ersetzen** zu öffnen und eine vorhandene Eingabe zu ändern.  
  
 Wählen Sie **Eingabe hinzufügen** aus, um das Dialogfeld **Eingabe hinzufügen** zu öffnen und eine neue Datenquelle anzugeben.  
  
 Sie können eine vorhandene Eingabe auch ändern, indem Sie auf den Link ** \@ InputRowset** klicken, der im Bereich DMX-Abfrage rot hervorgehoben ist.  
  
 **Spalten zuordnen**  
 Wählen Sie Spalten aus dem Miningmodell aus, und ordnen Sie sie dann Spalten in der externen Datenquelle zu.  
  
 Sie können auch auf den markierten **\<Mapping>** Link im DMX-Abfrage Bereich klicken.  
  
 **Ausgabe hinzufügen**  
 Klicken Sie auf diese Option, um die Spalten auszuwählen, die als Bestandteil einer Vorhersageabfrage ausgegeben werden sollen.  
  
 Sie können auch auf den markierten **\<Add Output>** Link im DMX-Abfrage Bereich klicken.  
  
 **Modellspalten**  
 Listet die Spalten im ausgewählten Miningmodell auf. Mit einem Rautenzeichen neben dem Spaltennamen wird angegeben, dass die Spalte vorhersagbar ist.  
  
 **Eingabespalten**  
 Listet die Spalten aus der externen Datenquelle auf, die als Eingaben hinzugefügt wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
  
  
