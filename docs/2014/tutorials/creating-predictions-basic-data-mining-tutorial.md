---
title: Erstellen von Vorhersagen (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
caps.latest.revision: 42
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 64045eb4a87794e3d4b870ddb3ede28e48af2ce2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267966"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a>Erstellen von Vorhersagen (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem Sie entschieden, dass Sie mit den Ergebnissen zufrieden sind und die Genauigkeit Ihrer Miningmodelle getestet haben, können Sie Sie vorhersagen erzeugen, mit dem Generator für Vorhersageabfragen auf die **Miningmodellvorhersage** Registerkarte im Data Mining Designer.  
  
 Der Generator für Vorhersageabfragen verfügt über drei Sichten. Mit der **Entwurf** und **Abfrage** Ansichten können Sie erstellen und überprüfen Sie Ihre Abfrage. Sie können dann führen Sie die Abfrage und Anzeigen der Ergebnisse in die **Ergebnis** anzeigen.  
  
 Alle Vorhersageabfragen verwenden die DMX-Programmiersprache, die Kurzform für Data Mining Extensions (Data Mining-Erweiterungen). DMX hat eine ähnliche Syntax wie T-SQL, wird jedoch für Abfragen von Data Mining-Objekten verwendet. Obwohl DMX-Syntax nicht kompliziert ist, verwenden Sie einen Abfrage-Generator wie diesem oder in der [SQL Server Data Mining-Add-Ins für Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), ist es einfacher, auswählen von Eingaben, und Erstellen von Ausdrücken, daher wird dringend empfohlen, Sie erfahren, die Grundlagen.  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Der erste Schritt beim Erstellen einer Vorhersageabfrage ist die Auswahl eines Miningmodells und einer Eingabetabelle.  
  
#### <a name="to-select-a-model-and-input-table"></a>So wählen Sie ein Modell und eine Eingabetabelle aus  
  
1.  Auf der **Miningmodellvorhersage** -Registerkarte des Data Mining-Designers in der **Miningmodell** auf **Modell auswählen**.  
  
2.  In der **Miningmodell auswählen** Dialogfeld navigieren Sie zur Struktur der **Targeted Mailing** , erweitern Sie die Struktur, wählen `TM_Decision_Tree`, und klicken Sie dann auf **OK**.  
  
3.  In der **Eingabetabelle(n)** auf **Falltabelle auswählen**.  
  
4.  In der **Tabelle auswählen** Dialogfeld die **Datenquelle** wählen Sie die Datenquellensicht [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].  
  
5.  In **Tabellen-/Sichtname**, wählen die **ProspectiveBuyer (Dbo)** Tabelle, und klicken Sie dann auf **OK**.  
  
     Die `ProspectiveBuyer` Tabelle am ehesten entspricht der **vTargetMail** Falltabelle.  
  
## <a name="mapping-the-columns"></a>Zuordnen der Spalten  
 Wenn Sie die Eingabetabelle ausgewählt haben, erstellt der Generator für Vorhersageabfragen eine Standardzuordnung zwischen dem Miningmodell und der Eingabetabelle, die auf den Spaltennamen basiert. Mindestens eine Spalte in der Struktur muss mit einer Spalte in den externen Daten übereinstimmen.  
  
> [!IMPORTANT]  
>  Die Daten, die Sie zur Ermittlung der Genauigkeit der Modelle verwenden, müssen eine Spalte enthalten, die der vorhersagbaren Spalte zugeordnet werden kann. Wenn so eine Spalte nicht vorhanden ist, können Sie eine Spalte mit leeren Werten erstellen. Sie muss jedoch den gleichen Datentyp wie die vorhersagbare Spalte aufweisen.  
  
#### <a name="to-map-the-inputs-to-the-model"></a>So ordnen Sie dem Modell die Eingaben zu  
  
1.  Mit der rechten Maustaste Verbindungslinien zwischen den **Miningmodell** Fenster aus, um die **Eingabetabelle(n) auswählen** , und wählen **Verbindungen ändern**.  
  
     Beachten Sie, dass nicht jede Spalte zugeordnet wird. Wir werden die Zuordnungen hinzufügen, für mehrere **Tabellenspalten**. Wir generieren außerdem eine neue Geburtsdatumsspalte, die auf der aktuellen Datumsspalte basiert, um die Übereinstimmung zwischen den Spalten zu erhöhen.  
  
2.  Klicken Sie unter **Tabellenspalte**, klicken Sie auf die `Bike Buyer` Zelle, und wählen Sie aus der Dropdownliste ProspectiveBuyer.Unknown.  
  
     Dies ordnet die vorhersagbare Spalte [Bike Buyer] einer Eingabetabellenspalte zu.  
  
3.  Klicken Sie auf **OK**.  
  
4.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **Targeted Mailing** Datenquellensicht und wählen Sie **Ansicht-Designer**.  
  
5.  Mit der rechten Maustaste in der Tabelle ProspectiveBuyer, und wählen Sie **neue benannte Berechnung**.  
  
6.  In der **benannte Berechnung erstellen** im Dialogfeld für **Spaltenname**, Typ `calcAge`.  
  
7.  Für **Beschreibung**, Typ **Berechnen des Alters basierend auf "BirthDate"**.  
  
8.  In der **Ausdruck** geben `DATEDIFF(YYYY,[BirthDate],getdate())` , und klicken Sie dann auf **OK**.  
  
     Da in die Eingabetabelle keine **Alter** Spalte im Modell entspricht Sie können diesen Ausdruck kundenalter auf Grundlage der Spalte "BirthDate" in der Eingabetabelle berechnen. Da **Alter** als die meisten fahrradkäufen identifiziert wurde Spalte für den Kauf eines Fahrrads, müssen sie sowohl im Modell und in der Eingabetabelle vorhanden.  
  
9. Wählen Sie im Data Mining-Designer die **Miningmodellvorhersage** Registerkarte, und öffnen Sie erneut die **Verbindungen ändern** Fenster.  
  
10. Klicken Sie unter **Tabellenspalte**, klicken Sie auf die **Alter** Zelle, und wählen Sie aus der Dropdownliste ProspectiveBuyer.calcAge.  
  
    > [!WARNING]  
    >  Wenn die Spalte in der Liste nicht angezeigt wird, müssen Sie u. U. die Definition der im Designer geladenen Datenquellensicht aktualisieren. Zu diesem Zweck, von der **Datei** , wählen Sie im Menü **alle speichern**, und klicken Sie dann das Schließen und öffnen Sie das Projekt in den Designer erneut.  
  
11. Klicken Sie auf **OK**.  
  
## <a name="designing-the-prediction-query"></a>Entwerfen die Vorhersageabfrage  
  
1.  Die erste Schaltfläche auf der Symbolleiste des der **Miningmodellvorhersage** Registerkarte ist die **zur Entwurfssicht abfrageentwurfssicht wechseln / zur ergebnissicht wechseln / zur Abfragesicht** Schaltfläche. Klicken Sie auf den Pfeil nach unten, klicken Sie auf diese Schaltfläche, und wählen **Entwurf**.  
  
2.  Im Raster auf die **Miningmodellvorhersage** Registerkarte, klicken Sie auf die Zelle in der ersten leeren Zeile in der **Quelle** Spalte, und wählen Sie dann **Vorhersagefunktion**.  
  
3.  In der **Vorhersagefunktion** -Zeile in der **Feld** Spalte `PredictProbability`.  
  
     In der **Alias** Spalte mit der gleichen Zeile Typ **Wahrscheinlichkeit des Ergebnisses**.  
  
4.  Von der **Miningmodell** oben im Fenster auswählen, und ziehen Sie [Bike Buyer] in der **Kriterium/Argument** Zelle.  
  
     Wenn Sie die Maustaste loslassen, [TM_Decision_Tree]. [Bike Buyer] angezeigt wird, der **Kriterium/Argument** Zelle.  
  
     Hierdurch wird die Zielspalte für die `PredictProbability`-Funktion angegeben. Weitere Informationen zu Funktionen finden Sie unter [Data Mining-Erweiterungen &#40;DMX&#41; Funktionsverweis](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
5.  Klicken Sie auf die nächste leere Zeile in der **Quelle** Spalte und wählen Sie dann TM_Decision_Tree Miningmodell **.**  
  
6.  In der `TM_Decision_Tree` -Zeile in der **Feld** Spalte `Bike Buyer`.  
  
7.  In der `TM_Decision_Tree` -Zeile in der **Kriterium/Argument** Spalte, Datentyp `=1`.  
  
8.  Klicken Sie auf die nächste leere Zeile in der **Quelle** Spalte, und wählen Sie dann **ProspectiveBuyer-Tabelle**.  
  
9. In der `ProspectiveBuyer` -Zeile in der **Feld** Spalte **ProspectiveBuyerKey**.  
  
     Damit wird der Vorhersageabfrage ein eindeutiger Bezeichner hinzugefügt, sodass Sie feststellen können, wer wahrscheinlich ein Fahrrad kaufen wird und wer nicht.  
  
10. Fügen Sie dem Raster fünf weitere Zeilen hinzu. Wählen Sie für jede Zeile **ProspectiveBuyer-Tabelle** als die **Quelle** und fügen Sie die folgenden Spalten in der **Feld** Zellen:  
  
    -   calcAge  
  
    -   LastName  
  
    -   FirstName  
  
    -   AddressLine1  
  
    -   AddressLine2  
  
 Führen Sie zum Schluss die Abfrage aus, und durchsuchen Sie die Ergebnisse.  
  
 Die **Generator für Vorhersageabfragen** umfasst zusätzlich folgende Steuerelemente:  
  
-   **Anzeigen** Kontrollkästchen  
  
     Ermöglicht das Entfernen von Klauseln aus der Abfrage, ohne sie aus dem Designer zu löschen. Diese Funktion kann bei komplexen Abfragen hilfreich sein, wenn Sie die Syntax beibehalten und keine DMX kopieren und in das Fenster einfügen möchten.  
  
-   **Gruppieren**  
  
     Fügt eine öffnende (linke) Klammer am Anfang der ausgewählten Zeile oder eine schließende (rechte) Klammer am Ende der aktuellen Zeile ein.  
  
-   **UND/ODER**  
  
     Fügt den `AND`-Operator oder `OR`-Operator unmittelbar nach der aktuellen Funktion oder der Spalte ein.  
  
#### <a name="to-run-the-query-and-view-results"></a>So führen Sie die Abfrage aus und zeigen die Ergebnisse an  
  
1.  In der **Miningmodellvorhersage** Registerkarte die **Ergebnis** Schaltfläche.  
  
2.  Nachdem die Abfrage ausgeführt wurde und die Ergebnisse angezeigt werden, können Sie die Ergebnisse überprüfen.  
  
     Die **Miningmodellvorhersage** Registerkarte zeigt Kontaktinformationen für potenzielle Kunden, die wahrscheinlich ein Fahrrad kaufen werden. Die **Wahrscheinlichkeit des Ergebnisses** Spalte gibt an, die Wahrscheinlichkeit die Vorhersage zutrifft. Anhand dieser Ergebnisse können Sie entscheiden, welche potenziellen Kunden beim Targeted Mailing angeschrieben werden sollen.  
  
3.  An diesem Punkt können Sie die Ergebnisse speichern. Hierfür stehen drei Möglichkeiten zur Verfügung:  
  
    -   Mit der rechten Maustaste einer Zeile mit Daten in den Ergebnissen, und wählen **Kopie** nur für diesen Wert (und die Spaltenüberschrift) in die Zwischenablage zu speichern.  
  
    -   Mit der rechten Maustaste in eine beliebige Zeile in den Ergebnissen, und wählen **Alles kopieren** um das gesamte Resultset, einschließlich Spaltenüberschriften, in die Zwischenablage zu kopieren.  
  
    -   Klicken Sie auf **Abfrageergebnis speichern** zum Speichern der Ergebnisse direkt in einer Datenbank wie folgt:  
  
        1.  In der **speichern Abfrageergebnis der Data Mining** im Dialogfeld Wählen Sie eine Datenquelle oder eine neue Datenquelle zu definieren.  
  
        2.  Geben Sie einen Namen für die Tabelle ein, in die die Abfrageergebnisse eingefügt werden.  
  
        3.  Verwenden Sie die Option **zur Datenquellensicht hinzufügen**, um eine Tabelle erstellen, und fügen Sie es einer vorhandenen Datenquellensicht hinzu. Diese Option ist nützlich, wenn Sie alle verknüpften Tabellen für ein Modell – z. B. Trainingsdaten, Vorhersagequelldaten und Abfrageergebnisse – in der gleichen Datenquellensicht beibehalten möchten.  
  
        4.  Verwenden Sie die Option **überschreiben, falls vorhanden**, um eine vorhandene Tabelle mit den neuesten Ergebnissen zu aktualisieren.  
  
             Sie müssen die Option verwenden, um die Tabelle zu überschreiben, falls Sie der Vorhersageabfrage Spalten hinzugefügt, die Namen oder Datentypen von Spalten in der Vorhersageabfrage geändert oder ALTER-Anweisungen für die Zieltabelle ausgeführt haben.  
  
             Auch wenn mehrere Spalten den gleichen Namen (z. B. den Standardspaltennamen **Ausdruck**) müssen Sie einen Alias für die Spalten mit doppelten Namen erstellen, oder es wird ein Fehler ausgelöst werden, wenn der Designer versucht wird, um die Ergebnisse in SQL zu speichern Server. Dies liegt daran, dass mehrere Spalten unter SQL Server nicht über denselben Namen verfügen dürfen.  
  
             Weitere Informationen finden Sie unter [Data Mining-Abfrage Ergebnis im Dialogfeld Speichern &#40;Miningmodellvorhersage-Ansicht&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Verwenden von Drillthrough für Strukturdaten &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Vorhersageabfragen mithilfe des Generators für Vorhersageabfragen](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
