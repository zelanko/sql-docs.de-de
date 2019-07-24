---
title: Berechnungs Gruppen in Analysis Services tabellarischen Modellen | Microsoft-Dokumentation
ms.date: 07/24/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af63f41555a021fc720c7d1e15778265fe7de500
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419525"
---
# <a name="calculation-groups-preview"></a>Berechnungs Gruppen (Vorschau)
 
[!INCLUDE[ssas-appliesto-sql2019-aas](../../includes/ssas-appliesto-sql2019-aas.md)]

Berechnungs Gruppen können die Anzahl von redundanten Measures erheblich verringern, indem allgemeine Measure-Ausdrücke als *Berechnungs Elemente*gruppiert werden. Berechnungs Gruppen werden in Azure Analysis Services tabellarischen und SQL Server Analysis Services 2019-Modellen mit dem [Kompatibilitäts Grad](compatibility-level-for-tabular-models-in-analysis-services.md)1470 und höher unterstützt. Modelle mit dem Kompatibilitäts Grad 1470 befinden sich zurzeit in der **Vorschau**Phase.  

Dieser Artikel beschreibt: 

> [!div class="checklist"]
> * Vorteile 
> * Funktionsweise von Berechnungs Gruppen
> * Dynamische Format Zeichenfolgen
> * Stelle
> * Rangfolge
> * Tools
> * Einschränkungen



## <a name="benefits"></a>Vorteile

Berechnungs Gruppen beheben ein Problem in komplexen Modellen, bei denen es eine Verbreitung redundanter Measures mit denselben Berechnungen geben kann, die am häufigsten bei Zeit Intelligenz Berechnungen verwendet werden. Ein Vertriebs Analyst möchte z. b. Umsatz Summen und Bestellungen nach Monat-bis-heute (MTD), Quartal-to-date (QTD), year-to-date (YTD), Aufträge Year-to-date für das vorherige Jahr (PY) usw. anzeigen. Der Daten modelzierer muss separate Measures für jede Berechnung erstellen, was zu Dutzenden von Measures führen kann. Für den Benutzer kann dies bedeuten, dass Sie genau so viele Measures sortieren und Sie einzeln auf den Bericht anwenden müssen. 

Sehen wir uns zunächst an, wie Berechnungs Gruppen Benutzern in einem Bericht Erstellungs Tool wie Power BI angezeigt werden. Wir sehen uns nun an, was eine Berechnungs Gruppe ausmacht und wie Sie in einem Modell erstellt werden.

Berechnungsgruppen werden in Berichterstellungsclients als Tabelle mit einer einzigen Spalte angezeigt. Die Spalte ist nicht wie eine typische Spalte oder Dimension, sondern stellt eine oder mehrere wiederverwendbare Berechnungen dar, oder *Berechnungs Elemente* , die auf jedes Measure angewendet werden können, das dem Filter Werte für eine Visualisierung bereits hinzugefügt wurde.

In der folgenden Animation analysiert ein Benutzer Umsatzdaten für die Jahre 2012 und 2013. Vor dem Anwenden einer Berechnungs Gruppe berechnet der allgemeine basismeasure- **Umsatz** eine Summe der Gesamtumsätze für jeden Monat. Der Benutzer möchte dann Zeit Intelligenz Berechnungen anwenden, um Umsatz Summen für "Monat", "Quartal bis Datum", "Jahr bis Datum" usw. zu erhalten. Ohne Berechnungs Gruppen müsste der Benutzer einzelne Zeit Intelligenz Measures auswählen.

Bei einer Berechnungs Gruppe wird in diesem Beispiel **Zeit Intelligenz**, wenn der Benutzer das **Zeit Berechnungs** Element in den **Spalten** Filterbereich zieht, jedes Berechnungs Element als separate Spalte angezeigt. Werte für jede Zeile werden aus dem basismeasure " **Sales**" berechnet.  

![Die Berechnungs Gruppe wird in Power BI angewendet.](media/calculation-groups/calc-groups-pbi.gif)


