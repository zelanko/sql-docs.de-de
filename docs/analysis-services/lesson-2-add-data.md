---
title: 'Lektion 2: Hinzufügen von Daten | Microsoft-Dokumentation'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a7c3756e6c8c35472b760d9fa3100b4f40ecfdc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38034679"
---
# <a name="lesson-2-add-data"></a>Lektion 2: Hinzufügen von Daten
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion verwenden Sie den Tabellenimport-Assistenten in SSDT mit der Beispieldatenbank AdventureWorksDW SQL, wählen Sie Daten, Vorschau anzeigen und Filtern Sie die Daten, und klicken Sie dann in den Modellarbeitsbereich zu importieren.  
  
Mit dem Tabellenimport-Assistenten können Sie Daten aus einer Reihe verschiedener relationaler Quellen importieren: Access, SQL, Oracle, Sybase, Informix, DB2, Teradata usw. Die Schritte zum Importieren von Daten aus jeder dieser relationalen Quellen sind sehr ähnlich und mit dem unten beschriebenen Vorgang vergleichbar. Daten können auch mithilfe einer gespeicherten Prozedur ausgewählt werden. Weitere Informationen finden Sie Informationen zum Importieren von Daten und die verschiedenen Typen von Datenquellen, die Sie aus importieren können, finden Sie unter [Datenquellen](../analysis-services/tabular-models/data-sources-ssas-tabular.md).  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 1: Erstellen eines neuen Tabellenmodellprojekts](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Erstellen einer Verbindung  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2014-database"></a>Erstellen Sie eine Verbindung mit einer der AdventureWorksDW2014-Datenbank  
  
1.  Im tabellarischen Modell-Explorer mit der Maustaste **Datenquellen** > **aus Datenquelle importieren**.  
  
    Dadurch wird der Tabellenimport-Assistenten, der Sie durch das Herstellen einer Verbindung mit einer Datenquelle führt. Wenn der Tabellenmodell-Explorer nicht angezeigt wird, doppelklicken klicken Sie auf **Model.bim** in **Projektmappen-Explorer** um das Modell im Designer zu öffnen. 
    
    ![als-tabellarische-lesson2-tme](../analysis-services/media/as-tabular-lesson2-tme.png) 

    Hinweis: Wenn Sie Ihr Modell mit Kompatibilitätsgrad 1400 erstellen, wird Ihnen die neue Daten abrufen-Oberfläche anstelle des Tabellenimport-Assistenten angezeigt. Die Dialogfelder, erscheint ein wenig anders, als die folgenden Schritte aus, aber Sie werden weiterhin in der nachvollziehen können. 
  
2.  In den Tabellenimport-Assistent unter **relationale Datenbanken**, klicken Sie auf **Microsoft SQL Server** > **Weiter**.  
  
3.  Geben Sie auf der Seite **Mit einer Microsoft SQL Server-Datenbank verbinden** in **Anzeigename der Verbindung**Folgendes ein: **Adventure Works-Datenbank aus SQL**.  
  
4.  In **Servernamen**, geben Sie den Namen des Servers, auf dem Sie die Datenbank "AdventureWorksDW" installiert.  
  
5.  In der **Datenbanknamen** die Option **"AdventureWorksDW"**, und klicken Sie dann auf **Weiter**.  
  
    ![als-tabellarische-lesson2-Tiw-name](../analysis-services/media/as-tabular-lesson2-tiw-name.png)
  
6.  Auf der Seite **Identitätswechselinformationen** müssen Sie die Anmeldeinformationen angeben, mit denen Analysis Services eine Verbindung mit der Datenquelle herstellt, wenn Daten importiert und verarbeitet werden. Überprüfen Sie, ob **Bestimmter Windows-Benutzername und bestimmtes Kennwort** ausgewählt ist, geben Sie in den Feldern **Benutzername** und **Kennwort**Ihre Windows-Anmeldeinformationen ein, und klicken Sie anschließend auf **Weiter**.  
  
    > [!NOTE]  
    > Die Verwendung eines Windows-Benutzerkontos und -Kennworts stellt die sicherste Methode für das Herstellen einer Verbindung mit einer Datenquelle dar. Weitere Informationen finden Sie unter [Identitätswechsel](../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
7.  Überprüfen Sie auf der Seite **Auswählen, wie die Daten importiert werden sollen** , ob die Option **Aus einer Liste von Tabellen und Sichten auswählen, um die zu importierenden Daten zu bestimmen** ausgewählt ist. Sie möchten in einer Liste von Tabellen und Sichten eine Auswahl treffen. Klicken Sie daher auf **Weiter** , um eine Liste aller Quelltabellen in der Quelldatenbank anzuzeigen.  
  
8.  Aktivieren Sie auf der Seite **Tabellen und Sichten auswählen** das Kontrollkästchen für die folgenden Tabellen: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**und **FactInternetSales**.  
  
    Klicken Sie**NICHT** auf **Fertig stellen**.  
  
## <a name="FilterData"></a>Filter the table data  
Die DimCustomer-Tabelle, die Sie aus der Beispieldatenbank importieren, enthält eine Teilmenge der Daten aus der ursprünglichen SQL Server Adventure Works-Datenbank. Sie filtern einige mehr Spalten aus der DimCustomer-Tabelle, die nicht benötigt, wenn Sie in das Modell importiert werden. Wenn möglich, sollten Sie Daten herausfiltern, die nicht verwendet werden, um vom Modell verwendeten in-Memory-Speicher zu sparen.  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>So filtern Sie die Tabellendaten vor dem Importieren  
  
1.  Wählen Sie die Zeile für die **DimCustomer** Tabelle, und klicken Sie dann auf **Vorschau & Filter**. Das Fenster **Vorschau der ausgewählten Tabelle** wird geöffnet und enthält alle Spalten in der DimCustomer-Quelltabelle.  
  
2.  Deaktivieren Sie das Kontrollkästchen am Anfang der folgenden Spalten: **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**. 

    ![als tabellarische-lesson2-Tiw-klare](../analysis-services/media/as-tabular-lesson2-tiw-clear.png)
  
    Da die Werte für diese Spalten nicht relevant für die Analyse von Internetverkäufen sind, müssen die Spalten nicht importiert werden. Entfernen nicht erforderlicher Spalten wird Ihr Modell kleiner und effizienter machen.  
  
3.  Überprüfen Sie, ob alle anderen Spalten aktiviert sind, und klicken Sie anschließend auf **OK**.  
  
    Die Wörter **Angewendete Filter** werden nun in der Spalte **Filterdetails** in der Zeile **DimCustomer** angezeigt. Wenn Sie auf diesen Link klicken, sehen Sie eine Textbeschreibung der Filter, die Sie soeben angewendet haben.  
    
    ![als-tabellarische-lesson2-angewendete-Filter](../analysis-services/media/as-tabular-lesson2-applied-filters.png)
    
  
4.  Filtern Sie die verbleibenden Tabellen, indem Sie die Kontrollkästchen für die folgenden Spalten in jeder Tabelle deaktivieren:  
    
    **DimDate**
    
      |Spalte|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |Spalte|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |Spalte|  
      |-----------|  
      |**SpanishProductName**|  
      |**FrenchProductName**|  
      |**FrenchDescription**|  
      |**ChineseDescription**|  
      |**ArabicDescription**|  
      |**HebrewDescription**|  
      |**ThaiDescription**|  
      |**GermanDescription**|  
      |**JapaneseDescription**|  
      |**TurkishDescription**|  
  
    **DimProductCategory**
  
      |Spalte|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |Spalte|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      |Spalte|  
      |------------------|  
      |**OrderDateKey**|  
      |**DueDateKey**|  
      |**ShipDateKey**|   
  
## <a name="Import"></a>Import the selected tables and column data  
Nun, dass Sie in der Vorschau angezeigt und nicht benötigte Daten herausgefiltert haben, können Sie die restlichen Daten importieren, die Sie wünschen. Der Assistent importiert die Tabellendaten zusammen mit allen Beziehungen zwischen Tabellen. Neue Tabellen und Spalten im Modell erstellt werden, und die Sie herausgefilterten Daten werden nicht importiert.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>So importieren Sie ausgewählte Tabellen- und Spaltendaten  
  
1.  Überprüfen Sie Ihre Auswahl. Wenn alles korrekt erscheint, klicken Sie auf **Fertig stellen**.  
  
    Während des Datenimports zeigt der Assistent an, wie viele Zeilen abgerufen wurden. Wenn alle Daten importiert wurden, wird in einer Meldung angezeigt, dass der Import erfolgreich abgeschlossen wurde.  
    
    ![als tabellarische-lesson2-Erfolg](../analysis-services/media/as-tabular-lesson2-success.png) 
  
    > [!TIP]  
    > Klicken Sie zum Anzeigen der Beziehungen, die automatisch zwischen den importierten Tabellen erstellt wurden, in der Zeile **Datenvorbereitung** auf **Details**. 
  
2.  Klicken Sie auf **Schließen**.  
  
    Der Assistent wird geschlossen, und der Modelldesigner zeigt nun Ihre importierten Tabellen. 
  
## <a name="save-your-model-project"></a>Speichern Sie Ihres modellprojekts  
Es ist wichtig, um das Modellprojekt häufig zu speichern.  
  
#### <a name="to-save-the-model-project"></a>So speichern Sie das Modellprojekt  
  
-   Click **Datei** > **Alle speichern**.  
  
## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 3: Markieren als Datumstabelle](../analysis-services/lesson-3-mark-as-date-table.md).

  
  
