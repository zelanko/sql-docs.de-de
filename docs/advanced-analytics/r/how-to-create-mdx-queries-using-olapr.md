---
title: Erstellen von MDX-Abfragen in R mithilfe von olapr
description: Verwenden Sie die olapr-paketbibliothek in SQL Server, um MDX-Abfragen in R-sprach Skripts zu schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2d3b9df3e99abe3a443dd0fa9b66921a0e9a4506
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345566"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Erstellen von MDX-Abfragen in R mithilfe von olapr
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Das [olapr](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) -Paket unterstützt MDX-Abfragen für in SQL Server Analysis Services gehostete Cubes. Sie können eine Abfrage für einen vorhandenen Cube erstellen, Dimensionen und andere Cubeobjekte durchsuchen und vorhandene MDX-Abfragen einfügen, um Daten abzurufen.

In diesem Artikel werden die beiden Haupt Verwendungsmöglichkeiten des **olapr** -Pakets beschrieben:

+ [Erstellen einer MDX-Abfrage aus R mithilfe der im olapr-Paket bereitgestellten Konstruktoren](#buildMDX)
+ [Ausführen einer vorhandenen, gültigen MDX-Abfrage mit olapr und einem OLAP-Anbieter](#executeMDX)

Die folgenden Vorgänge werden nicht unterstützt:

+ DAX-Abfragen für ein tabellarisches Modell
+ Erstellung von neuen OLAP-Objekten
+ Rück Schreiben von Partitionen, einschließlich Measures oder Summen

## <a name="buildMDX"></a>Erstellen einer MDX-Abfrage aus R

1. Definieren Sie eine Verbindungszeichenfolge, die die OLAP-Datenquelle (SSAS-Instanz) und den MSOLAP-Anbieter angibt.

2. Verwenden Sie die Funktion `OlapConnection(connectionString)` , um ein Handle für die MDX-Abfrage zu erstellen und die Verbindungszeichenfolge zu übergeben.

3. Verwenden Sie den `Query()` -Konstruktor zum Instanziieren eines Abfrageobjekts.

4. Verwenden Sie die folgenden Hilfsfunktionen, um weitere Details über die Dimensionen und Measures anzugeben, die in der MDX-Abfrage enthalten sein sollen:

     + `cube()` Geben Sie den Namen der SSAS-Datenbank an. Wenn Sie eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Computernamen und den Instanznamen an. 
     + `columns()`Geben Sie die Namen der Measures an, die im **on Columns** -Argument verwendet werden sollen.
     + `rows()`Geben Sie die Namen der Measures an, die im **on Rows** -Argument verwendet werden sollen.
     + `slicers()` Geben Sie ein Feld oder Elemente an, das bzw. die als Datenschnitt verwendet werden soll(en). Ein Datenschnitt funktioniert wie ein Filter, der auf alle MDX-Abfragedaten angewendet wird.
     
     + `axis()` Geben Sie den Namen einer in der Abfrage zu verwendenden zusätzlichen Achse an. 
     
         Ein OLAP-Cube kann bis zu 128 Abfrageachsen enthalten. Im Allgemeinen werden die ersten vier Achsen als **Spalten**, **Zeilen**, **Seiten**und **Kapitel**bezeichnet. 
         
         Wenn Ihre Abfrage relativ einfach ist, können Sie die Funktionen `columns`, `rows`usw. verwenden, um Ihre Abfrage zu erstellen. Jedoch können Sie auch die `axis()` -Funktion mit einem Indexwert ungleich null verwenden, um eine MDX-Abfrage mit vielen Qualifizierern zu erstellen oder zusätzliche Dimensionen als Qualifizierer hinzuzufügen.

5. Übergeben Sie das Handle und die abgeschlossene MDX-Abfrage abhängig von der Form der Ergebnisse in eine der folgenden Funktionen: 

  + `executeMD` Gibt ein mehrdimensionales Array zurück
  + `execute2D` Gibt einen zweidimensionalen (tabellarischen) Datenrahmen zurück

## <a name="executeMDX"></a>Ausführen einer gültigen MDX-Abfrage aus R

1. Definieren Sie eine Verbindungszeichenfolge, die die OLAP-Datenquelle (SSAS-Instanz) und den MSOLAP-Anbieter angibt.

2. Verwenden Sie die Funktion `OlapConnection(connectionString)` , um ein Handle für die MDX-Abfrage zu erstellen und die Verbindungszeichenfolge zu übergeben.

3. Definieren Sie eine R-Variable zum Speichern des Texts der MDX-Abfrage.

4. Übergeben Sie das Handle und die Variable, die die MDX-Abfrage enthält, an die Funktionen `executeMD` oder `execute2D`, je nach Form der Ergebnisse.

    + `executeMD` Gibt ein mehrdimensionales Array zurück
    + `execute2D` Gibt einen zweidimensionalen (tabellarischen) Datenrahmen zurück

## <a name="examples"></a>Beispiele

Die folgenden Beispiele basieren auf dem Projekt AdventureWorks Data Mart und Cube, da dieses Projekt in mehreren Versionen, einschließlich Sicherungsdateien, die problemlos in Analysis Services wieder hergestellt werden können, allgemein verfügbar ist. Wenn Sie über keinen vorhandenen Cube verfügen, erhalten Sie einen Beispielcube, indem Sie eine der folgenden Optionen verwenden:

+ Erstellen Sie den Cube, der in diesen Beispielen verwendet wird, indem Sie das Analysis Services Tutorial bis zu Lektion 4 befolgen: [Erstellen eines OLAP-Cubes](../../analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial.md)

+ Laden Sie einen vorhandenen Cube als Sicherung herunter, und stellen Sie ihn in einer Instanz von Analysis Services wieder her. Diese Site stellt z. b. einen vollständig verarbeiteten Cube im ZIP-Format bereit: [Adventure Works mehrdimensionales Modell SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Extrahieren Sie die Datei, und stellen Sie Sie dann auf der SSAS-Instanz wieder her. Weitere Informationen finden Sie unter [Backup und Restore](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)oder [Restore-asdatabase-Cmdlet](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

### <a name="1-basic-mdx-with-slicer"></a>1. Einfache MDX mit Datenschnitt

Diese MDX-Abfrage wählt die _Measures_ für die Anzahl und den Betrag von Internetumsätzen aus und platziert sie auf der Spaltenachse. Sie fügt ein Mitglied der Dimension „Verkaufsgebiet“ als *Datenschnitt*hinzu, um die Abfrage so zu filtern, dass nur Umsätze aus Australien in Berechnungen verwendet werden.

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ In Spalten können Sie mehrere Measures als Elemente einer durch Trennzeichen getrennten Zeichenfolge angeben.
+ Die Zeilenachse verwendet alle möglichen Werte (alle ELEMENTE) der Dimension „Produktlinie“. 
+ Diese Abfrage gibt eine Tabelle mit drei Spalten zurück, die eine  rollupzusammenfassung der Internet Verkäufe aus allen Ländern enthält.
+ Die WHERE-Klausel gibt die _Slicerachse_an. In diesem Beispiel verwendet der Slicer einen Member der **SalesTerritory** -Dimension, um die Abfrage so zu filtern, dass nur die Verkäufe aus Australien in Berechnungen verwendet werden.

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>So erstellen Sie diese Abfrage mithilfe der in olapR bereitgestellten Funktionen

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

Stellen Sie für eine benannte Instanz sicher, dass alle Zeichen, die in R als Steuerzeichen angesehen werden könnten, mit Escapezeichen versehen werden  Die folgende Verbindungs Zeichenfolge verweist z. b. auf einen Instanz-OLAP01 auf einem Server mit dem Namen condesohq:

```R
cnnstr <- "Data Source=ContosoHQ\\OLAP01; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>So führen Sie diese Abfrage als vordefinierte MDX-Zeichenfolge aus

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

Wenn Sie eine Abfrage mit dem MDX-Generator in SQL Server Management Studio definieren und dann die MDX-Zeichenfolge speichern, werden die Achsen beginnend mit 0 (wie hier gezeigt) aufgelistet: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

Trotzdem können Sie diese Abfrage als vordefinierte MDX-Zeichenfolge ausführen. Wenn Sie jedoch dieselbe Abfrage mithilfe von R mithilfe der `axis()` -Funktion erstellen möchten, müssen Sie die Achsen beginnend bei 1 umgestalten.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Durchsuchen von Cubes und ihren Feldern in einer SSAS-Instanz

Sie können die `explore`-Funktion verwenden, um eine Liste der Cubes, Dimensionen oder Elemente zurückzugeben, die zum Erstellen Ihrer Abfrage verwendet werden sollen. Dies ist praktisch, wenn Sie keinen Zugang zu anderen Tools zum Durchsuchen von OLAP haben oder die MDX-Abfrage programmgesteuert erstellen oder ändern möchten.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>So listen Sie die für die angegebene Verbindung verfügbaren Cubes auf

Um alle Cubes oder Perspektiven auf der Instanz anzuzeigen, für die Sie eine Ansichtsberechtigung besitzen, übergeben Sie das Handle als Argument an `explore`.

> [!IMPORTANT]
> Das Endergebnis ist **kein** Cube. TRUE gibt lediglich an, dass der Metadatenvorgang erfolgreich war. Bei ungültigen Argumenten wird ein Fehler ausgelöst.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs)
```

| Ergebnisse  |
| ----|
| _Analysis Services-Tutorial_|
|_Internetumsätze_|
|_Umsätze der Wiederverkäufer_|
|_Umsatzzusammenfassung_|
|_[1] WAHR_|

#### <a name="to-get-a-list-of-cube-dimensions"></a>So rufen Sie eine Liste der Cubedimensionen ab

Um alle Dimensionen im Cube oder der Perspektive anzuzeigen, geben Sie den Namen des Cubes oder der Perspektive an.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| Ergebnisse  |
| ----|
| _Kunde_|
|_Datum_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>So geben Sie alle Elemente der angegebenen Dimension und Hierarchie zurück

Geben Sie nach dem Definieren der Quelle und dem Erstellen des Handles den Cube, die Dimension und die Hierarchie an, die zurückgegeben werden sollen. In den Rückgabe Ergebnissen stellen Elemente, die mit **->** dem Präfix versehen sind, untergeordnete Elemente des vorherigen Members dar.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| Ergebnisse  |
| ----|
| _Zubehör_|
|_Fahrräder_|
|_Bekleidung_|
|_Komponenten_|
|Montagekomponenten >|
|Montagekomponenten >|


## <a name="see-also"></a>Siehe auch

[Verwenden von Daten aus OLAP-Cubes in R](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
