---
title: Berechnungsgruppen in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 06/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: abc1f51d21613676fd94271f931e1a7692cc1efc
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822689"
---
# <a name="calculation-groups-preview"></a>Berechnungsgruppen (Vorschau)
 
[!INCLUDE[ssas-appliesto-sql2019-aas](../../includes/ssas-appliesto-sql2019-aas.md)]

Berechnungsgruppen erheblich weniger redundante Measures durch Gruppieren von allgemeinen Measureausdrücke als *Berechnung Elemente*. Berechnungsgruppen werden unterstützt, in Azure Analysis Services und SQL Server Analysis Services 2019 tabellarische Modelle, auf die 1470 und höher [Kompatibilitätsgrad](compatibility-level-for-tabular-models-in-analysis-services.md). Modelle mit Kompatibilitätsgrad 1470 sind derzeit in **Vorschau**.  

Dieser Artikel beschreibt: 

> [!div class="checklist"]
> * Vorteile 
> * Funktionsweise von Berechnungsgruppen
> * Dynamische Formatzeichenfolgen
> * Rangfolge
> * Tools
> * Einschränkungen



## <a name="benefits"></a>Vorteile

Berechnungsgruppen beheben ein Problem bei komplexen Modellen, in denen es möglich, einer Verbreitung von redundanten Measures, die mit der gleichen Berechnungen - am häufigsten verwendeten mit Zeitintelligenz Berechnungen. Z. B. ein sales Analyst Gesamtumsatz anzeigen möchte, und sortiert nach Monat-bis-Datum (MTD), Quarter-to-Date (QTD), Jahr-bis-heute (seit Jahresbeginn), ordnet Jahr-bis-heute für das Vorjahr (PY), und So weiter. Die datenmodellierer verfügt über separate Measures für jede Berechnung zu erstellen, was zu Dutzenden von Measures führen kann. Für den Benutzer kann dies bedeuten, müssen über viele Measures sortiert und einzeln auf ihren Bericht anwenden. 

Lassen Sie uns zunächst sehen Sie sich wie Berechnungsgruppen für Benutzer in ein Berichtstool wie Power BI angezeigt werden. Wir werden dann sehen Sie sich eine Gruppe Berechnung macht und wie sie in einem Modell erstellt werden.

Berechnungsgruppen werden in Berichterstellungsclients als Tabelle mit einer einzigen Spalte angezeigt. Die Spalte, die wie eine typische Spalte oder eine Dimension ist nicht, stattdessen eine oder mehrere wiederverwendbare Berechnungen dar oder *Berechnung Elemente* , die angewendet werden kann, um ein Measure, das Werte-Filter für eine Visualisierung bereits hinzugefügt wurden.

In der folgenden Animation analysiert ein Benutzer Umsatzdaten für Jahre 2012 und 2013. Vor dem Anwenden einer Berechnungsgruppe, allgemeine basismeasure **Sales** berechnet die Summe der Gesamtumsatz für jeden Monat. Der Benutzer möchte anschließend anzuwendende zeitintelligenzfunktionen Berechnungen durch, um die Gesamtumsätze für Monat bis Datum "," Quartal bis Datum "," Jahr-bis-Datum abrufen und so weiter. Ohne Berechnungsgruppen müsste der Benutzer einzelne zeitintelligenzfunktionen Measures auswählen.

Mit einer Berechnungsgruppe, in diesem Beispiel den Namen **Zeitintelligenz**, wenn der Benutzer zieht die **die Zeitberechnung** Element für die **Spalten** Filterbereich, jede Berechnungselement wird als separate Spalte angezeigt. Werte für jede Zeile aus der Messung berechnet werden **Sales**.  

![Berechnungsgruppe, die in Power BI angewendet wird](media/calculation-groups/calc-groups-pbi.gif)


Berechnungsgruppen arbeiten mit **explizite** DAX-Measures. In diesem Beispiel **Sales** eines expliziten Measures, die bereits im Modell erstellt wird. Berechnungsgruppen funktionieren nicht mit impliziten DAX-Measures. Beispielsweise werden in Power BI impliziten Measures erstellt, wenn ein Benutzer visuelle Elemente, um aggregierte Werte anzuzeigen, ohne ein explizites Measure erstellen Spalten gezogen. Zu diesem Zeitpunkt generiert Power BI DAX für implizite Measures, die als Inline geschrieben, DAX-Berechnungen – was bedeutet, dass implizite Measures Berechnungsgruppen nicht bearbeiten können. Eine neue Modelleigenschaft sichtbar, in dem Tabular Object Model (TOM) wurde eingeführt, **DiscourageImplicitMeasures**. Derzeit um Berechnungsgruppen erstellen Sie diese Eigenschaft müssen festgelegt werden **"true"** . Bei Festlegung auf "true", "Power BI Desktop in Live Connect deaktiviert Modus die Erstellung impliziter Measures an.