Berechnungs Gruppen können mit **expliziten** DAX-Measures verwendet werden. In diesem Beispiel ist **Sales** ein explizites Measure, das bereits im Modell erstellt wurde. Berechnungs Gruppen können nicht mit impliziten DAX-Measures verwendet werden. Beispielsweise werden in Power BI implizite Measures erstellt, wenn ein Benutzer Spalten auf visuelle Elemente zieht, um aggregierte Werte anzuzeigen, ohne ein explizites Measure zu erstellen. Zu diesem Zeitpunkt generiert Power BI DAX für implizite Measures, die als Inline-DAX-Berechnungen geschrieben wurden. Dies bedeutet, dass implizite Measures nicht mit Berechnungs Gruppen funktionieren können. Eine neue Modell Eigenschaft, die im tabellarischen Objektmodell (Tom) sichtbar ist, wurde in " **entmuageimplicitmeasures**" eingeführt. Derzeit muss diese Eigenschaft auf **true**festgelegt werden, damit Berechnungs Gruppen erstellt werden können. Wenn der Wert auf true festgelegt ist, wird die Erstellung impliziter Measures im Live Connect-Modus Power BI Desktop deaktiviert.

## <a name="how-they-work"></a>Funktionsweise

Nachdem Sie nun gesehen haben, wie Berechnungs Gruppen von Benutzern profitieren, sehen wir uns an, wie das Beispiel für die Zeit Intelligenz-Berechnungs Gruppe erstellt wird.

Bevor wir uns mit den Details befassen, führen wir einige neue DAX-Funktionen speziell für Berechnungs Gruppen ein: 

[Selectedmeasure](https://docs.microsoft.com/dax/selectedmeasure-function-dax) : wird von Ausdrücken für Berechnungs Elemente verwendet, um auf das Measure zu verweisen, das sich derzeit im Kontext befindet. In diesem Beispiel das Sales-Measure.

[Selectedmeasurename](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) : wird von Ausdrücken für Berechnungs Elemente verwendet, um das Measure zu bestimmen, das sich im Kontext nach Namen befindet.

[Isselectedmeasure](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) : wird von Ausdrücken für Berechnungs Elemente verwendet, um zu bestimmen, ob das Measure, das sich im Kontext befindet, in einer Liste von Measures angegeben wird.

[Selectedmeasformatatstring](https://docs.microsoft.com/dax/selectedmeasureformatstring-function-dax) : wird von Ausdrücken für Berechnungs Elemente verwendet, um die Format Zeichenfolge des Measures abzurufen, das sich im Kontext befindet.

### <a name="time-intelligence-example"></a>Beispiel für Zeit Intelligenz

Tabellenname- **Zeit Intelligenz**   
Spaltenname- **Zeitberechnung**   
Rangfolge- **20**   

#### <a name="time-intelligence-calculation-items"></a>Zeit Intelligenz-Berechnungs Elemente

**Current**

```dax
SELECTEDMEASURE()
```

**MTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESMTD(DimDate[Date]))
```

**QTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESQTD(DimDate[Date]))
```

**YTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

**SEILE**

```dax
CALCULATE(SELECTEDMEASURE(), SAMEPERIODLASTYEAR(DimDate[Date]))
```

**PY-MTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "MTD"
)
```

**PY-QTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "QTD"
)
```

**PY YTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

**IM JAHRESVERGLEICH**

```dax
SELECTEDMEASURE() –
CALCULATE(
    SELECTEDMEASURE(),
    'Time Intelligence'[Time Calculation] = "PY"
)
```

**IM JAHRESVERGLEICH**

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

