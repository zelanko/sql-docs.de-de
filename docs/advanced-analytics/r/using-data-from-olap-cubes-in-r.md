---
title: Verwenden von Daten aus OLAP-Cubes in R – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e55093c83e9a306a06235d6bb613dac78d4677ce
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642304"
---
# <a name="using-data-from-olap-cubes-in-r"></a>Verwenden von Daten aus OLAP-Cubes in R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die **OlapR** Paket ist ein R-Paket, sofern von Microsoft für die Verwendung mit Machine Learning Server und SQL Server, die Sie MDX-Abfragen zum Abrufen von Daten aus OLAP-Cubes ausführen können. Mit diesem Paket müssen Sie nicht verknüpfte Server erstellen oder vereinfachten Rowsets zu bereinigen. Sie können OLAP-Daten direkt aus r abrufen.

Dieser Artikel beschreibt die-API sowie eine Übersicht über OLAP- und MDX-R-Benutzer, die möglicherweise neu für mehrdimensionale Cubedatenbanken.

> [!IMPORTANT]
> Eine Instanz von Analysis Services kann herkömmliche mehrdimensionalen Cubes oder tabellarische Modelle unterstützen, aber eine Instanz kann nicht unterstützen beide Modelle. Aus diesem Grund, bevor Sie versuchen, eine MDX-Abfrage für einen Cube zu erstellen, stellen Sie sicher, dass die Instanz von Analysis Services mehrdimensionale Modelle enthält.

## <a name="what-is-an-olap-cube"></a>Was ist ein OLAP-Cube?

