---
title: Erstellen von MDX-Abfragen in R mit olapR
description: Erfahren Sie, wie die olapR-Paketbibliothek in SQL Server verwendet wird, um MDX-Abfragen zu schreiben oder eine vorhandene MDX-Abfrage in einem Skript in der Programmiersprache R auszuführen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 05/22/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 107b4cc7c68f1fdf91a685235d336556740547c7
ms.sourcegitcommit: afb02c275b7c79fbd90fac4bfcfd92b00a399019
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91956591"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Erstellen von MDX-Abfragen in R mit olapR
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Das [olapR](/machine-learning-server/r-reference/olapr/olapr)-Paket unterstützt MDX-Abfragen für in SQL Server Analysis Services gehostete Cubes. Sie können eine Abfrage für einen vorhandenen Cube erstellen, Dimensionen und andere Cubeobjekte durchsuchen und vorhandene MDX-Abfragen einfügen, um Daten abzurufen.

In diesem Artikel werden die beiden wichtigsten Verwendungsmöglichkeiten des **olapR**-Pakets beschrieben:

+ [Erstellen einer MDX-Abfrage aus R mithilfe der im olapR-Paket bereitgestellten Konstruktoren](#buildMDX)
+ [Ausführen einer vorhandenen, gültigen MDX-Abfrage mit olapR und einem OLAP-Anbieter](#executeMDX)

Die folgenden Vorgänge werden nicht unterstützt:

+ DAX-Abfragen für ein tabellarisches Modell
+ Erstellung von neuen OLAP-Objekten
+ Rückschreiben von Partitionen, einschließlich Measures oder Summen

## <a name="build-an-mdx-query-from-r"></a><a name="buildMDX"></a> Erstellen einer MDX-Abfrage aus R

1. Definieren Sie eine Verbindungszeichenfolge, die die OLAP-Datenquelle (SSAS-Instanz) und den MSOLAP-Anbieter angibt.

2. Verwenden Sie die Funktion `OlapConnection(connectionString)` , um ein Handle für die MDX-Abfrage zu erstellen und die Verbindungszeichenfolge zu übergeben.

3. Verwenden Sie den `Query()` -Konstruktor zum Instanziieren eines Abfrageobjekts.

4. Verwenden Sie die folgenden Hilfsfunktionen, um weitere Details über die Dimensionen und Measures anzugeben, die in der MDX-Abfrage enthalten sein sollen:

     + `cube()` Geben Sie den Namen der SSAS-Datenbank an. Wenn Sie eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Computernamen und den Instanznamen an. 
     + `columns()` Geben Sie die Namen der zu verwendenden Measures im **ON COLUMNS**-Argument an.
     + `rows()` Geben Sie die Namen der zu verwendenden Measures im **ON ROWS**-Argument an.
     + `slicers()` Geben Sie ein Feld oder Elemente an, das bzw. die als Datenschnitt verwendet werden soll(en). Ein Datenschnitt funktioniert wie ein Filter, der auf alle MDX-Abfragedaten angewendet wird.
     
     + `axis()` Geben Sie den Namen einer in der Abfrage zu verwendenden zusätzlichen Achse an. 
     
         Ein OLAP-Cube kann bis zu 128 Abfrageachsen enthalten. Im Allgemeinen werden die ersten vier Achsen als **Spalten**, **Zeilen**, **Seiten** und **Kapitel** bezeichnet. 
         
         Wenn Ihre Abfrage relativ einfach ist, können Sie die Funktionen `columns`, `rows`usw. verwenden, um Ihre Abfrage zu erstellen. Jedoch können Sie auch die `axis()` -Funktion mit einem Indexwert ungleich null verwenden, um eine MDX-Abfrage mit vielen Qualifizierern zu erstellen oder zusätzliche Dimensionen als Qualifizierer hinzuzufügen.

5. Übergeben Sie das Handle und die fertiggestellte MDX-Abfrage abhängig von der Form der Ergebnisse an eine der folgenden Funktionen: 

  + `executeMD` Gibt ein mehrdimensionales Array zurück
  + `execute2D` Gibt einen zweidimensionalen (tabellarischen) Datenrahmen zurück

## <a name="execute-a-valid-mdx-query-from-r"></a><a name="executeMDX"></a> Ausführen einer gültigen MDX-Abfrage aus R

1. Definieren Sie eine Verbindungszeichenfolge, die die OLAP-Datenquelle (SSAS-Instanz) und den MSOLAP-Anbieter angibt.

2. Verwenden Sie die Funktion `OlapConnection(connectionString)` , um ein Handle für die MDX-Abfrage zu erstellen und die Verbindungszeichenfolge zu übergeben.

3. Definieren Sie eine R-Variable zum Speichern des Texts der MDX-Abfrage.

4. Übergeben Sie das Handle und die Variable, die die MDX-Abfrage enthält, an die Funktionen `executeMD` oder `execute2D`, je nach Form der Ergebnisse.

    + `executeMD` Gibt ein mehrdimensionales Array zurück
    + `execute2D` Gibt einen zweidimensionalen (tabellarischen) Datenrahmen zurück

## <a name="examples"></a>Beispiele

Die folgenden Beispiele basieren auf dem Projekt AdventureWorks Data Mart und Cube, da dieses Projekt in mehreren Versionen, einschließlich Sicherungsdateien, die problemlos in Analysis Services wiederhergestellt werden können, allgemein verfügbar ist. Wenn Sie über keinen vorhandenen Cube verfügen, erhalten Sie einen Beispielcube, indem Sie eine der folgenden Optionen verwenden:

+ Erstellen Sie den Cube, der in diesen Beispielen verwendet wird, indem Sie dem Analysis Services-Tutorial bis zur Lektion 4 folgen: [Erstellen eines OLAP-Cubes](/analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial)

+ Laden Sie einen vorhandenen Cube als Sicherung herunter, und stellen Sie ihn in einer Instanz von Analysis Services wieder her. Diese Site stellt beispielsweise einen vollständig verarbeiteten Cube im ZIP-Format bereit: [Adventure Works Multidimensional Model SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Extrahieren Sie die Datei, und stellen Sie sie dann auf der SSAS-Instanz wieder her. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen](/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) oder [Restore-ASDatabase Cmdlet](/powershell/module/sqlserver/restore-asdatabase).

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
+ Diese Abfrage würde eine Tabelle mit drei Spalten zurückgeben, die eine _Rollup_ -Zusammenfassung der Internetumsätze aus allen Ländern enthält.
+ Die WHERE-Klausel beschreibt die _Slicer-Achse_. In diesem Beispiel verwendet der Datenschnitt ein Element der **Verkaufsgebiet**-Dimension zum Filtern der Abfrage, sodass nur Umsätze aus Australien in Berechnungen verwendet werden.

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

Stellen Sie sicher, dass für eine benannte Instanz alle Zeichen, die in R als Steuerzeichen angesehen werden könnten, mit Escapezeichen versehen werden. Die folgende Verbindungszeichenfolge verweist beispielsweise auf einen Instanz-OLAP01 auf einem Server mit dem Namen ContosoHQ:

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

Wenn Sie Abfragen mithilfe des MDX-Generators in SQL Server Management Studio definieren und die MDX-Zeichenfolge speichern, werden die Achsen beginnend mit 0 nummeriert, wie hier dargestellt: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

Trotzdem können Sie diese Abfrage als vordefinierte MDX-Zeichenfolge ausführen. Um jedoch die gleiche Abfrage mithilfe von R und der `axis()`-Funktion zu erstellen, muss die Nummerierung der Achsen mit 1 zu beginnen.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Durchsuchen von Cubes und ihren Feldern in einer SSAS-Instanz

Sie können die `explore` -Funktion verwenden, um eine Liste der Cubes, Dimensionen oder Elemente zurückzugeben, die zum Erstellen Ihrer Abfrage verwendet werden sollen. Dies ist praktisch, wenn Sie keinen Zugang zu anderen Tools zum Durchsuchen von OLAP haben oder die MDX-Abfrage programmgesteuert erstellen oder ändern möchten.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>So listen Sie die für die angegebene Verbindung verfügbaren Cubes auf

Um alle Cubes oder Perspektiven auf der Instanz anzuzeigen, für die Sie eine Ansichtsberechtigung besitzen, übergeben Sie das Handle als Argument an `explore`.

> [!IMPORTANT]
> Das Endergebnis ist **kein** Cube; WAHR zeigt einfach an, dass die Metadatenoperation erfolgreich war. Bei ungültigen Argumenten wird ein Fehler ausgelöst.

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
|_Date_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>So geben Sie alle Elemente der angegebenen Dimension und Hierarchie zurück

Geben Sie nach dem Definieren der Quelle und dem Erstellen des Handles den Cube, die Dimension und die Hierarchie an, die zurückgegeben werden sollen. Elemente in den Rückgabeergebnisse, denen **->** vorangestellt ist, stellen untergeordnete Elemente des zuvor aufgelisteten Elements dar.

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP; initial catalog=Analysis Services Tutorial"
ocs <- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| Ergebnisse  |
| ----|
| _Accessories_|
|_Bikes_|
|_Clothing_|
|_Komponenten_|
|Montagekomponenten >|
|Montagekomponenten >|


## <a name="see-also"></a>Weitere Informationen

[Verwenden von Daten aus OLAP-Cubes in R](../../machine-learning/r/using-data-from-olap-cubes-in-r.md)