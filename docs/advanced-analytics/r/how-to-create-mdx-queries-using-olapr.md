---
title: 'Vorgehensweise: Erstellen von MDX-Abfragen in R mit OlapR – SQL Server Machine Learning Services'
description: Verwenden Sie die OlapR-Paket-Bibliothek in SQL Server, um MDX-Abfragen in der Sprache R-Skript zu schreiben.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: dfae657f6ab7d8f0cefbdec729e6e836c4f7e4d8
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175277"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>Vorgehensweise: Erstellen von MDX-Abfragen in R mit olapR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die [OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) Paket unterstützt die MDX-Abfragen für Cubes in SQL Server Analysis Services gehostet. Sie können eine Abfrage für einen vorhandenen Cube zu erstellen, Durchsuchen von Dimensionen und andere Cubeobjekte und fügen Sie in vorhandene MDX-Abfragen zum Abrufen von Daten.

In diesem Artikel wird beschrieben, die zwei wichtigsten Einsatzzwecke von der **OlapR** Paket:

+ [Erstellen Sie eine MDX-Abfrage aus R, die mit den Konstruktoren, die im Paket OlapR bereitgestellten](#buildMDX)
+ [Führen Sie eine gültige MDX-Abfrage, die mit OlapR und OLAP-Anbieter](#executeMDX)

Die folgenden Vorgänge werden nicht unterstützt:

+ DAX-Abfragen für ein tabellarisches Modell
+ Erstellen von neuen OLAP-Objekten
+ Rückschreiben von Daten in Partitionen, einschließlich Measures oder Summen

## <a name="buildMDX"></a> Erstellen Sie eine MDX-Abfrage aus R

1. Definieren Sie eine Verbindungszeichenfolge, die die OLAP-Datenquelle (SSAS-Instanz) und den MSOLAP-Anbieter angibt.

2. Verwenden Sie die Funktion `OlapConnection(connectionString)` , um ein Handle für die MDX-Abfrage zu erstellen und die Verbindungszeichenfolge zu übergeben.

3. Verwenden Sie den `Query()` -Konstruktor zum Instanziieren eines Abfrageobjekts.

4. Verwenden Sie die folgenden Hilfsfunktionen, um weitere Details über die Dimensionen und Measures anzugeben, die in der MDX-Abfrage enthalten sein sollen:

     + `cube()` Geben Sie den Namen der SSAS-Datenbank an. Wenn eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Computernamen und den Instanznamen an. 
     + `columns()` Geben Sie die Namen der Measures für die Verwendung in der **ON COLUMNS** Argument.
     + `rows()` Geben Sie die Namen der Measures für die Verwendung in der **ON ROWS** Argument.
     + `slicers()` Geben Sie ein Feld oder Elemente an, das bzw. die als Datenschnitt verwendet werden soll(en). Ein Datenschnitt funktioniert wie ein Filter, der auf alle MDX-Abfragedaten angewendet wird.
     
     + `axis()` Geben Sie den Namen einer in der Abfrage zu verwendenden zusätzlichen Achse an. 
     
         Ein OLAP-Cube kann bis zu 128 Abfrageachsen enthalten. In der Regel die ersten vier Achsen als bezeichnet **Spalten**, **Zeilen**, **Seiten**, und **Kapiteln**. 
         
         Wenn Ihre Abfrage relativ einfach ist, können Sie die Funktionen `columns`, `rows`usw. verwenden, um Ihre Abfrage zu erstellen. Jedoch können Sie auch die `axis()` -Funktion mit einem Indexwert ungleich null verwenden, um eine MDX-Abfrage mit vielen Qualifizierern zu erstellen oder zusätzliche Dimensionen als Qualifizierer hinzuzufügen.

5. Übergeben Sie das Handle und die abgeschlossene MDX-Abfrage in eine der folgenden Funktionen, abhängig von der Form der Ergebnisse: 

  + `executeMD` Gibt ein mehrdimensionales Array zurück
  + `execute2D` Gibt einen zweidimensionalen (tabellarischen) Datenrahmen zurück

## <a name="executeMDX"></a> Führen Sie eine gültige MDX-Abfrage aus R

1. Definieren Sie eine Verbindungszeichenfolge, die die OLAP-Datenquelle (SSAS-Instanz) und den MSOLAP-Anbieter angibt.

2. Verwenden Sie die Funktion `OlapConnection(connectionString)` , um ein Handle für die MDX-Abfrage zu erstellen und die Verbindungszeichenfolge zu übergeben.

3. Definieren Sie eine R-Variable zum Speichern des Texts der MDX-Abfrage.

4. Übergeben Sie das Handle und die Variable, die die MDX-Abfrage enthält, an die Funktionen `executeMD` oder `execute2D`, je nach Form der Ergebnisse.

    + `executeMD` Gibt ein mehrdimensionales Array zurück
    + `execute2D` Gibt einen zweidimensionalen (tabellarischen) Datenrahmen zurück

## <a name="examples"></a>Beispiele

In den folgenden Beispielen basieren auf dem AdventureWorks Data Marts und Cubes-Projekt, da dieses Projekt ist allgemein verfügbar in mehreren Versionen, einschließlich der Sicherungsdateien, die mit Analysis Services problemlos wiederhergestellt werden können. Wenn Sie nicht über einen vorhandenen Cube verfügen, erhalten Sie einen Beispielcube mithilfe einer der folgenden Optionen:

+ Erstellen Sie den Cube, der verwendet wird, in diesen Beispielen im Analysis Services Tutorial bis zur Lektion 4: [Erstellen eines OLAP-Cubes](../../analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial.md)

+ Einen vorhandenen Cube als Sicherung herunterladen und in einer Instanz von Analysis Services wiederhergestellt werden kann. Diese Website bietet beispielsweise einen vollständig verarbeiteten Cube im ZIP-Format: [AdventureWorks mehrdimensionale Modelle SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334). Extrahieren Sie die Datei, und klicken Sie dann in Ihrer SSAS-Instanz wiederherstellen. Weitere Informationen finden Sie unter [Sicherungs- und Wiederherstellungsvorgänge](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md), oder [Restore-ASDatabase Cmdlet](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

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
+ Diese Abfrage würde eine Tabelle mit drei Spalten mit Zurückgeben einer _Rollup_ -Zusammenfassung der internetumsätze aus allen Ländern.
+ Gibt an, die WHERE-Klausel der _Slicer-Achse_. In diesem Beispiel verwendet der Slicer ein Element der **"salesterritory"** Dimension, um die Abfrage zu filtern, sodass nur Umsätze aus Australien in Berechnungen verwendet werden.

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

Werden Sie für eine benannte Instanz ist sicher, dass alle Zeichen mit Escapezeichen versehen, die Steuerzeichen in r betrachtet werden können  Die folgende Verbindungszeichenfolge verweist beispielsweise eine Instanz OLAP01, auf einem Server mit dem Namen ContosoHQ:

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

Wenn Sie eine Abfrage definieren, mit dem MDX-Generator in SQL Server Management Studio, und speichern Sie die MDX-Zeichenfolge, wird es die Achsen bei 0 beginnt, Anzahl, wie hier gezeigt: 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

Trotzdem können Sie diese Abfrage als vordefinierte MDX-Zeichenfolge ausführen. Allerdings erstellen Sie die gleiche Abfrage mithilfe von R und die `axis()` -Funktion, Sie müssen neu nummerieren die Achsen, beginnend mit 1.

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2. Durchsuchen von Cubes und ihren Feldern in einer SSAS-Instanz

Sie können die `explore`-Funktion verwenden, um eine Liste der Cubes, Dimensionen oder Elemente zurückzugeben, die zum Erstellen Ihrer Abfrage verwendet werden sollen. Dies ist praktisch, wenn Sie keinen Zugang zu anderen Tools zum Durchsuchen von OLAP haben oder die MDX-Abfrage programmgesteuert erstellen oder ändern möchten.

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>So listen Sie die für die angegebene Verbindung verfügbaren Cubes auf

Um alle Cubes oder Perspektiven auf der Instanz anzuzeigen, für die Sie eine Ansichtsberechtigung besitzen, übergeben Sie das Handle als Argument an `explore`.

> [!IMPORTANT]
> Das Endergebnis ist **nicht** eines Cubes; "True" lediglich gibt an, dass der Metadatenvorgang erfolgreich war. Bei ungültigen Argumenten wird ein Fehler ausgelöst.

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

Geben Sie nach dem Definieren der Quelle und dem Erstellen des Handles den Cube, die Dimension und die Hierarchie an, die zurückgegeben werden sollen. In den rückgabeergebnissen, Elemente, die mit dem Präfix **->** untergeordnete Elemente des vorhergehenden Members darstellt.

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