Um diese Berechnungs Gruppe zu testen, können Sie eine DAX-Abfrage in SSMS oder in der Open-Source- [DAX](http://daxstudio.org/)-Abfrage ausführen. YoY und YoY% werden in diesem Abfrage Beispiel ausgelassen.

#### <a name="time-intelligence-query"></a>Zeit Intelligenz Abfrage

```dax
EVALUATE
CALCULATETABLE (
    SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Current", CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "Current" ),
        "QTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "QTD" ),
        "YTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "YTD" ),
        "PY",      CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY" ),
        "PY QTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY QTD" ),
        "PY YTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY YTD" )
    ),
    DimDate[CalendarYear] IN { 2012, 2013 }
)
```

#### <a name="time-intelligence-query-return"></a>Zeit Intelligenz Abfrage Rückgabe

Die Rückgabe Tabelle zeigt Berechnungen für jedes angewendete Berechnungs Element an. Beispielsweise sehen Sie, dass QTD für März 2012 die Summe aus Januar, Februar und 2012 ist.

![Abfrage Rückgabe](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>Dynamische Format Zeichenfolgen

*Dynamische Format* Zeichenfolgen mit Berechnungs Gruppen ermöglichen die bedingte Anwendung von Format Zeichenfolgen, ohne dass Sie eine Zeichenfolge zurückgeben.

Tabellarische Modelle unterstützen die dynamische Formatierung von Measures mithilfe der DAX- [Format](https://docs.microsoft.com/dax/format-function-dax) Funktion. Die Format-Funktion hat jedoch den Nachteil, dass eine Zeichenfolge zurückgegeben wird, wodurch Measures erzwungen werden, die andernfalls numerisch wären, um auch als Zeichenfolge zurückgegeben zu werden. Dies kann einige Einschränkungen haben, z. b. die Verwendung der meisten Power BI visuellen Elemente, die von numerischen Werten wie Diagrammen abhängig sind.

### <a name="dynamic-format-strings-for-time-intelligence"></a>Dynamische Format Zeichenfolgen für Zeit Intelligenz

Wenn wir uns das oben gezeigte Zeit Intelligenz Beispiel ansehen, sollten alle Berechnungs Elemente mit Ausnahme von **YoY%** das Format des aktuellen Measures im Kontext verwenden. Beispielsweise sollte für das Sales Base-Measure berechnetes **YTD** eine Währung sein. Wenn es sich hierbei um eine Berechnungs Gruppe handelt, die einem Order-basismeasure ähnelt, wäre das Format numerisch. Der Wert für " **YoY%** " sollte jedoch unabhängig vom Format des Basismeasures ein Prozentsatz sein.

Für " **YoY%** " können Sie die Format Zeichenfolge überschreiben, indem Sie die Format Zeichenfolgen-Ausdrucks Eigenschaft auf **0,00%;-0,00%; 0,00%** festlegen. Weitere Informationen zu Format Zeichenfolgen-Ausdrucks Eigenschaften finden Sie unter [MDX-Zell Eigenschaften-Formatieren von Zeichen folgen Inhalten](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values).

In diesem matrixvisual in Power BI sehen Sie **Sales Current/YoY** , und **Orders Current/YoY** behalten ihre jeweiligen basismeasure-Format Zeichenfolgen bei. **Sales YoY%** und **Order YoY%** überschreibt jedoch die Format Zeichenfolge für die Verwendung des *Prozent* Formats.

![Zeit Intelligenz in Matrix Visualisierung](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>Dynamische Format Zeichenfolgen für die Währungsumrechnung

Dynamische Format Zeichenfolgen ermöglichen eine einfache Währungsumrechnung. Sehen Sie sich das folgende Adventure Works-Datenmodell an. Sie wird für die *1:* n-Währungsumrechnung modelliert, wie von [Konvertierungs Typen](../currency-conversions-analysis-services.md#conversion-types)definiert.

![Währungs Satz im tabellarischen Modell](media/calculation-groups/calc-groups-currency-conversion.png)

Der **DimCurrency** -Tabelle wird eine **FormatString** -Spalte hinzugefügt und mit Format Zeichenfolgen für die jeweiligen Währungen aufgefüllt.

![Zeichen folgen Spalte formatieren](media/calculation-groups/calc-groups-formatstringcolumn.png)

In diesem Beispiel wird die folgende Berechnungs Gruppe als definiert:

### <a name="currency-conversion-example"></a>Beispiel für Währungsumrechnung

Tabellenname- **Währungsumrechnung**   
Spaltenname: **Konvertierungs Berechnung**   
Rangfolge- **5**   

#### <a name="calculation-items-for-currency-conversion"></a>Berechnungs Elemente für die Währungsumrechnung

**Keine Konvertierung**

```dax
SELECTEDMEASURE()
```

**Umgewandelte Währung**

```dax
IF(
    //Check one currency in context & not US Dollar, which is the pivot currency:
    SELECTEDVALUE( DimCurrency[CurrencyName], "US Dollar" ) = "US Dollar",
    SELECTEDMEASURE(),
    SUMX(
        VALUES(DimDate[Date]),
        CALCULATE( DIVIDE( SELECTEDMEASURE(), MAX(FactCurrencyRate[EndOfDayRate]) ) )
    )
)
```

Format Zeichen folgen Ausdruck

```dax
SELECTEDVALUE(
    DimCurrency[FormatString],
    SELECTEDMEASUREFORMATSTRING()
)
```
Der Format Zeichenfolgen-Ausdruck muss eine skalare Zeichenfolge zurückgeben. Er verwendet die neue [selectedmeasformatatstring](https://docs.microsoft.com/dax/selectedmeasureformatstring-function-dax) -Funktion, um die basismeasure-Format Zeichenfolge wiederherzustellen, wenn mehrere Währungen im Filter Kontext vorhanden sind.

Die folgende Animation zeigt die Währungsumrechnung für das **Sales** -Measure (Dynamic Format) in einem Bericht.

![Dynamische Format Zeichenfolge für Währungsumrechnung angewendet](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>Rangfolge

Die Rangfolge ist eine Eigenschaft, die für eine Berechnungs Gruppe definiert wurde. Gibt die Auswertungs Reihenfolge an, wenn mehr als eine Berechnungs Gruppe vorhanden ist. Eine höhere Zahl weist auf eine höhere Rangfolge hin. Dies bedeutet, dass Sie vor Berechnungs Gruppen mit niedrigerer Rangfolge ausgewertet wird.

In diesem Beispiel verwenden wir das gleiche Modell wie im obigen Beispiel für die Zeit Intelligenz, aber auch eine Berechnungs Gruppe mit **Durchschnittswerten** hinzufügen. Die Berechnungs Gruppe "Average" enthält durchschnittliche Berechnungen, die unabhängig von der herkömmlichen Zeit Intelligenz sind, da Sie den Datumsfilter Kontext nicht ändern, sondern nur die durchschnittlichen Berechnungen darin anwenden.

In diesem Beispiel wird eine tägliche durchschnittliche Berechnung definiert. Berechnungen, wie z. b. durchschnittliche Barrel von Öl pro Tag, sind in Öl-und Gasanwendungen üblich. Weitere häufige Geschäfts Beispiele sind der durchschnittliche Umsatz im Einzelhandel.

Obwohl solche Berechnungen unabhängig von Zeit Intelligenz Berechnungen berechnet werden, ist es möglicherweise erforderlich, diese zu kombinieren. Beispielsweise kann es vorkommen, dass ein Benutzer einen Strom von Öl pro Tag YTD sehen möchte, um den täglichen Ölpreis von Beginn des Jahres bis zum aktuellen Datum anzuzeigen. In diesem Szenario sollte die Rangfolge für Berechnungs Elemente festgelegt werden.

### <a name="averages-example"></a>Beispiel für Mittelwerte

Der Tabellenname ist **Average**.   
Der Spaltenname ist die **durchschnittliche Berechnung**.   
Die Rangfolge ist **10**.   

#### <a name="calculation-items-for-averages"></a>Berechnungs Elemente für Durchschnittswerte

**Kein Durchschnitt**

```dax
SELECTEDMEASURE()
```

**Täglicher Durchschnitt**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Im folgenden finden Sie ein Beispiel für eine DAX-Abfrage und eine Rückgabe Tabelle:

#### <a name="averages-query"></a>Average-Abfrage

```dax
EVALUATE
    CALCULATETABLE (
        SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Sales", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "No Average"
        ),
        "YTD", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "No Average"
        ),
        "Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "Daily Average"
        ),
        "YTD Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "Daily Average"
        )
    ),
    DimDate[CalendarYear] = 2012
)
```

#### <a name="averages-query-return"></a>Durchschnittliche Abfrage Rückgabe

![Abfrage Rückgabe](media/calculation-groups/calc-groups-ytd-daily-avg.png)

Die folgende Tabelle zeigt, wie die Werte von März 2012 berechnet werden.


|Spaltenname  |Berechnung |
|---------|---------|
|YTD     |    Summe der Verkäufe für Jan, Feb, Mar 2012<br />= 495.364 + 506.994 + 373.483     |
|Täglicher Durchschnitt    |     Umsätze für Mar 2012 dividiert durch Anzahl von Tagen im März<br />= 373.483/31       |
|Täglicher YTD-Durchschnitt     | YTD für Mar 2012 dividiert durch Anzahl der Tage in Jan, Feb und Mar<br />= 1.375.841/(31 + 29 + 31)       |

Hier ist die Definition des YTD-Berechnungs Elements, das mit der Rangfolge **20**angewendet wird.

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

Dies ist der tägliche Durchschnitt, der mit einer Rangfolge von **10**angewendet wird.

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Da die Rangfolge der Zeit Intelligenz-Berechnungs Gruppe höher als die der Berechnung der Durchschnittswerte ist, wird Sie so weit wie möglich angewendet. Die tägliche durchschnittliche Berechnung von YTD wendet YTD auf den Zähler und den Nenner (Anzahl der Tage) der täglichen durchschnittlichen Berechnung an.

Dies entspricht dem folgenden Ausdruck:

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

Nicht dieser Ausdruck:

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>Seitwärts Rekursion

Im obigen Beispiel für die Zeit Intelligenz verweisen einige Berechnungs Elemente auf andere in derselben Berechnungs Gruppe. Dies wird als " *seitwärts Rekursion*" bezeichnet. Beispielsweise verweist **YoY%** auf **YoY** und **py**.

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

In diesem Fall werden beide Ausdrücke separat ausgewertet, da Sie unterschiedliche berechnenden Anweisungen verwenden. Andere Rekursions Typen werden nicht unterstützt.

## <a name="single-calculation-item-in-filter-context"></a>Einzelnes Berechnungs Element im Filter Kontext

In unserem Zeit Intelligenz Beispiel hat das Berechnungs Element **py YTD** einen einzelnen Berechnungs Ausdruck:

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

Das YTD-Argument der Compu()-Funktion überschreibt den Filter Kontext, um die bereits im YTD-Berechnungs Element definierte Logik wiederzuverwenden. Es ist nicht möglich, "py" und "YTD" in einer einzelnen Auswertung anzuwenden. Berechnungs Gruppen werden *nur angewendet* , wenn sich ein einzelnes Berechnungs Element aus der Berechnungs Gruppe im Filter Kontext befindet.

## <a name="mdx-support"></a>MDX-Unterstützung

Berechnungs Gruppen unterstützen MDX-Abfragen (Multidimensional Data Expressions). Dies bedeutet, dass Microsoft Excel-Benutzer, die tabellarische Datenmodelle mithilfe von MDX Abfragen, die Berechnungs Gruppen in Arbeitsblatt-PivotTables und-Diagrammen in vollem Umfang nutzen können.

## <a name="tools"></a>Tools

Berechnungs Gruppen werden in SQL Server Data Tools, Visual Studio mit Analysis Services Erweiterungen noch nicht unterstützt. Berechnungs Gruppen können jedoch mit tmsl (tabellarische Modell Skriptsprache) oder dem [tabellarischen](https://github.com/otykier/TabularEditor)Open Source-Editor erstellt werden.

## <a name="limitations"></a>Einschränkungen

[Sicherheit auf Objektebene](object-level-security.md) (OLS), die für Berechnungs Gruppen Tabellen definiert werden, werden nicht unterstützt. Allerdings können die OLE in anderen Tabellen im gleichen Modell definiert werden. Wenn ein Berechnungs Element auf ein gesichertes OLE-Objekt verweist, wird ein generischer Fehler zurückgegeben.

[Sicherheit auf Zeilenebene](roles-ssas-tabular.md#bkmk_rowfliters) (RLS) wird nicht unterstützt. Sie können RLS für Tabellen im gleichen Modell definieren, jedoch nicht für Berechnungs Gruppen selbst (direkt oder indirekt).

## <a name="see-also"></a>Siehe auch  

[DAX in tabellarischen Modellen](understanding-dax-in-tabular-models-ssas-tabular.md)   
[DAX-Referenz](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