OLAP ist die Kurzform für Online Analytical Processing. OLAP-Lösungen werden häufig zum Erfassen und speichern kritische geschäftliche Daten im Laufe der Zeit verwendet. OLAP-Daten werden von einer Vielzahl von Tools, Dashboards und Visualisierungen für Business Analytics genutzt. Weitere Informationen finden Sie unter [analytische onlineverarbeitung](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft bietet [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), sodass Sie entwerfen, bereitstellen und Abfragen von OLAP-Daten in Form von _Cubes_ oder _Tabellenmodelle_. Ein Cube ist eine mehrdimensionale Datenbank an. _Dimensionen_ ähneln Facets der Daten oder Faktoren in Bezug auf r Sie Dimensionen verwenden, um eine bestimmte Teilmenge der Daten zu identifizieren, die Sie zusammenfassen oder analysieren möchten. Beispielsweise ist die Zeit eine wichtige Dimension, die so viel, damit viele OLAP-Lösungen mehrere Kalender definiert, in der Standardeinstellung beim Aufteilen in Slices und Zusammenfassen von Daten enthalten. 

Aus Gründen der Leistung eine OLAP-Datenbank häufig Zusammenfassungen berechnet (oder _Aggregationen_) im voraus und speichert sie schneller abrufen. Zusammenfassungen basieren auf *Measures*, die darstellen, dass Formeln, die auf numerische Daten angewendet werden können. Sie verwenden die Dimensionen, um eine Teilmenge der Daten definieren, und berechnen Sie das Measure über die Daten. Beispielsweise würden Sie ein Measure verwenden, berechnet den Gesamtumsatz für eine bestimmte Produktlinie in mehrere Quartalen abzüglich steuern, um die durchschnittliche Lieferkosten für einen bestimmten Lieferanten, Jahr-bis-heute kumulative Gehälter bezahlt, und So weiter zu melden.

MDX, kurz für mehrdimensionale Ausdrücke, ist die Sprache zum Abfragen von Cubes verwendet. Eine MDX-Abfrage enthält in der Regel eine Datendefinition, die eine oder mehrere Dimensionen und mindestens ein Measure enthält, obwohl MDX-Abfragen deutlich komplexer abrufen können und parallelen Windows, kumulative Durchschnittswerte, Summen, Ränge oder Perzentile umfassen. 

Hier sind einige andere Begriffe, die beim Erstellen von MDX-Abfragen hilfreich sein können:

+ *Aufteilen in Slices* nimmt eine Teilmenge des Cubes mithilfe von Werten aus einer einzelnen Dimension.

+ *Dicing* (Teilwürfel) erstellt einen Teilwürfel durch Angabe eines Wertebereichs für mehrere Dimensionen.

+ *Drilldown* navigiert von einer Zusammenfassung zu Detailinformationen.

+ *Drillup* bezeichnet die Bewegung von Details zu einer höheren Aggregationsstufe.

+ *Rollup* fasst die Daten für eine Dimension zusammen.

+ Beim*Pivotieren* wird der Würfel oder die Datenauswahl gedreht.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>Wie Erstellen von MDX-Abfragen mit olapR

Der folgende Artikel bietet Ausführliche Beispiele für die Syntax zum Erstellen oder Ausführen von Abfragen für einen Cube:

+ [Vorgehensweise: Erstellen von MDX-Abfragen mithilfe von R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>OlapR API

Das **olapR** -Paket unterstützt zwei Methoden zum Erstellen von MDX-Abfragen:

- **Verwenden Sie den MDX-Generator.** Verwenden Sie die R-Funktionen im Paket, um eine einfache MDX-Abfrage zu generieren, indem Sie einen Cube auswählen und dann festlegen, Achsen und Datenschnitte. Dies ist eine einfache Möglichkeit, eine gültige MDX-Abfrage zu erstellen, wenn Sie keinen Zugriff auf herkömmlichen OLAP-Tools oder tiefgreifende der MDX-Sprache Kenntnis.

    Nicht alle MDX-Abfragen können mithilfe dieser Methode erstellt werden, da MDX komplex sein kann. Diese API unterstützt jedoch die meisten Vorgänge häufigste und nützlichste, einschließlich Slice, Dice, Drilldown, Rollup und Pivot in N-Dimensionen.

+ **Fügen Sie kopieren und wohlgeformte MDX ein.** Erstellen Sie manuell, und fügen Sie in einer MDX-Abfrage. Diese Option ist die am besten, wenn Sie vorhandene MDX-Abfragen verfügen, die Sie wiederverwenden möchten oder wenn die Abfrage, die Sie erstellen möchten, zu komplex für ist **OlapR** behandelt.

    Nach dem Erstellen Ihrer MDX mithilfe beliebiger Clienthilfsprogramme wie SSMS oder Excel, speichern Sie die Abfragezeichenfolge ein. Geben Sie diese MDX-Zeichenfolge als Argument an die *Handler für die Abfrage von SSAS* in die **OlapR** Paket. Der Anbieter sendet die Abfrage an den angegebenen Analysis Services-Server und übergibt die Ergebnisse in R. 

Beispiele zum Erstellen einer MDX Abfragen oder zum Ausführen vorhandenen MDX-Abfragen, finden Sie unter [Vorgehensweise: Erstellen von MDX-Abfragen mithilfe von R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Bekannte Probleme

Dieser Abschnitt enthält einige bekannte Probleme und häufig gestellte Fragen zu den **OlapR** Paket.

### <a name="tabular-model-support"></a>Unterstützung für tabellarische Modelle

Wenn Sie eine Verbindung mit einer Instanz von Analysis Services herstellen, die ein tabellarisches Modell enthält die `explore` -Funktion meldet Erfolg mit dem Wert "true" zurück. Allerdings tabellenmodellobjekte unterscheiden sich von mehrdimensionalen Objekten und die Struktur einer mehrdimensionalen Datenbank unterscheidet sich von der ein tabellarisches Modell.

Obwohl DAX (Data Analysis Expressions), die in der Regel mit tabellarischen Modellen verwendete Sprache ist, können Sie gültige MDX-Abfragen für ein tabellarisches Modell entwerfen, wenn Sie bereits mit MDX vertraut sind. Die OlapR Konstruktoren können keine gültigen MDX-Abfragen für ein tabellarisches Modell erstellen.

MDX-Abfragen sind jedoch eine ineffiziente Möglichkeit zum Abrufen von Daten aus einem tabellarischen Modell. Wenn Sie zum Abrufen von Daten aus einem tabellarischen Modell für die Verwendung in R benötigen, erwägen Sie stattdessen diese Methoden:

+ Aktivieren von DirectQuery für das Modell, und fügen Sie den Server als Verbindungsserver in SQL Server. 
+ Wenn das tabellarische Modell auf einem relationalen Datamart erstellt wurde, werden rufen Sie die Daten direkt aus der Quelle ab.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Gewusst wie: bestimmen, ob eine Instanz tabellarische oder mehrdimensionale Modelle enthält.

Eine einzelne Analysis Services-Instanz kann nur ein Typ von Modell enthalten, obwohl sie mehrere Modelle enthalten kann. Der Grund ist, dass es grundlegende Unterschiede zwischen tabellarischen Modellen und mehrdimensionale Modelle, die steuern, wie Daten gespeichert und verarbeitet werden. Beispielsweise tabellarische Modelle werden im Arbeitsspeicher gespeichert und Nutzen von columnstore-Indizes, um schnell Berechnungen durchzuführen. In mehrdimensionalen Modellen Daten auf dem Datenträger gespeichert und Aggregationen im Voraus definiert und mithilfe von MDX-Abfragen abgerufen werden.

Wenn Sie eine Verbindung mit Analysis Services mit einem Client z. B. SQL Server Management Studio herstellen, können Sie einen Blick feststellen, welcher Modelltyp unterstützt wird, indem Sie das Symbol für die Datenbank ansehen.

Sie können auch anzeigen, und Fragen Sie die Servereigenschaften, um zu bestimmen, welche Art von Modell die Instanz unterstützt. Die **Servermodus** -Eigenschaft unterstützt zwei Werte: _mehrdimensionale_ oder _tabellarische_.

Finden Sie allgemeine Informationen zu den zwei Arten von Modellen im folgenden Artikel:

+ [Mehrdimensionale und tabellarische Modelle vergleichen](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Finden Sie im folgenden Artikel Informationen zum Abfragen von Eigenschaften aus:

+ [OLE DB für OLAP-Schemarowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>Rückschreiben von Kennwörtern wird nicht unterstützt.

Es ist nicht möglich, um die Ergebnisse von benutzerdefinierten R-Berechnungen wieder in den Cube zu schreiben.

Im Allgemeinen auch, wenn Sie ein Cube für das Rückschreiben aktiviert ist, wird nur eingeschränkte Vorgänge werden unterstützt, und möglicherweise ist zusätzliche Konfiguration erforderlich. Es wird empfohlen, dass Sie MDX für Vorgänge dieser Art.

+ [Dimensionen mit aktiviertem Schreibzugriff](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitionen mit aktiviertem Schreibzugriff](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Festlegen von benutzerdefiniertem Zugriff auf Zellendaten](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>MDX-Abfragen langer block Cubeverarbeitung

Obwohl die **OlapR** Paket führt nur Lesevorgänge, lang andauernde MDX-Abfragen erstellen sperren, die verhindern, dass den Cube verarbeitet wird. Testen Sie die MDX-Abfragen immer im voraus, damit Sie wissen, wie viele Daten zurückgegeben werden sollen.

Wenn Sie versuchen, eine Verbindung mit einem Cube, die gesperrt wird, erhalten Sie möglicherweise einen Fehler, den das Datawarehouse SQL Server nicht erreicht werden kann. Vorgeschlagene Lösungen umfassen das Aktivieren von Remoteverbindungen, überprüfen den Server oder Instanznamen, und So weiter; sollten Sie aber die Möglichkeit, der eine früheren offene Verbindung.

Eine SSAS-Serveradministrator kann verhindern, dass Sperrungen durch identifizieren und geöffneten Sitzungen beenden. Eine Timeouteigenschaft kann auch MDX-Abfragen auf der Ebene für das erzwungene Beenden aller lang andauernden Abfragen angewendet werden.

## <a name="resources"></a>Ressourcen

Wenn Sie neu in OLAP oder MDX-Abfragen sind, finden Sie unter folgenden Wikipedia-Artikeln: 

+ [OLAP-cubes](https://en.wikipedia.org/wiki/OLAP_cube)
+ [MDX-Abfragen](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
