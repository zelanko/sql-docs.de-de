---
title: Verwenden von Daten aus OLAP-Cubes in R
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ec50ee1b10a51e16b72d7ffc110448dcf016a13f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714973"
---
# <a name="using-data-from-olap-cubes-in-r"></a>Verwenden von Daten aus OLAP-Cubes in R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Das **olapr** -Paket ist ein von Microsoft bereitgestelltes R-Paket für die Verwendung mit Machine Learning Server und SQL Server, mit dem Sie MDX-Abfragen ausführen können, um Daten aus OLAP-Cubes zu erhalten. Mit diesem Paket müssen Sie keine verknüpften Server erstellen oder vereinfachte Rowsets bereinigen. Sie können OLAP-Daten direkt von R erhalten.

In diesem Artikel wird die API zusammen mit einer Übersicht über OLAP und MDX für R-Benutzer beschrieben, die möglicherweise noch nicht mit mehrdimensionalen Cube-Datenbanken neu sind.

> [!IMPORTANT]
> Eine Instanz von Analysis Services kann entweder herkömmliche mehrdimensionale Cubes oder tabellarische Modelle unterstützen, aber eine Instanz kann nicht beide Modelltypen unterstützen. Bevor Sie versuchen, eine MDX-Abfrage für einen Cube zu erstellen, vergewissern Sie sich daher, dass die Analysis Services Instanz mehrdimensionale Modelle enthält.

## <a name="what-is-an-olap-cube"></a>Was ist ein OLAP-Cube?

