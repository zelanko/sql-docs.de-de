---
title: Erstellen von Vorhersagen (Tutorial zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67597533"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a>Erstellen von Vorhersagen (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem Sie die Genauigkeit der Mining Modelle getestet haben und sich entschieden haben, dass Sie mit den Ergebnissen zufrieden sind, können Sie Vorhersagen generieren, indem Sie die Vorhersage Abfrage-Generator auf der Registerkarte **Mining Modellvorhersage** im Data Mining-Designer verwenden.  
  
 Der Generator für Vorhersageabfragen verfügt über drei Sichten. Mit den **Entwurfs** -und **Abfrage** Ansichten können Sie die Abfrage erstellen und untersuchen. Anschließend können Sie die Abfrage ausführen und die Ergebnisse in der **Ergebnis** Ansicht anzeigen.  
  
 Alle Vorhersageabfragen verwenden die DMX-Programmiersprache, die Kurzform für Data Mining Extensions (Data Mining-Erweiterungen). DMX hat eine ähnliche Syntax wie T-SQL, wird jedoch für Abfragen von Data Mining-Objekten verwendet. Obwohl die DMX-Syntax nicht kompliziert ist, wird die Auswahl von Eingaben und buildausdrücken mit einem Abfrage-Generator wie diesem oder dem in den [SQL Server Data Mining-Add-Ins für Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md)erheblich vereinfacht. Daher wird dringend empfohlen, die Grundlagen zu erlernen.  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Der erste Schritt beim Erstellen einer Vorhersageabfrage ist die Auswahl eines Miningmodells und einer Eingabetabelle.  
  
#### <a name="to-select-a-model-and-input-table"></a>So wählen Sie ein Modell und eine Eingabetabelle aus  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Mining Modellvorhersage** im Feld **Mining Modell** auf **Modell auswählen**.  
  
2.  Navigieren Sie im Dialogfeld **Mining Modell auswählen** durch die Struktur zur Ziel- **Mailing** -Struktur, erweitern Sie die Struktur, `TM_Decision_Tree`wählen Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Klicken Sie im Feld **Eingabe Tabelle (n) auswählen** auf **Fall Tabelle auswählen**.  
  
4.  Wählen Sie im Dialogfeld **Tabelle auswählen** in der Liste **Datenquelle** die Datenquellen Sicht [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]aus.  
  
5.  Wählen Sie unter **Tabellen-/Sichtname**die Tabelle **ProspectiveBuyer (dbo)** aus, und klicken Sie dann auf **OK**.  
  
     Die `ProspectiveBuyer` Tabelle ähnelt am ehesten der Fall Tabelle **vTargetMail** .  
  
## <a name="mapping-the-columns"></a>Zuordnen der Spalten  
 Wenn Sie die Eingabetabelle ausgewählt haben, erstellt der Generator für Vorhersageabfragen eine Standardzuordnung zwischen dem Miningmodell und der Eingabetabelle, die auf den Spaltennamen basiert. Mindestens eine Spalte in der Struktur muss mit einer Spalte in den externen Daten übereinstimmen.  
  
> [!IMPORTANT]  
>  Die Daten, die Sie zur Ermittlung der Genauigkeit der Modelle verwenden, müssen eine Spalte enthalten, die der vorhersagbaren Spalte zugeordnet werden kann. Wenn so eine Spalte nicht vorhanden ist, können Sie eine Spalte mit leeren Werten erstellen. Sie muss jedoch den gleichen Datentyp wie die vorhersagbare Spalte aufweisen.  
  
#### <a name="to-map-the-inputs-to-the-model"></a>So ordnen Sie dem Modell die Eingaben zu  
  
1.  Klicken Sie mit der rechten Maustaste auf die Zeilen, die das Fenster **Mining Modell** mit dem Fenster **Eingabe Tabelle auswählen** verbinden, und wählen Sie **Verbindungen ändern**aus.  
  
     Beachten Sie, dass nicht jede Spalte zugeordnet wird. Wir fügen Zuordnungen für mehrere **Tabellen Spalten**hinzu. Wir generieren außerdem eine neue Geburtsdatumsspalte, die auf der aktuellen Datumsspalte basiert, um die Übereinstimmung zwischen den Spalten zu erhöhen.  
  
2.  Klicken Sie unter **Tabellenspalte**auf `Bike Buyer` die Zelle, und wählen Sie ProspectiveBuyer. Unknown aus der Dropdown Liste aus.  
  
     Dies ordnet die vorhersagbare Spalte [Bike Buyer] einer Eingabetabellenspalte zu.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die gewünschte **Mailing** Datenquellen Sicht, und wählen Sie **Ansicht-Designer**aus.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Tabelle ProspectiveBuyer, und wählen Sie **neue benannte Berechnung**aus.  
  
6.  Geben `calcAge`Sie im Dialogfeld **benannte Berechnung erstellen** im Feld **Spaltenname den Namen**ein.  
  
7.  Geben **** Sie als Beschreibung **Age date based on BirthDate**ein.  
  
8.  Geben `DATEDIFF(YYYY,[BirthDate],getdate())` Sie im Feld **Ausdruck** ein, und klicken Sie dann auf **OK**.  
  
     Da die Eingabe Tabelle keine **Alters** Spalte enthält, die der Tabelle im Modell entspricht, können Sie diesen Ausdruck verwenden, um das Kunden Alter anhand der Spalte BirthDate in der Eingabe Tabelle zu berechnen. Da **Age** als die einflussreichste Spalte für die Vorhersage von Fahrrad Käufen identifiziert wurde, muss es sowohl im Modell als auch in der Eingabe Tabelle vorhanden sein.  
  
9. Wählen Sie im Data Mining-Designer die Registerkarte **Mining Modellvorhersage** aus, und öffnen Sie das Fenster **Verbindungen ändern** erneut.  
  
10. Klicken Sie unter **Tabellenspalte**auf die Zelle **Age** , und wählen Sie ProspectiveBuyer. CalcAge aus der Dropdown Liste aus.  
  
    > [!WARNING]  
    >  Wenn die Spalte in der Liste nicht angezeigt wird, müssen Sie u. U. die Definition der im Designer geladenen Datenquellensicht aktualisieren. Wählen Sie hierzu im Menü **Datei** die Option **Alle speichern**aus, und schließen Sie dann das Projekt im Designer, und öffnen Sie es erneut.  
  
11. Klicken Sie auf **OK**.  
  
## <a name="designing-the-prediction-query"></a>Entwerfen der Vorhersage Abfrage  
  
1.  Die erste Schaltfläche auf der Symbolleiste der Registerkarte **Mining Modellvorhersage** ist die Schaltfläche **zur Entwurfs Sicht wechseln/zur Ergebnis Sicht wechseln/zur Abfrage Ansicht wechseln** . Klicken Sie auf der Schaltfläche auf den Pfeil nach unten, und wählen Sie **Entwurf**aus.  
  
2.  Klicken Sie im Raster auf der Registerkarte **Mining Modellvorhersage** auf die Zelle in der ersten leeren Zeile in der Spalte **Quelle** , und wählen Sie dann **Vorhersagefunktion**aus.  
  
3.  Wählen Sie `PredictProbability`in der Zeile **Vorhersagefunktion** in der Spalte **Feld** den Wert aus.  
  
     Geben Sie in der Spalte **Alias** der gleichen Zeile die **Wahrscheinlichkeit für Ergebnis**ein.  
  
4.  Wählen Sie im obigen Fenster **Mining Modell** die Option [Bike Buyer] aus, und ziehen Sie Sie in die Zelle **Kriterium/Argument** .  
  
     Wenn Sie los gehen, [TM_Decision_Tree]. [Bike Buyer] wird in der Zelle " **Kriterium/Argument** " angezeigt.  
  
     Hierdurch wird die Zielspalte für die `PredictProbability`-Funktion angegeben. Weitere Informationen zu Funktionen finden Sie unter [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
5.  Klicken Sie in der Spalte **Quelle** auf die nächste leere Zeile, und wählen Sie dann **TM_Decision_Tree** Mining Modell aus.  
  
6.  Wählen Sie `TM_Decision_Tree` `Bike Buyer`in der Zeile in der Spalte **Feld** den Wert aus.  
  
7.  Geben `=1`Sie `TM_Decision_Tree` in der Zeile in der Spalte **Kriterium/Argument** den Namen ein.  
  
8.  Klicken Sie in der Spalte **Quelle** auf die nächste leere Zeile, und wählen Sie dann **ProspectiveBuyer Table**aus.  
  
9. Wählen Sie `ProspectiveBuyer` in der Zeile in der Spalte **Feld** die Option **ProspectiveBuyerKey**aus.  
  
     Damit wird der Vorhersageabfrage ein eindeutiger Bezeichner hinzugefügt, sodass Sie feststellen können, wer wahrscheinlich ein Fahrrad kaufen wird und wer nicht.  
  
10. Fügen Sie dem Raster fünf weitere Zeilen hinzu. Wählen Sie für jede Zeile **ProspectiveBuyer Table** als **Quelle** aus, und fügen Sie dann die folgenden Spalten in den **Feld** Zellen hinzu:  
  
    -   calcAge  
  
    -   LastName  
  
    -   FirstName  
  
    -   AddressLine1  
  
    -   AddressLine2  
  
 Führen Sie zum Schluss die Abfrage aus, und durchsuchen Sie die Ergebnisse.  
  
 Die **Vorhersage Abfrage-Generator** enthält auch die folgenden Steuerelemente:  
  
-   Kontrollkästchen **anzeigen**  
  
     Ermöglicht das Entfernen von Klauseln aus der Abfrage, ohne sie aus dem Designer zu löschen. Diese Funktion kann bei komplexen Abfragen hilfreich sein, wenn Sie die Syntax beibehalten und keine DMX kopieren und in das Fenster einfügen möchten.  
  
-   **Gruppe**  
  
     Fügt eine öffnende (linke) Klammer am Anfang der ausgewählten Zeile oder eine schließende (rechte) Klammer am Ende der aktuellen Zeile ein.  
  
-   **und/oder**  
  
     Fügt den `AND`-Operator oder `OR`-Operator unmittelbar nach der aktuellen Funktion oder der Spalte ein.  
  
#### <a name="to-run-the-query-and-view-results"></a>So führen Sie die Abfrage aus und zeigen die Ergebnisse an  
  
1.  Wählen Sie auf der Registerkarte **Mining Modellvorhersage** die **Ergebnis** Schaltfläche aus.  
  
2.  Nachdem die Abfrage ausgeführt wurde und die Ergebnisse angezeigt werden, können Sie die Ergebnisse überprüfen.  
  
     Auf der Registerkarte **Mining Modellvorhersage** werden Kontaktinformationen für potenzielle Kunden angezeigt, die wahrscheinlich Fahrrad Käufer sind. Die **Wahrscheinlichkeit der Ergebnis** Spalte gibt die Wahrscheinlichkeit an, dass die Vorhersage richtig ist. Anhand dieser Ergebnisse können Sie entscheiden, welche potenziellen Kunden beim Targeted Mailing angeschrieben werden sollen.  
  
3.  An diesem Punkt können Sie die Ergebnisse speichern. Hierfür stehen drei Möglichkeiten zur Verfügung:  
  
    -   Klicken Sie mit der rechten Maustaste auf eine Daten Zeile in den Ergebnissen, und wählen Sie **Kopieren** aus, um nur diesen Wert (und die Spaltenüberschrift) in der Zwischenablage zu speichern.  
  
    -   Klicken Sie mit der rechten Maustaste auf eine beliebige Zeile in den Ergebnissen, und wählen Sie **Alle kopieren** , um das gesamte Resultset einschließlich der Spaltenüberschriften in die Zwischenablage zu kopieren.  
  
    -   Klicken Sie auf **Abfrageergebnis speichern** , um die Ergebnisse wie folgt direkt in einer Datenbank zu speichern:  
  
        1.  Wählen Sie im Dialogfeld **Ergebnis der Data Mining-Abfrage speichern** eine Datenquelle aus, oder definieren Sie eine neue Datenquelle.  
  
        2.  Geben Sie einen Namen für die Tabelle ein, in die die Abfrageergebnisse eingefügt werden.  
  
        3.  Verwenden Sie die Option zur Datenquellen Sicht **Hinzufügen**, um die Tabelle zu erstellen und zu einer vorhandenen Datenquellen Sicht hinzuzufügen. Dies ist hilfreich, wenn Sie alle verknüpften Tabellen für ein Modell (z. b. Trainingsdaten, Vorhersage Quelldaten und Abfrageergebnisse) in derselben Datenquellen Sicht beibehalten möchten.  
  
        4.  Verwenden Sie die Option über **schreiben, falls vorhanden**, um eine vorhandene Tabelle mit den neuesten Ergebnissen zu aktualisieren.  
  
             Sie müssen die Option verwenden, um die Tabelle zu überschreiben, falls Sie der Vorhersageabfrage Spalten hinzugefügt, die Namen oder Datentypen von Spalten in der Vorhersageabfrage geändert oder ALTER-Anweisungen für die Zieltabelle ausgeführt haben.  
  
             Wenn mehrere Spalten denselben Namen aufweisen (z. b. den standardmäßigen Spaltennamen **Ausdruck**), müssen Sie außerdem einen Alias für die Spalten mit doppelten Namen erstellen, oder es wird ein Fehler ausgelöst, wenn der Designer versucht, die Ergebnisse in SQL Server zu speichern. Dies liegt daran, dass mehrere Spalten unter SQL Server nicht über denselben Namen verfügen dürfen.  
  
             Weitere Informationen finden Sie unter [Dialog Feld "Ergebnisse der Data Mining-Abfrage speichern" &#40;Mining Modell-Vorhersage Ansicht&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Verwenden von Drillthrough für Strukturdaten &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [erstellt eine Vorhersage mithilfe des Generators für Vorhersageabfragen](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
