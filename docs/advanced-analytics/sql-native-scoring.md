---
title: Native Bewertung in SQL Server-Machine Learning | Microsoft-Dokumentation
description: Generieren von Vorhersagen mit der VORHERSAGE für T-SQL-Funktion, die Bewertung der Dta-Eingaben für ein vorab trainiertes Modell in R oder Python geschrieben sind, auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf8f9a6362b72efddccbf5c2b0e54096c6e86aa7
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2018
ms.locfileid: "40394295"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>Native Bewertung mithilfe der VORHERSAGEN für T-SQL-Funktion
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Sobald Sie ein vorab trainiertes Modell verfügen, können Sie neue Eingabedaten an die Funktion zum Generieren von Vorhersagewerte übergeben oder *Bewertungen*. In SQL Server 2017-Windows oder Linux oder in Azure SQL-Datenbank können die PREDICT-Funktion in Transact-SQL Sie zur Unterstützung der nativen Bewertung. Es erfordert nur, dass Sie ein Modell bereits trainiert wird, verfügen Sie mithilfe von T-SQL-aufrufen können. 

+ Was ist die native Bewertung im Vergleich zu echtzeitbewertung
+ Funktionsweise
+ Unterstützte Plattformen und Anforderungen

## <a name="what-is-native-scoring-and-how-is-it-different-from-real-time-scoring"></a>Was mit der nativen Bewertung ist ein, und wie es von echtzeitbewertung unterscheidet?

In SQL Server 2016 hat Microsoft ein Extensibility Framework, mit dem R-Skripts, die von T-SQL ausgeführt werden kann. Dieses Framework unterstützt bei Vorgängen, die Sie in R, die von einfachen Funktionen bis hin zu Schulungen komplexen Machine learning-Modelle ausführen können. Die Dual-Process-Architektur erfordert jedoch einen externen R-Prozess für jeden Aufruf, unabhängig von der Komplexität des Vorgangs aufgerufen. Wenn Sie ein vorab trainiertes Modell aus einer Tabelle und die Bewertung für diese Daten bereits in SQL Server laden, stellt der Aufwand des Aufrufs des externen Prozess von R eine unnötige Leistungseinbuße dar.

_Bewertung_ ist ein zweistufiger Prozess. Geben Sie Sie zunächst ein vorab trainiertes Modell aus einer Tabelle zu laden. Zweitens übergeben, die neuen Eingabedaten an die Funktion zum Generieren von Werten der Vorhersage (oder _Bewertungen_). Die Eingabe kann entweder tabellarisch oder einzelne Zeilen sein. Sie können auch Ausgabe einen einzelne Spalte-Wert, die Wahrscheinlichkeit darstellt, oder Sie möglicherweise mehrere Werte, z. B. eines Konfidenzintervalls, Fehler oder andere nützliche Ergänzung der Vorhersage ausgegeben.

Wenn die Eingabe viele Zeilen mit Daten enthält, ist es in der Regel schneller, die Vorhersagewerte im Rahmen der Bewertung in eine Tabelle einzufügen.  Generieren ein einzelnes Ergebnis ist ein üblicher in einem Szenario, in dem Sie Eingabewerte aus einem Formular oder einer benutzeranforderung, und das Ergebnis an eine Clientanwendung zurück. Zur Verbesserung der Leistung beim aufeinander folgenden Bewertungen zu generieren, kann SQL Server das Modell zwischenspeichern, damit sie in den Arbeitsspeicher neu geladen werden kann.

Zur Unterstützung von schnellen Bewertung die SQL Server-Machine Learning-Dienste (und Microsoft Machine Learning Server), geben Sie die integrierten bewertungsbibliotheken, die in R oder T-SQL zu arbeiten. Es gibt verschiedene Optionen, je nachdem, welche, die Version Sie verfügen.

**Native Bewertung**

+ Die PREDICT-Funktion in Transact-SQL unterstützt _nativen Bewertung_ in jeder Instanz von SQL Server 2017. Es erfordert nur, dass Sie ein Modell bereits trainiert wird, verfügen Sie mithilfe von T-SQL-aufrufen können. Native Bewertung mit T-SQL bietet folgende Vorteile:

    + Es ist keine zusätzliche Konfiguration erforderlich.
    + Die R-Laufzeit wird nicht aufgerufen. Besteht keine Notwendigkeit zur Installation von r

**Echtzeitbewertung**

+ **Sp_rxPredict** ist eine gespeicherte Prozedur aus, für die echtzeitbewertung, die verwendet werden können Ergebnisse aus jedem unterstützten Modelltyp generiert, ohne Aufrufen der R-Laufzeit.

  Diese gespeicherte Prozedur wird auch in SQL Server 2016 verfügbar, wenn Sie ein upgrade die R-Komponenten, die mit dem eigenständigen Installer von Microsoft R Server. Sp_rxPredict wird auch in SQL Server 2017 unterstützt. Aus diesem Grund können Sie diese Funktion verwenden, beim Generieren von Bewertungen mit einem Modelltyp, der von der PREDICT-Funktion nicht unterstützt.

