---
title: Verwenden von Daten aus OLAP-Cubes in R
description: Dieser Artikel enthält eine Beschreibung der olapR-API sowie eine Übersicht über OLAP und MDX für R-Benutzer, denen mehrdimensionale Cube-Datenbanken möglicherweise noch nicht vertraut sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2da5cbf0fd3fbc5b8fe1105261fff98625d590e5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727317"
---
# <a name="using-data-from-olap-cubes-in-r"></a>Verwenden von Daten aus OLAP-Cubes in R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Das **olapR**-Paket ist ein R-Paket, das von Microsoft zur Verwendung mit Machine Learning Server und SQL Server bereitgestellt wird und mit dem Sie MDX-Abfragen zum Abrufen von Daten aus OLAP-Cubes ausführen können. Mit diesem Paket brauchen Sie keine Verbindungsserver zu erstellen oder vereinfachte Rowsets zu bereinigen, sondern können OLAP-Daten direkt aus R abrufen.

Dieser Artikel enthält eine Beschreibung der API sowie eine Übersicht über OLAP und MDX für R-Benutzer, denen mehrdimensionale Cube-Datenbanken möglicherweise noch nicht vertraut sind.

> [!IMPORTANT]
> Eine Instanz von Analysis Services kann entweder herkömmliche mehrdimensionale Cubes oder tabellarische Modelle unterstützen, jedoch nicht beide Modelltypen. Bevor Sie versuchen, eine MDX-Abfrage für einen Cube zu erstellen, vergewissern Sie sich daher, dass die Analysis Services-Instanz mehrdimensionale Modelle enthält.

## <a name="what-is-an-olap-cube"></a>Was ist ein OLAP-Cube?

