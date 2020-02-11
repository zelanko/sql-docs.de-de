---
title: Ändern der Sicht der Ablauf Verfolgungs Ergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 860a80dc-bac0-4ef0-bf7f-7a9b430d7aa3
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 780772f7703e4499c13eb9373ccad4252097b536
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089441"
---
# <a name="modify-the-trace-results-view"></a>Ändern der Sicht der Ablaufverfolgungsergebnisse
  In diesem Thema wird beschrieben, wie die Ablaufverfolgungsergebnisse-Sicht einer Sitzung für erweiterte Ereignisse in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] durch die Ausführung der folgenden Aufgaben geändert wird.  
  
1.  [Hinzufügen oder Entfernen von Spalten](#AddRemoveColumns)  
  
2.  [Erstellen, Bearbeiten oder Löschen zusammengeführter Spalten](#ChangeColumns)  
  
3.  [Sortieren der Ergebnisse](#SortResults)  
  
4.  [Gruppieren der Ergebnisse](#GroupResults)  
  
5.  [Aggregieren der Ergebnisse](#AggregateResults)  
  
6.  [Filtern der Ergebnisse](#Filter)  
  
7.  [Textsuche in Spalten](#Search)  
  
8.  [Ändern der Anzeigeeinstellungen](#ChangeDisplay)  
  
##  <a name="AddRemoveColumns"></a>Hinzufügen oder Entfernen von Spalten  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf den Spaltenheader, und wählen Sie dann **Spalten auswählen**aus.  
  
3.  Wählen Sie im Dialogfeld **Spalten auswählen** im Abschnitt **Verfügbare Spalten** die Spaltennamen aus, die Sie hinzufügen möchten, und klicken Sie dann auf den Pfeil nach rechts.  
  
    > [!NOTE]  
    >  Standardmäßig werden die Spalten nach Namen sortiert. Um die Spalten nach Ereignis anzuzeigen, klicken Sie auf **Nach Ereignis anordnen**.  
  
     Um Spalten im Abschnitt **Ausgewählte Spalten** zu entfernen, wählen Sie die Spalten aus, die Sie entfernen möchten, und klicken Sie auf die den Pfeil nach links.  
  
4.  Um im Abschnitt **Ausgewählte Spalten** die Spaltenreihenfolge zu ändern, klicken Sie auf **Nach oben** bzw. **Nach unten** . Sie können nicht mehrere Zeilen gleichzeitig verschieben.  
  
5.  Klicken Sie auf **OK**.  
  
##  <a name="ChangeColumns"></a>Erstellen, bearbeiten oder löschen zusammen geführter Spalten  
  
#### <a name="to-create-merged-columns"></a>So erstellen Sie zusammengeführte Spalten  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf den Spaltenheader, und klicken Sie dann auf **Spalten auswählen**.  
  
3.  Klicken Sie im Dialogfeld **Spalten auswählen** auf **Neu**.  
  
4.  Geben Sie im Dialogfeld **Neue zusammengeführte Spalte** im Feld **Name der zusammengeführten Spalte** einen Namen für die zusammengeführte Spalte ein.  
  
5.  Wählen Sie im Feld **Zusammenzuführende Originalspalten** in der Dropdownliste zwei oder mehr Spalten aus, die zusammengeführt werden sollen.  
  
    > [!NOTE]  
    >  Erweiterte Ereignisse unterstützen nur das Zusammenführen von bis zu fünf Spalten.  
  
6.  Klicken Sie auf **OK**.  
  
#### <a name="to-edit-merged-columns"></a>So bearbeiten Sie zusammengeführte Spalten  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf den Spaltenheader, und klicken Sie dann auf **Spalten auswählen**.  
  
3.  Klicken Sie im Dialogfeld **Spalten auswählen** auf **Bearbeiten**.  
  
4.  Zum Ändern des Namens für die zusammengeführte Spalte geben Sie im Dialogfeld **Neue zusammengeführte Spalte** im Feld **Name der zusammengeführten Spalte** einen neuen Namen ein.  
  
     Um die Spalten zu ändern, die Sie zusammenzuführen möchten, wählen Sie im Feld **Zusammenzuführende Originalspalten** in der Dropdownliste die zusammenzuführenden Spalten aus, und klicken Sie dann auf **OK**.  
  
#### <a name="to-delete-merged-columns"></a>So löschen Sie zusammenzuführende Spalten  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf den Spaltenheader, und klicken Sie dann auf **Spalten auswählen**.  
  
3.  Wählen Sie im Dialogfeld **Spalten auswählen** den Namen der zusammengeführten Spalte aus, die Sie löschen möchten, und klicken Sie dann auf **Löschen**.  
  
##  <a name="SortResults"></a>Sortieren der Ergebnisse  
  
#### <a name="to-sort-the-results-in-ascending-or-descending-order"></a>So sortieren Sie die Ergebnisse in aufsteigender oder absteigender Reihenfolge  
  
-   Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste auf die Schaltfläche **Datenfeed Abbrechen** klicken.  
  
-   Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf die Spaltenüberschrift, nach der die Sortierung erfolgen soll. Klicken Sie auf **Aufsteigend sortieren** oder **Absteigend sortieren** , um die Spalte in aufsteigender bzw. absteigender Reihenfolge zu sortieren.  
  
     Bei gruppierten Spalten werden bei Sortierung der Spalte nur die Daten innerhalb der Gruppe sortiert.  
  
##  <a name="GroupResults"></a>Gruppieren von Ergebnissen  
  
#### <a name="to-group-the-results-by-a-single-column"></a>So gruppieren Sie die Ergebnisse nach einer einzelnen Spalte  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste erweiterte Ereignisse auf die Schaltfläche **Datenfeed Abbrechen** klicken.  
  
2.  Klicken Sie im Fenster für die Ablaufverfolgungsergebnisse mit der rechten Maustaste auf den Spaltenheader, den Sie gruppieren möchten, und klicken Sie dann auf **Nach dieser Spalte gruppieren**.  
  
#### <a name="to-group-the-results-by-multiple-columns"></a>So gruppieren Sie die Ergebnisse nach mehreren Spalten  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste auf die Schaltfläche **Datenfeed Abbrechen** klicken.  
  
2.  Klicken Sie auf der Symbolleiste für erweiterte Ereignisse auf die Schaltfläche **Gruppierung** .  
  
3.  Wählen Sie im Dialogfeld **Gruppierung** im Feld **Verfügbare Spalten** die Spalten aus, die Sie gruppieren möchten, und klicken Sie dann auf den Pfeil nach rechts.  
  
     Um die Gruppierungsreihenfolge zu ändern, klicken Sie im Abschnitt **Spalten gruppiert nach** auf den Pfeil nach links bzw. rechts.  
  
     Um Spalten aus der Gruppierung zu entfernen, wählen Sie in der Liste **Spalten gruppiert nach** die zu entfernenden Spalten aus, und klicken Sie anschließend auf den Pfeil nach links.  
  
4.  Klicken Sie auf **OK**.  
  
##  <a name="AggregateResults"></a>Aggregat Ergebnisse  
 Erweiterte Ereignisse unterstützen fünf Aggregationsfunktionen:  
  
-   SUM  
  
-   Min  
  
-   Max  
  
-   Average  
  
-   Count  
  
 Sum, Min, Max und Average können nur mit verfügbaren numerischen Spalten verwendet werden. Count ist die Anzahl von Werten ungleich NULL, die für die ausgewählte Spalte in der Gruppe vorhanden sind.  
  
#### <a name="to-aggregate-results"></a>So aggregieren Sie Ergebnisse  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken, **Livedaten ansehen**auswählen und dann auf der Symbolleiste auf die Schaltfläche **Datenfeed Abbrechen** klicken.  
  
    > [!NOTE]  
    >  Die Aggregation wird für eine Gruppe ausgeführt, deshalb müssen Sie die Ergebnisse gruppieren, bevor Sie die Aggregation ausführen können.  
  
2.  Klicken Sie auf der Symbolleiste für erweiterte Ereignisse auf die Schaltfläche **Aggregat** .  
  
     Das Dialogfeld **Aggregation** wird mit den für die Aggregation verfügbaren Spalten angezeigt.  
  
3.  Wählen Sie unter **Aggregationstyp**in der Dropdownliste aus, wie Sie die entsprechende Spalte aggregieren möchten.  
  
4.  Wählen Sie im Feld **Aggregation sortieren nach** in der Dropdownliste die Spalte aus, nach der die Sortierung erfolgen soll.  
  
5.  Aktivieren Sie die Option **In aufsteigender Reihenfolge** , um das Aggregationsergebnis in aufsteigender Reihenfolge zu sortieren.  
  
6.  Aktivieren Sie die Option **In absteigender Reihenfolge** , um das Aggregationsergebnis in absteigender Reihenfolge zu sortieren.  
  
7.  Klicken Sie auf **OK**.  
  
##  <a name="Filter"></a>Filter Ergebnisse  
 Sie können Filter auf Ablaufverfolgungsergebnisse anwenden, um die Ablaufverfolgungsergebnisse einzugrenzen, die im Ablaufverfolgungsfenster angezeigt werden. Der Anzeigefilter umfasst einen Zeitfilter und einen erweiterten Filter. Sie filtern mithilfe des Zeitfilters die Ablaufverfolgungsergebnisse nach Ereigniszeitstempel und erstellen mithilfe des erweiterten Filters Filterbedingungen mit Ereignisfeldern und -aktionen. Zwischen Zeit- und erweitertem Filter besteht eine logische UND-Beziehung.  
  
#### <a name="to-create-a-filter"></a>So erstellen Sie einen Filter  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Wählen Sie im Fenster mit den Ablaufverfolgungsergebnissen die Ergebnisse aus, die Sie filtern möchten, und klicken Sie dann auf der Symbolleiste Erweiterte Ereignisse auf die Schaltfläche **Filter** .  
  
3.  Wählen Sie zum Festlegen des Zeitfilters im Dialogfeld **Filter** die Option **Zeitfilter festlegen** aus, und ziehen Sie die Schieberegler, um die Zeitachse festzulegen. Beachten Sie, dass beim Bewegen des Schiebereglers der Zeitwert im Zeitfeld dementsprechend angezeigt wird. Sie können die Zeit auch in den Zeitfeldern eingeben oder in der Dropdownliste auswählen. Wenn Sie die Zeit eingeben, bewegt sich der linke Zeitschieberegler entsprechend.  
  
4.  Wenden Sie im Abschnitt **zusätzliche Filter** die Filterkriterien an, und klicken Sie dann auf **anwenden**. Wenn Sie mit dem Erstellen des Filters fertig sind, klicken Sie auf **OK**.  
  
 Wenn ein Ereignisfeld über den gleichen Namen wie eine Aktion verfügt, liegt ein Sonderfall vor. Ein Beispiel dafür ist session_id. Es gibt mehrere Ereignisse, die ein Feld session_id enthalten, und Sie könnten auch die Aktion session_id hinzufügen. Beide Informationen werden gesammelt, im Anzeigeraster des Profilers für erweiterte Ereignisse wird jedoch folgende Logik angewendet.  
  
-   Nur eine Kopie der Spalte (in diesem Fall session_id) wird in der Rasteranzeige dargestellt.  
  
-   Wenn sowohl Felder als auch eine Aktion in den Daten enthalten sind, wird der Feldwert angezeigt.  
  
-   Wenn nur ein Feld oder eine Aktion in den Daten enthalten ist, wird das Feld oder die Aktion angezeigt.  
  
-   Wenn weder eine Aktion noch ein Feld vorhanden ist, wird NULL angezeigt.  
  
##  <a name="Search"></a>In Spalten nach Text suchen  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Klicken Sie auf der Symbolleiste für erweiterte Ereignisse auf die Schaltfläche **Suchen** .  
  
3.  Geben Sie im Dialogfeld **In erweiterten Ereignissen suchen** im Feld **Suchen nach** den Text ein, nach dem Sie suchen möchten.  
  
     In der Dropdownliste können Sie eine der letzten 20 Suchzeichenfolgen auswählen.  
  
4.  Wählen Sie im Feld **Suchen in** in der Dropdownliste den Speicherort aus, an dem Sie nach dem angegebenen Text suchen möchten. Verwenden Sie zum Suchen die folgenden Optionen:  
  
    -   **Tabellen Spalten**. Verwenden Sie diese Option, um alle sichtbaren Spalten im Ablaufverfolgungsfenster zu durchsuchen.  
  
    -   **Details**. Verwenden Sie diese Option, um alle (höher gestuften und nicht höher gestuften) Spalten im Ablauf Verfolgungs Fenster zu durchsuchen, die vor dem Öffnen des Dialog Felds **in erweiterten Ereignissen suchen** ausgewählt wurden.  
  
    -   **Der Name der Ereignis Spalte>. \< ** Verwenden Sie diese Option, um in einer bestimmten Ereignisspalte aus der Dropdownliste zu suchen.  
  
5.  Verwenden Sie die folgenden Optionen, um anzugeben, wie Sie die Suche definieren möchten:  
  
    1.  **Groß-/Kleinschreibung** Verwenden Sie diese Option, um die Suchergebnisse für den Text anzuzeigen, den Sie im Feld **Suchen** nach eingegeben haben, das sowohl nach Inhalt als auch nach Groß-/Kleinschreibung übereinstimmt.  
  
    2.  Entsprechung für **ganzes Wort**suchen. Verwenden Sie diese Option, um nur die Suchergebnisse für den Text anzuzeigen, die mit vollständigen Wörtern übereinstimmen.  
  
    3.  **Suchen Sie nach oben**. Verwenden Sie diese Option, um ab der Cursorposition zum Anfang der Ergebnisse zu suchen.  
  
    4.  **Verwenden**Sie. Verwenden Sie diese Option, um die Sonderzeichen und die regulären Ausdrücke zu interpretieren, die Sie im Feld **Suchen nach** eingegeben haben. Sonderzeichen zählen die Platzhalterzeichen (*) und (?), mit denen Sie ein oder mehrere Zeichen darstellen. Reguläre Ausdrücke sind besondere Schreibweisen, die verwendet wurden, um Muster im Suchtext zu definieren.  
  
6.  Klicken Sie auf **Weitersuchen** , um nach dem nächsten Vorkommen des Texts zu suchen, den Sie im Feld **Suchen nach** eingegeben haben.  
  
##  <a name="ChangeDisplay"></a>Ändern der Anzeigeeinstellungen  
 Sie können Spalteninformationen (Spaltenreihenfolge, Mergespalte und Spaltenbreite) und Filterinformationen eines Ablaufverfolgungsergebnisses in einer Anzeigeeinstellungsdatei (VIEWSETTING-Datei) für erweiterte Ereignisse speichern. Nach dem Speichern der Datei können Sie sie auf die Ablaufverfolgungsergebnisse anwenden, um die Ansicht zu ändern.  
  
#### <a name="to-change-the-display-settings"></a>So ändern Sie die Anzeigeeinstellungen  
  
1.  Öffnen Sie eine XEL-Datei, um die Ablaufverfolgungsergebnisse anzuzeigen.  
  
    > [!NOTE]  
    >  Sie können auch mit der rechten Maustaste auf den Sitzungs Namen klicken und dann **Livedaten ansehen**auswählen.  
  
2.  Wählen Sie im Fenster mit den Ablaufverfolgungsergebnissen auf der Symbolleiste für erweiterte Ereignisse oder im Menü **Anzeigeeinstellungen**aus.  
  
3.  Wählen Sie eine der folgenden Optionen aus der Dropdownliste aus:  
  
    -   **Speichern**unter. Speichern Sie die Spalten- und Filterinformationen eines Ablaufverfolgungsergebnisses in einer VIEWSETTING-Datei.  
  
    -   **Öffnen**Sie. Öffnen Sie eine vorhandene VIEWSETTING-Datei.  
  
    -   **Zuletzt verwendete öffnen**. Öffnen Sie eine vor kurzem gespeicherte VIEWSETTING-Datei.  
  
  