OLAP ist für die analytische Online Verarbeitung kurz. OLAP-Lösungen werden häufig zum Erfassen und Speichern wichtiger Geschäftsdaten im Zeitverlauf verwendet. OLAP-Daten werden von einer Vielzahl von Tools, Dashboards und Visualisierungen für Business Analytics genutzt. Weitere Informationen finden Sie unter [analytische Online Verarbeitung](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft stellt [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services)bereit, mit dem Sie OLAP-Daten in Form von _Cubes_ oder _tabellarischen Modellen_entwerfen, bereitstellen und Abfragen können. Ein Cube ist eine Mehrdimensionale Datenbank. _Dimensionen_ sind wie Facetten der Daten oder Faktoren in R: Sie verwenden Dimensionen, um eine bestimmte Teilmenge von Daten zu identifizieren, die Sie zusammenfassen oder analysieren möchten. Beispielsweise ist Time eine wichtige Dimension, sodass viele OLAP-Lösungen mehrere standardmäßig definierte Kalender enthalten, die beim aufteilen und Zusammenfassen von Daten verwendet werden können. 

Aus Leistungsgründen berechnet eine OLAP-Datenbank häufig Zusammenfassungen (oder _Aggregationen_) im voraus und speichert Sie dann für einen schnelleren Abruf. Zusammenfassungen basieren auf *Measures*, die Formeln darstellen, die auf numerische Daten angewendet werden können. Verwenden Sie die Dimensionen, um eine Teilmenge der Daten zu definieren, und berechnen Sie dann das Measure über diese Daten. Beispielsweise verwenden Sie ein Measure, um den Gesamtumsatz für eine bestimmte Produktlinie über mehrere Quartale abzüglich der Steuern zu berechnen, um die durchschnittlichen Versandkosten für einen bestimmten Lieferanten, die kostenpflichtigen laufenden kumulativen Kosten usw. zu berechnen.

MDX, Short für mehrdimensionale Ausdrücke, ist die Sprache, die zum Abfragen von Cubes verwendet wird. Eine MDX-Abfrage enthält in der Regel eine Datendefinition, die mindestens eine Dimension enthält, und mindestens ein Measure, obwohl MDX-Abfragen erheblich komplexer werden können, und umfasst parallele Fenster, kumulative Durchschnittswerte, Summen, Ränge oder Quantilen. 

Im folgenden finden Sie einige andere Begriffe, die beim Entwickeln von MDX-Abfragen hilfreich sein können:

+ Beim *Slicing* wird eine Teilmenge des Cubes verwendet, indem Werte aus einer einzelnen Dimension verwendet werden.

+ *Dicing* (Teilwürfel) erstellt einen Teilwürfel durch Angabe eines Wertebereichs für mehrere Dimensionen.

+ *Drilldown* navigiert von einer Zusammenfassung zu Detailinformationen.

+ *Drillup* bezeichnet die Bewegung von Details zu einer höheren Aggregationsstufe.

+ *Rollup* fasst die Daten für eine Dimension zusammen.

+ Beim*Pivotieren* wird der Würfel oder die Datenauswahl gedreht.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>Verwenden von olapr zum Erstellen von MDX-Abfragen

Der folgende Artikel enthält ausführliche Beispiele für die Syntax zum Erstellen oder Ausführen von Abfragen für einen Cube:

+ [Erstellen von MDX-Abfragen mithilfe von R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapr-API

Das **olapR** -Paket unterstützt zwei Methoden zum Erstellen von MDX-Abfragen:

- **Verwenden Sie den MDX-Generator.** Verwenden Sie die R-Funktionen im Paket, um eine einfache MDX-Abfrage zu generieren. Wählen Sie dazu einen Cube aus, und legen Sie dann Achsen und Slicer fest. Dies ist eine einfache Möglichkeit, eine gültige MDX-Abfrage zu erstellen, wenn Sie keinen Zugriff auf herkömmliche OLAP-Tools haben oder nicht über umfassende Kenntnisse der MDX-Sprache verfügen.

    Nicht alle MDX-Abfragen können mit dieser Methode erstellt werden, da MDX komplex sein kann. Diese API unterstützt jedoch die meisten der gängigsten und nützlichsten Vorgänge, einschließlich Slice, Würfel, Drilldown, Rollup und Pivot in N-Dimensionen.

+ **Kopieren und Einfügen wohlgeformter MDX.** Erstellen Sie manuell eine MDX-Abfrage, und fügen Sie Sie dann ein. Diese Option ist am besten geeignet, wenn MDX-Abfragen vorhanden sind, die Sie wieder verwenden möchten, oder wenn die Abfrage, die Sie erstellen möchten, für die Verarbeitung durch **olapr** zu komplex ist.

    Nachdem Sie die MDX-Datei mit einem beliebigen Client Hilfsprogramm wie SSMS oder Excel aufgebaut haben, speichern Sie die Abfrage Zeichenfolge. Stellen Sie diese MDX-Zeichenfolge als Argument für den *SSAS-Abfrage Handler* im **olapr** -Paket bereit. Der Anbieter sendet die Abfrage an den angegebenen Analysis Services Server und übergibt die Ergebnisse an R. 

Beispiele zum Erstellen einer MDX-Abfrage oder zum Ausführen einer vorhandenen MDX-Abfrage finden [Sie unter Erstellen von MDX-Abfragen mithilfe von R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Bekannte Probleme

In diesem Abschnitt werden einige bekannte Probleme und häufig gestellte Fragen zum **olapr** -Paket aufgelistet.

### <a name="tabular-model-support"></a>Unterstützung von Tabellen Modellen

Wenn Sie eine Verbindung mit einer Instanz von Analysis Services herstellen, die ein tabellarisches `explore` Modell enthält, meldet die Funktion Erfolg mit dem Rückgabewert true. Tabellarische Modell Objekte unterscheiden sich jedoch von mehrdimensionalen Objekten, und die Struktur einer mehrdimensionalen Datenbank unterscheidet sich von der Struktur eines tabellarischen Modells.

Obwohl DAX (Data Analysis Expressions) die Sprache ist, die in der Regel mit tabellarischen Modellen verwendet wird, können Sie gültige MDX-Abfragen für ein tabellarisches Modell entwerfen, wenn Sie bereits mit MDX vertraut sind. Sie können die olapr-Konstruktoren nicht zum Erstellen gültiger MDX-Abfragen für ein tabellarisches Modell verwenden.

MDX-Abfragen sind jedoch eine ineffiziente Methode zum Abrufen von Daten aus einem tabellarischen Modell. Wenn Sie Daten aus einem tabellarischen Modell für die Verwendung in R benötigen, sollten Sie stattdessen diese Methoden in Erwägung gezogen werden:

+ Aktivieren Sie directquery für das Modell, und fügen Sie den Server in SQL Server als Verbindungs Server hinzu. 
+ Wenn das tabellarische Modell auf einer relationalen Data Mart erstellt wurde, können Sie die Daten direkt aus der Quelle abrufen.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Bestimmen, ob eine Instanz tabellarische oder mehrdimensionale Modelle enthält

Eine einzelne Analysis Services Instanz kann nur einen Modelltyp enthalten, Sie kann jedoch mehrere Modelle enthalten. Der Grund hierfür sind grundlegende Unterschiede zwischen tabellarischen Modellen und mehrdimensionalen Modellen, die Steuern, wie Daten gespeichert und verarbeitet werden. Tabellarische Modelle werden z. b. im Arbeitsspeicher gespeichert und nutzen columnstore--Indizes, um sehr schnelle Berechnungen auszuführen. In mehrdimensionalen Modellen werden Daten auf dem Datenträger gespeichert, und Aggregationen werden im Voraus definiert und mithilfe von MDX-Abfragen abgerufen.

Wenn Sie mithilfe eines Clients wie SQL Server Management Studio eine Verbindung mit Analysis Services herstellen, können Sie auf einen Blick feststellen, welcher Modelltyp unterstützt wird, indem Sie sich das Symbol für die Datenbank ansehen.

Sie können auch die Server Eigenschaften anzeigen und Abfragen, um zu bestimmen, welcher Modelltyp von der Instanz unterstützt wird. Die servermoduseigenschaft unterstützt zwei Werte: mehr _dimensional_ oder _Tabellarisch_.

Allgemeine Informationen zu den beiden Modelltypen finden Sie im folgenden Artikel:

+ [Vergleichen von mehrdimensionalen und tabellarischen Modellen](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Weitere Informationen zum Abfragen von Server Eigenschaften finden Sie im folgenden Artikel:

+ [OLE DB für OLAP-Schemarowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>Das Rück schreiben wird nicht unterstützt.

Es ist nicht möglich, die Ergebnisse von benutzerdefinierten R-Berechnungen wieder in den Cube zu schreiben.

Im Allgemeinen werden nur eingeschränkte Vorgänge unterstützt, auch wenn ein Cube für das Rück schreiben aktiviert ist, und möglicherweise ist eine zusätzliche Konfiguration erforderlich. Es wird empfohlen, MDX für solche Vorgänge zu verwenden.

+ [Dimensionen mit aktiviertem Schreibzugriff](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitionen mit aktiviertem Schreibzugriff](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Festlegen des benutzerdefinierten Zugriffs auf Zelldaten](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>MDX-Abfragen mit langer Ausführungszeit blockieren die Cubeverarbeitung

Obwohl das **olapr** -Paket nur Lesevorgänge ausführt, können MDX-Abfragen mit langer Ausführungszeit Sperren erstellen, die die Verarbeitung des Cubes verhindern. Testen Sie die MDX-Abfragen immer im voraus, damit Sie wissen, wie viele Daten zurückgegeben werden sollen.

Wenn Sie versuchen, eine Verbindung mit einem gesperrten Cube herzustellen, erhalten Sie möglicherweise eine Fehlermeldung, dass der SQL Server Data Warehouse nicht erreicht werden kann. Vorgeschlagene Lösungen sind u. a. das Aktivieren von Remote Verbindungen, das Überprüfen des Server-oder Instanznamens usw. berücksichtigen Sie jedoch die Möglichkeit einer vorherigen geöffneten Verbindung.

Ein SSAS-Administrator kann Sperr Probleme vermeiden, indem er geöffnete Sitzungen identifiziert und beendet. Eine Timeout-Eigenschaft kann auch auf MDX-Abfragen auf Serverebene angewendet werden, um die Beendigung aller Abfragen mit langer Ausführungsdauer zu erzwingen.

## <a name="resources"></a>Ressourcen

Wenn Sie noch nicht mit OLAP-oder MDX-Abfragen vertraut sind, lesen Sie die folgenden Wikipedia-Artikel: 

+ [OLAP-Cubes](https://en.wikipedia.org/wiki/OLAP_cube)
+ [MDX-Abfragen](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