## <a name="how-they-work"></a>Funktionsweise

Nun, Sie gesehen haben, wie Berechnungsgruppen Benutzer profitieren, werfen wir einen Blick auf wie bei dem der Zeitintelligenz Berechnung Gruppe Beispiel erstellt wird.

Bevor wir ins Detail gehen, führen wir einige neuen DAX-Funktionen speziell für Berechnungsgruppen aus: 

[SELECTEDMEASURE](https://docs.microsoft.com/dax/selectedmeasure-function-dax) : wird verwendet, der von Ausdrücken für die Berechnung von Elementen auf das Measure verweisen, die derzeit im Kontext vorhanden ist. In diesem Beispiel ist das Sales-Measure.

[SELECTEDMEASURENAME](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) : wird verwendet, die von Ausdrücken für die Berechnung-Elemente, die das Measure zu ermitteln, die im Kontext nach dem Namen vorhanden ist.

[ISSELECTEDMEASURE](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) : wird verwendet, die von Ausdrücken für die Berechnung-Elemente, um zu bestimmen, das Measure, das im Kontext vorhanden ist, die in einer Liste von Measures angegeben ist.

[SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) : wird verwendet, die von Ausdrücken für die Berechnung abzurufenden Elemente an die Formatzeichenfolge des Measures, die im Kontext vorhanden ist.

### <a name="time-intelligence-example"></a>Beispiel für Time Intelligence

Tabellenname - **Zeitintelligenz**   
Spaltenname: **die Zeitberechnung**   
Rangfolge - **20**   

#### <a name="time-intelligence-calculation-items"></a>Time Intelligence Berechnung Elemente

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

**PY**

```dax
CALCULATE(SELECTEDMEASURE(), SAMEPERIODLASTYEAR(DimDate[Date]))
```

**PY MTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "MTD"
)
```

**PY QTD**

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

**YOY**

```dax
SELECTEDMEASURE() –
CALCULATE(
    SELECTEDMEASURE(),
    'Time Intelligence'[Time Calculation] = "PY"
)
```

**ÜBER JAHR IN %**

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

Sie können eine DAX-Abfrage in SSMS oder Open-Source ausführen, um diese Berechnungsgruppe zu testen, [DAX Studio](http://daxstudio.org/). Im Jahresvergleich und % im Jahresvergleich werden von der Abfrage werden beispielsweise weggelassen.

#### <a name="time-intelligence-query"></a>Time Intelligence-Abfrage

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

#### <a name="time-intelligence-query-return"></a>Time Intelligence zurückgibt.

Die zurückgegebene Tabelle zeigt die Berechnungen für jede Berechnung Element angewendet. Beispielsweise sehen Sie sich, dass QTD für März 2012 die Summe der Januar, Februar und März 2012 ist.

![Abfrage zurückgeben](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>Dynamische Formatzeichenfolgen

*Dynamische Formatzeichenfolgen* mit Berechnung mit Gruppen können Sie bedingte Anwendung von Formatzeichenfolgen auf Measures ohne gezwungen, sich Zeichenfolgen zurückzugeben.

Tabellarische Modelle unterstützen die dynamische Formatierung von Measures mit DAX [FORMAT](https://docs.microsoft.com/dax/format-function-dax) Funktion. Die FORMAT-Funktion hat jedoch den Nachteil, dass eine Zeichenfolge zurückgibt, und Erzwingen von Measures, die andernfalls numerisch sein, auch als Zeichenfolge zurückgegeben werden. Dies kann einige Einschränkungen, z. B. funktioniert nicht mit den meisten Power BI-Visuals, abhängig von numerischen Werten, wie Diagramme haben.

### <a name="dynamic-format-strings-for-time-intelligence"></a>Dynamische Formatzeichenfolgen für zeitintelligenzfunktionen

Wenn wir das oben gezeigte Beispiel für Zeitintelligenz betrachten, alle Berechnung die Elemente, mit Ausnahme von **% im Jahresvergleich** sollte das Format der das aktuelle Measure im Kontext verwenden. Z. B. **seit Jahresbeginn** berechnet die Basis Sales-Measure ' Currency ' sein sollte. Würde dies eine Berechnungsgruppe für z. B. ein basismeasure Bestellungen, würde das Format ein Zahlenwert angegeben werden. **% Im Jahresvergleich**, sollte jedoch ein Prozentsatz unabhängig vom Format der basismeasure sein.

Für **% im Jahresvergleich**, wir können die Formatzeichenfolge außer Kraft setzen, indem Sie die Format-String-Expression-Eigenschaft auf **0,00 %;-0.00 ";" 0,00 %** . Weitere Informationen zu den Eigenschaften des Ausdrucks Format finden Sie unter [MDX – Zelleigenschaften: FORMAT von Zeichenfolgeninhalten](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values).

In dieser Matrix visual in Power BI, Sie finden Sie unter **Sales aktuellen/im Jahresvergleich** und **Bestellungen aktuellen/im Jahresvergleich** behalten ihre jeweiligen basismeasure Formatzeichenfolgen. **% Der Umsätze im Jahresvergleich** und **Bestellungen über Jahr in %** , überschreibt jedoch die zu verwendende Formatzeichenfolge *Prozentsatz* Format.

![Zeitintelligenz im matrixvisual](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>Dynamische Formatzeichenfolgen für die währungsumrechnung

Dynamische Formatzeichenfolgen bieten einfache währungsumrechnung. Erwägen Sie die folgende Adventure Works-Datenmodell. Es wird für modelliert *1: n* währungsumrechnung gemäß [Umrechnungstyp](../currency-conversions-analysis-services.md#conversion-types).

![Currency-Rate im tabellarischen Modell](media/calculation-groups/calc-groups-currency-conversion.png)

Ein **FormatString** Spalte wird hinzugefügt, um die **DimCurrency** Tabelle, und klicken Sie mit Formatzeichenfolgen für die entsprechenden Währungen aufgefüllt.

![Format-Zeichenfolgenspalte](media/calculation-groups/calc-groups-formatstringcolumn.png)

In diesem Beispiel wird die folgende Berechnungsgruppe klicken Sie dann wie folgt definiert:

### <a name="currency-conversion-example"></a>Beispiel für die Konvertierung von Währung

Tabellenname - **Währungsumrechnung**   
Spaltenname: **Konvertierung-Berechnung**   
Rangfolge - **5**   

#### <a name="calculation-items-for-currency-conversion"></a>Berechnung der Elemente für die Währungsumrechnung

**Keine Konvertierung**

```dax
SELECTEDMEASURE()
```

**Konvertierte Währung**

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

Zeichenfolgenausdruck für Format

```dax
SELECTEDVALUE(
    DimCurrency[FormatString],
    SELECTEDMEASUREFORMATSTRING()
)
```
Der Formatausdruck für die Zeichenfolge muss es sich um eine skalare Zeichenfolge zurückgeben. Er verwendet den neuen [SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) Funktion, die mit der Formatzeichenfolge für die Messung zurückgesetzt werden soll, wenn mehrere Währungen in Filterkontext vorhanden sind.

Die folgende Animation zeigt die währungsumrechnung dynamisches Format aufweisen, der die **Sales** Measure in einem Bericht.

![Konvertierung dynamische Währungsformatzeichenfolge angewendet](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>Rangfolge

Rangfolge ist eine Eigenschaft für eine Berechnungsgruppe definiert. Es gibt die Reihenfolge der Auswertung an, wenn mehr als eine Gruppe von Berechnung vorhanden ist. Eine höhere Zahl gibt an der Rangfolge höher eingestuft, was bedeutet, dass es vor der Berechnungsgruppen mit niedrigerer Rangfolge ausgewertet wird.

In diesem Beispiel wir später verwenden Sie dasselbe Modell Zeitintelligenz Beispiel, aber auch hinzufügen, eine **Durchschnittswerte** Berechnungsgruppe. Die Gruppe der Durchschnittswerte Berechnung enthält durchschnittsberechnungen, die unabhängig von der herkömmlichen Zeitintelligenz darin, dass den Filterkontext Datum werden dadurch nicht verändert: nur durchschnittsberechnungen darin gelten.

In diesem Beispiel wird eine tägliche durchschnittliche Berechnung definiert. Berechnungen wie durchschnittliche barrel Öl pro Tag werden häufig bei Öl und Gas-Anwendungen. Andere häufige Business-Beispiele sind die durchschnittlichen Umsatz im Store im Einzelhandel.

Während Sie solche Berechnungen unabhängig von der Zeitintelligenz Berechnungen berechnet werden, sein gibt es auch erforderlich, diese zu kombinieren. Beispielsweise kann ein Benutzer möchte barrel Öl pro Tag seit Jahresbeginn Öl Tagessatz vom Anfang des Jahres auf das aktuelle Datum anzeigen, finden Sie unter. In diesem Fall sollte die Rangfolge für Berechnung Elemente festgelegt werden.

### <a name="averages-example"></a>Durchschnittswerte-Beispiel

Der Tabellenname ist **Durchschnittswerte**.   
Der Spaltenname ist **Durchschnittsberechnung**.   
Rangfolge ist **10**.   

#### <a name="calculation-items-for-averages"></a>Durchschnittswerte Berechnung Elemente

**Keine Durchschnitt**

```dax
SELECTEDMEASURE()
```

**Im Tagesdurchschnitt**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Hier ist ein Beispiel einer DAX-Abfrage und der zurückgegebenen Tabelle:

#### <a name="averages-query"></a>Durchschnittswerte-Abfrage

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

#### <a name="averages-query-return"></a>Durchschnittswerte Abfrage zurückgeben

![Abfrage zurückgeben](media/calculation-groups/calc-groups-ytd-daily-avg.png)

Die folgende Tabelle zeigt, wie die Werte für März 2012 berechnet werden.


|Spaltenname  |Berechnung |
|---------|---------|
|YTD     |    Summe der Verkäufe für Januar, Februar, März 2012<br />= 495,364 + 506,994 + 373,483     |
|Im Tagesdurchschnitt    |     Verkäufe für März 2012 geteilt durch die Anzahl der Tage im März<br />= 373,483 / 31       |
|Im Tagesdurchschnitt seit Jahresbeginn     | YTD für März 2012 geteilt durch die Anzahl der Tage im Januar, Februar und März<br />=  1,375,841 / (31 + 29 + 31)       |

Hier ist die Definition des Elements Berechnung seit Jahresbeginn, mit der Rangfolge angewendet **20**.

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

So sieht tägliche durchschnittliche, mit einer Priorität von angewendet **10**.

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

Da die Rangfolge der Berechnungsgruppe Zeitintelligenz höher als bei der der Gruppe der Durchschnittswerte Berechnung ist, wird er als allgemein wie möglich angewendet. Die tägliche durchschnittliche seit Jahresbeginn Berechnung gilt seit Jahresbeginn für sowohl den Zähler und Nenner (Anzahl von Tagen) der tägliche Berechnung des Durchschnitts.

Dies entspricht dem folgenden Ausdruck:

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

Keine dieser Ausdruck:

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>Sideways Rekursion

Im obigen Zeitintelligenz-Beispiel finden Sie einige der Elemente, Berechnung an andere Personen in der gleichen Gruppe für die Berechnung. Dies wird als bezeichnet *sideways Rekursion*. Z. B. **% im Jahresvergleich** verweist auf beides **im Jahresvergleich** und **PY**.

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

Beide Ausdrücke werden in diesem Fall einzeln ausgewertet, da sie verschiedene verwenden Anweisungen zu berechnen. Andere Arten von Rekursion werden nicht unterstützt.

## <a name="single-calculation-item-in-filter-context"></a>Einzelne Berechnung-Element in der Filterkontext

In unserem Beispiel der Zeitintelligenz der **PY YTD** Berechnungselement verfügt über einen einzelnen Ausdruck berechnen:

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

Die YTD-Argument für die CALCULATE()-Funktion überschreibt den Filterkontext die Logik, die bereits in das Berechnungselement seit Jahresbeginn definiert wiederverwenden. Es ist nicht möglich, sowohl für PY seit Jahresbeginn in eine einzelne Auswertung anzuwenden. Berechnungsgruppen sind *nur angewendet,* ist eine einzelne Berechnung-Element aus der Berechnungsgruppe in Filterkontext.

## <a name="mdx-support"></a>MDX-Unterstützung

Berechnungsgruppen unterstützen MDX Daten (Multidimensional Expressions) Abfragen. Dies bedeutet, Microsoft Excel-Benutzer, welche Abfrage tabellarischen Datenmodellen mithilfe von MDX, ausnutzen können von Berechnungsgruppen im Arbeitsblatt PivotTables und Diagrammen.

## <a name="tools"></a>Tools

Berechnungsgruppen werden noch nicht in SQL Server Data Tools, Visual Studio mit Analysis Services-Erweiterungen unterstützt. Allerdings können Berechnungsgruppen erstellt werden, mithilfe von Tabular Model Scripting Language (TMSL) oder der open Source- [tabellarischen Editor](https://github.com/otykier/TabularEditor).

## <a name="limitations"></a>Einschränkungen

[Sicherheit auf Zeilenebene Objekt](object-level-security.md) (OLS) definierte Berechnung der gruppentabellen wird nicht unterstützt. OLS kann jedoch auf andere Tabellen im gleichen Modell definiert werden. Wenn ein Berechnungselement auf eine OLS gesichertes Objekt verweist, wird ein generischer Fehler zurückgegeben.

[Sicherheit auf Zeilenebene](roles-ssas-tabular.md#bkmk_rowfliters) (auf Zeilenebene RLS) wird nicht unterstützt. Sie können RLS für Tabellen in das gleiche Modell, jedoch nicht für Berechnungsgruppen selbst (direkt oder indirekt) definieren.

[Zeilen-Ausdrücke erläutert](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md) Berechnungsgruppen werden nicht unterstützt.

## <a name="see-also"></a>Siehe auch  

[DAX in tabellarischen Modellen](understanding-dax-in-tabular-models-ssas-tabular.md)   
[DAX-Referenz](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