+ Die RxPredict-Funktion kann verwendet werden, für die schnelle Bewertung in R-Code.

Für alle dieser Bewertungsmethoden müssen Sie ein Modell verwenden, die mit einer der unterstützten Revoscaler- oder MicrosoftML Algorithmen trainiert wurde.

Ein Beispiel für die echtzeitbewertung in Aktion, finden Sie unter [End-to-End Loan Kreditabschreibungen Vorhersage erstellt mithilfe von Azure HDInsight Spark-Cluster und SQL Server 2016 R Services](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>Wie systemeigene Bewertung funktioniert

Native Bewertung verwendet die systemeigene C++-Bibliotheken von Microsoft, die das Modell aus einer speziellen Binärformat zu lesen und Generieren von Bewertungen können. Da ein Modell veröffentlicht und für die Bewertung ohne Aufruf von R-Interpreter verwendet werden kann, wird der Mehraufwand für mehrere Prozess-Interaktionen reduziert. Daher unterstützt die nativen Bewertung wesentlich schnellere vorhersageleistung in Produktionsszenarien Enterprise.

Zum Generieren von Bewertungen, die diese Bibliothek verwenden, rufen Sie die bewertungs-Funktion, und übergeben die folgenden erforderlichen Eingaben:

+ Ein kompatibles Modell. Finden Sie unter den [Anforderungen](#Requirements) finden Sie Details.
+ Eingabedaten als SQL-Abfrage in der Regel definiert.

Die Funktion gibt die Vorhersagen für die Eingabedaten, sowie alle Spalten der Quelldaten, denen Sie durchlaufen möchten.

Codebeispiele zusammen mit Anweisungen zur Vorbereitung der Modelle in das Binärformat erforderlich ist, finden Sie im Artikel:

+ [Echtzeitbewertung ausführen](r/how-to-do-realtime-scoring.md)

Eine vollständige Lösung, die enthält nativen Bewertung, finden Sie in diesen Beispielen aus dem SQL Server-Entwicklungsteam:

+ Stellen Sie Ihre ML-Skript: [mit einem Python-Modell](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ Stellen Sie Ihre ML-Skript: [mithilfe eines R-Modells](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)

## <a name="requirements"></a>Anforderungen

Unterstützte Plattformen sind wie folgt aus:

+ SQL Server 2017 Machine Learning Services (einschließlich Microsoft R Server 9.1.0)
    
    Verwenden von PREDICT nativen Bewertung erfordert SQL Server 2017.
    Dies funktioniert auf einer beliebigen Version von SQL Server 2017, einschließlich Linux.

    Sie können auch echtzeitbewertung mit Sp_rxPredict ausführen. Verwenden Sie diese gespeicherte Prozedur erfordert das Aktivieren des [SQL Server-CLR-Integration](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration).

+ SQL Server 2016

   Echtzeitbewertung mit Sp_rxPredict mit SQL Server 2016 möglich ist, und kann auch zu Microsoft R Server ausgeführt werden. Diese Option erfordert SQLCLR aktiviert werden soll, und dass Sie das Microsoft R Server-Upgrade zu installieren.
   Weitere Informationen finden Sie unter [in Echtzeit bewerten](Real-time-scoring.md)

### <a name="model-preparation"></a>Modellvorbereitung

+ Das Modell muss mithilfe einer der unterstützten im Voraus trainiert werden **Rx** Algorithmen. Weitere Informationen finden Sie unter [unterstützt Algorithmen](#bkmk_native_supported_algos).
+ Das Modell muss gespeichert werden, mithilfe der neuen Serialisierungsfunktion, die in Microsoft R Server 9.1.0 bereitgestellt. Die Serialisierungsfunktion ist optimiert, um schnelle Bewertung zu unterstützen.

### <a name="bkmk_native_supported_algos"></a> Algorithmen, die nativen Bewertung unterstützen

+ RevoScaleR-Modelle

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

Wenn Sie Modelle auf der Grundlage MicrosoftML verwenden müssen, verwenden Sie die echtzeitbewertung mit Sp_rxPredict.

### <a name="restrictions"></a>Restrictions

Die folgenden Modelltypen werden nicht unterstützt:

+ Modelle, die mit anderen, nicht unterstützte Typen von R-Transformationen
+ Modelle mit den `rxGlm` oder `rxNaiveBayes` Algorithmen in RevoScaleR
+ PMML-Modelle
+ Mit anderen R-Bibliotheken über CRAN oder andere Repositorys erstellte Modelle
+ Modelle mit jedem anderen R-transformation

## <a name="see-also"></a>Siehe auch

[Echtzeitbewertung in SQL Server-Machine learning ](real-time-scoring.md)