OLAP ist die Kurzform für Online Analytical Processing (analytische Onlineverarbeitung). OLAP-Lösungen werden häufig zum Erfassen und Speichern wichtiger Unternehmensdaten im Zeitverlauf verwendet. OLAP-Daten werden von einer Vielzahl von Tools, Dashboards und Visualisierungen für Business Analytics genutzt. Weitere Informationen finden Sie unter [Analytische Onlineverarbeitung (OLAP)](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft stellt [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services) bereit, mit denen Sie OLAP-Daten in Form von _Cubes_ oder _tabellarischen Modellen_ entwerfen, bereitstellen und abfragen können. Ein Cube ist eine mehrdimensionale Datenbank. _Dimensionen_ sind wie Facetten der Daten oder Faktoren in R: Sie verwenden Dimensionen, um eine bestimmte Teilmenge von Daten anzugeben, die Sie zusammenfassen oder analysieren möchten. Beispielsweise ist Zeit eine sehr wichtige Dimension, sodass viele OLAP-Lösungen mehrere standardmäßig definierte Kalender enthalten, die beim Aufteilen und Zusammenfassen von Daten verwendet werden können. 

Aus Leistungsgründen berechnet eine OLAP-Datenbank häufig Zusammenfassungen (oder _Aggregationen_) im Voraus und speichert diese dann für einen schnelleren Abruf. Zusammenfassungen basieren auf *Measures*, die Formeln zur Anwendung auf numerische Daten darstellen. Sie verwenden die Dimensionen, um eine Teilmenge der Daten zu definieren, und berechnen dann das Measure über diese Daten. Beispielsweise verwenden Sie ein Measure, um den Gesamtumsatz für eine bestimmte Produktlinie über mehrere Quartale abzüglich der Steuern zu berechnen, um die durchschnittlichen Versandkosten für einen bestimmten Lieferanten zu melden, die im laufenden Jahr gezahlten kumulativen Gehälter zu ermitteln usw.

MDX ist die Kurzform für Multidimensional Expressions (mehrdimensionale Ausdrücke) und bezeichnet die Sprache, die zum Abfragen von Cubes verwendet wird. Eine MDX-Abfrage enthält in der Regel eine Datendefinition, die eine oder mehrere Dimensionen umfasst, und mindestens ein Measure, obwohl MDX-Abfragen erheblich komplexer werden und rollierende Zeitfenster, kumulative Durchschnittswerte, Summen, Ränge oder Perzentile umfassen können. 

Nachfolgend sind einige weitere Begriffe aufgeführt, die beim ersten Erstellen von MDX-Abfragen hilfreich sein können:

+ *Slicing* (Aufteilen in Slices) übernimmt eine Teilmenge des Cubes, indem Werte aus einer einzelnen Dimension verwendet werden.

+ *Dicing* (Teilwürfel) erstellt einen Teilwürfel durch Angabe eines Wertebereichs für mehrere Dimensionen.

+ *Drilldown* navigiert von einer Zusammenfassung zu Detailinformationen.

+ *Drillup* bezeichnet die Bewegung von Details zu einer höheren Aggregationsstufe.

+ *Rollup* fasst die Daten für eine Dimension zusammen.

+ Beim*Pivotieren* wird der Würfel oder die Datenauswahl gedreht.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>Verwenden von olapR zum Erstellen von MDX-Abfragen

Der folgende Artikel enthält ausführliche Beispiele für die Syntax zum Erstellen oder Ausführen von Abfragen für einen Cube:

+ [Erstellen von MDX-Abfragen mit R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR-API

Das **olapR** -Paket unterstützt zwei Methoden zum Erstellen von MDX-Abfragen:

- **Verwenden des MDX-Generators.** Verwenden Sie die R-Funktionen im Paket, um eine einfache MDX-Abfrage zu generieren. Wählen Sie dazu einen Cube aus, und legen Sie dann Achsen und Slicer fest. Dies ist eine einfache Methode zum Erstellen einer gültigen MDX-Abfrage, wenn Sie keinen Zugriff auf herkömmliche OLAP-Tools haben oder nicht über tiefgreifende Kenntnis der MDX-Sprache verfügen.

    Nicht alle MDX-Abfragen können mithilfe dieser Methode erstellt werden, da MDX komplex sein kann. Diese API unterstützt jedoch die meisten der gebräuchlichsten und nützlichsten Vorgänge, einschließlich Slice, Dice, Drilldown, Rollup und Pivotieren in N Dimensionen.

+ **Kopieren und Einfügen wohlgeformter MDX-Abfragen.** Erstellen Sie MDX-Abfragen manuell, und fügen Sie diese dann ein. Diese Option eignet sich am besten, wenn Sie vorhandene MDX-Abfragen erneut verwenden möchten oder die Abfrage, die Sie erstellen möchten, zu komplex für **olapR** ist.

    Nachdem Sie die MDX-Abfrage mit einem beliebigen Clienthilfsprogramm wie SSMS oder Excel erstellt haben, speichern Sie die Abfragezeichenfolge. Stellen Sie diese MDX-Zeichenfolge als Argument für den *SSAS-Abfragehandler* im **olapR**-Paket bereit. Der Anbieter sendet die Abfrage an den angegebenen Analysis Services-Server und gibt die Ergebnisse dann an R zurück. 

Beispiele zum Erstellen von MDX-Abfragen oder zum Ausführen vorhandener MDX-Abfragen finden Sie unter [Erstellen von MDX-Abfragen mit R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Bekannte Probleme

In diesem Abschnitt sind einige bekannte Probleme und häufig gestellte Fragen zum **olapR**-Paket aufgelistet.

### <a name="tabular-model-support"></a>Unterstützung tabellarischer Modelle

Wenn Sie eine Verbindung mit einer Instanz von Analysis Services herstellen, die ein tabellarisches Modell enthält, meldet die `explore`-Funktion einen erfolgreichen Abschluss mit dem Rückgabewert TRUE. Die Objekte des tabellarischen Modells unterscheiden sich jedoch von mehrdimensionalen Objekten, und die Struktur einer mehrdimensionalen Datenbank unterscheidet sich von der eines tabellarischen Modells.

Obwohl DAX (Data Analysis Expressions) die Sprache ist, die üblicherweise bei tabellarischen Modellen verwendet wird, können Sie auch gültige MDX-Abfragen für ein tabellarisches Modell entwerfen, wenn Sie bereits mit MDX vertraut sind. Sie können nicht die olapR-Konstruktoren zum Erstellen gültiger MDX-Abfragen für ein tabellarisches Modell verwenden.

MDX-Abfragen stellen jedoch eine ineffiziente Methode zum Abrufen von Daten aus einem tabellarischen Modell dar. Wenn Sie Daten aus einem tabellarischen Modell zur Verwendung in R abrufen müssen, sollten Sie stattdessen die folgenden Methoden in Betracht ziehen:

+ Aktivieren Sie DirectQuery für das Modell, und fügen Sie den Server als Verbindungsserver in SQL Server hinzu. 
+ Wenn das tabellarische Modell auf einem relationalen Data Mart basiert, rufen Sie die Daten direkt aus der Quelle ab.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Bestimmen, ob eine Instanz tabellarische oder mehrdimensionale Modelle enthält

Eine einzelne Analysis Services-Instanz kann nur einen Modelltyp enthalten, jedoch mehrere Modelle. Der Grund dafür sind grundlegende Unterschiede zwischen tabellarischen Modellen und mehrdimensionalen Modellen, die steuern, wie Daten gespeichert und verarbeitet werden. Tabellarische Modelle werden z.B. im Arbeitsspeicher gespeichert und nutzen Columnstore-Indizes, um sehr schnelle Berechnungen auszuführen. In mehrdimensionalen Modellen werden Daten auf dem Datenträger gespeichert, und Aggregationen werden im Voraus definiert und mithilfe von MDX-Abfragen abgerufen.

Wenn Sie mithilfe eines Clients wie SQL Server Management Studio eine Verbindung mit Analysis Services herstellen, können Sie auf einen Blick erkennen, welcher Modelltyp unterstützt wird, indem Sie sich das Symbol für die Datenbank ansehen.

Sie können auch die Servereigenschaften anzeigen und abfragen, um zu bestimmen, welcher Modelltyp von der Instanz unterstützt wird. Die Eigenschaft **Servermodus** unterstützt zwei Werte: _mehrdimensional_ oder _tabellarisch_.

Allgemeine Informationen zu den beiden Modelltypen finden Sie im folgenden Artikel:

+ [Vergleichen von mehrdimensionalen und tabellarischen Modellen](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Informationen zum Abfragen von Servereigenschaften finden Sie im folgenden Artikel:

+ [OLE DB für OLAP-Schemarowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>Rückschreiben wird nicht unterstützt

Es ist nicht möglich, die Ergebnisse von benutzerdefinierten R-Berechnungen in den Cube zurückzuschreiben.

Im Allgemeinen werden auch dann, wenn ein Cube für das Rückschreiben aktiviert ist, nur eingeschränkte Vorgänge unterstützt, und möglicherweise ist eine zusätzliche Konfiguration erforderlich. Es wird empfohlen, MDX für solche Vorgänge zu verwenden.

+ [Dimensionen mit aktiviertem Schreibzugriff](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitionen mit aktiviertem Schreibzugriff](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Festlegen von benutzerdefiniertem Zugriff auf Zellendaten](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>MDX-Abfragen mit langer Ausführungszeit blockieren die Cubeverarbeitung

Obwohl das **olapR**-Paket nur Lesevorgänge ausführt, können MDX-Abfragen mit langer Ausführungszeit Sperren bewirken, die eine Verarbeitung des Cubes verhindern. Testen Sie die MDX-Abfragen immer im Voraus, damit Sie wissen, wie viele Daten zurückgegeben werden sollten.

Wenn Sie versuchen, eine Verbindung mit einem gesperrten Cube herzustellen, erhalten Sie möglicherweise eine Fehlermeldung, dass das SQL Server Data Warehouse nicht erreicht werden kann. Als Lösung wird u.a. vorgeschlagen, Remoteverbindungen zu aktivieren, den Server- oder Instanznamen zu überprüfen usw. Ziehen Sie jedoch auch die Möglichkeit einer zuvor geöffneten Verbindung in Betracht.

Ein SSAS-Administrator kann Sperrprobleme vermeiden, indem er offene Sitzungen erkennt und beendet. Es kann auch eine Timeout-Eigenschaft für MDX-Abfragen auf Serverebene angewendet werden, um die Beendigung aller Abfragen mit langer Ausführungszeit zu erzwingen.

## <a name="resources"></a>Ressourcen

Wenn Sie neu in OLAP oder MDX-Abfragen einsteigen, lesen Sie die folgenden Wikipedia-Artikel: 

+ [OLAP-Cubes](https://en.wikipedia.org/wiki/OLAP_cube)
+ [MDX-Abfragen](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
