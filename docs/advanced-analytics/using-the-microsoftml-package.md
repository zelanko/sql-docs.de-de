---
title: Verwenden des MicrosoftML-Pakets mit SQLServer | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 51ffa33bef7ab880704c9c1391a69feb3e194202
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984562"
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>Verwenden des MicrosoftML-Pakets mit SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die [ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) Paket, die mit Microsoft R Server und SQL Server 2017 bereitgestellt wird, enthält mehrere Machine learning-Algorithmen. Diese APIs, die von Microsoft für interne Machine learning-Anwendungen entwickelt wurden, und wurden die optimierten im Laufe der Jahre zur Unterstützung von hoher Leistung für big Data mit multicore-Verarbeitung und schnelles streaming von Daten. MicrosoftML hinaus zahlreiche Transformationen für Text- und Image-Verarbeitung.

In SQL Server 2017 CTP 2.0 wurde Unterstützung für die Python-Sprache hinzugefügt. Die **Microsoftml** -Paket für Python Funktionen entsprechen denen im des MicrosoftML-Pakets für r enthält. 

+ **MicrosoftML für R**

    Einführung und Paket-Referenz: [MicrosoftML: machine Learning-R-Algorithmen](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    Da R Groß-/Kleinschreibung beachtet wird, stellen Sie sicher, dass Sie den Namen ordnungsgemäß beim Laden des Pakets verweisen.

+ **Microsoftml für Python**

    Einführung und Paket-Referenz: [Microsoftml (Funktion-Bibliothek für Python)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package). 

## <a name="whats-in-microsoftml"></a>Was ist in MicrosoftML

MicrosoftML enthält eine Vielzahl von Machine learning-Algorithmen und Transformationen, die für Leistung optimiert sind.

### <a name="machine-learning-algorithms"></a>Machine Learning-Algorithmen

-  Lineare Modelle: `rxFastLinear` basiert ein lineares lernmodul auf stochastischen dual-Koordinate Ascent, die für binäre Klassifizierung oder Regression verwendet werden kann. Das Modell unterstützt L1- und L2-Regularisierung.

- Decision Tree und Decision Forest-Modelle: `rxFastTree` ist ein boosted Decision Tree-Algorithmus, die ursprünglich als FastRank bezeichnet wurde, die für die Verwendung in Bing entwickelt wurde. Es ist eins der schnellsten und am häufigsten verwendeten Lernmodule. Es unterstützt binäre Klassifizierung und Regression.

  `rxFastForest` basiert ein Logistisches Regressionsmodell auf der random Forest-Methode. Es ähnelt der `rxLogit` -Funktion in RevoScaleR, unterstützt aber L1- und L2-Regularisierung. Es unterstützt binäre Klassifizierung und Regression.

- Die logistische Regression: `rxLogisticRegression` wird ein Logistisches Regressionsmodell ähnelt der `rxLogit` -Funktion in RevoScaleR mit zusätzlicher Unterstützung für L1- und L2-regularisierung. Unterstützt binäre und mehrklassenklassifizierung.

- Neuronale Netzwerke: die `rxNeuralNet` -Funktion unterstützt binäre Klassifizierung, multiklassenklassifizierung und Regression mit neuronalen Netzwerken. Convoluted Networks mit GPU-Beschleunigung mit einer einzigen GPU Customizable und unterstützt.

- Erkennung von Anomalien.  Die `rxOneClassSvm` Funktion basiert auf der SVM-Methode, jedoch ist für die binäre Klassifikation in unsymmetrischen Datasets optimiert.

### <a name="transformation-functions"></a>Transformationsfunktionen

MicrosoftML enthält zahlreiche spezielle Funktionen, die zum Transformieren von Daten und Extrahieren von Features nützlich sind.

- Funktionen zur Textverarbeitung von sind die `featurizeText` und `getSentiment` Funktionen. Sie können Anzahl der n-gramme, Erkennen der verwendeten Sprache oder Text-Normalisierung auszuführen. Auch können Sie allgemeine Vorgänge wie das Entfernen von Stoppwörtern bereinigen Text ausführen oder generieren Hash oder anzahlbasiert Features aus Text.

- Featureauswahl und Transformationsfunktionen, wie z. B. feature `selectFeatures` oder `getSentiment`, Daten analysieren und Erstellen von Features, die am häufigsten für die Modellierung hilfreich sind.

- Arbeiten mit kategorischen Variablen wie z. B. mit `categorical` oder `categoricalHash`, die konvertiert Kategoriewerte in indizierten Arrays für eine bessere Leistung.

- Spezielle Funktionen für die Verarbeitung und Analyse, wie z. B. `extractPixels` oder `featurizeImage`, können Sie die meisten Informationen zu Images und Bearbeitung von Bildern schneller.

Weitere Informationen finden Sie unter [MicrosoftML functions (Microsoft ML-Funktionen)](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml).

## <a name="how-to-use-microsoftml"></a>Gewusst wie: Verwenden des MicrosoftML

Dieser Abschnitt beschreibt das Suchen und Laden Sie das Paket in Ihrem R und Python-Code.

+ Des MicrosoftML-Pakets für R ist mit Microsoft R Server 9.1.0 und in SQL Server 2017 standardmäßig installiert.

    Es ist auch für die Verwendung mit SQL Server 2016 verfügbar, wenn Sie ein die R-Komponenten für die Instanz Upgrade mit dem Microsoft R Server-Installer, siehe hier: [Aktualisieren einer Instanz von SQL Server mithilfe der Bindung](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ Die **Microsoftml** für Python, wird standardmäßig mit SQL Server 2017 installiert ist-Paket 

   Um dieses Paket zu verwenden, empfehlen wir, dass Sie ein auf Release Candidate 2 oder höher Upgrade. Eine frühe Version RC1 veröffentlicht wurde, aber die Bibliothek einer beträchtlichen Überarbeitung, einschließlich der Änderungen an den Funktionsnamen unterzogen. 

Für R und Python, das Paket jedoch nicht standardmäßig geladen; Daher müssen Sie das Paket als Teil des Codes, seine Funktionen explizit laden.

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>Aufrufen von MicrosoftML-Funktionen von R in SQL Server

Klicken Sie in Ihrem R-Code Laden Sie des MicrosoftML-Pakets zu, und rufen Sie seine Funktionen wie jedes andere Paket.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**Hinweise**

+ Des MicrosoftML-Pakets ist vollständig in der datenverarbeitungspipeline bereitgestellt, die vom RevoScaleR-Paket integriert. Daher können Sie des MicrosoftML-Pakets in beliebigen Windows-basierten rechenkontexten, einschließlich einer Instanz von SQL-Server, auf Machine Learning-Erweiterungen aktiviert ist.

    MicrosoftML erfordert jedoch ein Verweis auf den RevoScaleR und die zugehörigen Funktionen zum Verwenden von remotecomputekontexten.

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>Aufrufen von Microsoftml-Funktionen von Python in SQL Server

Importieren Sie zum Aufrufen von Funktionen aus dem Paket in Ihrem Python-Code der **Microsoftml** -Paket, und importieren Sie **Revoscalepy** remotecomputekontexte oder verknüpfte Verbindung oder die Datenquelle verwendet werden sollen. -Objekte. Klicken Sie dann, verweisen auf den einzelnen Funktionen, die Sie benötigen.

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**Hinweise**

+ In SQL Server 2017 **Microsoftml** ist ein Modul Python35-kompatibel. 

+ Die Funktionen in **Microsoftml** in die Compute-Kontexte und Datenquellen, die von Microsoft Intune integriert sind, **Revoscalepy**. Daher können Sie die **Microsoftml** Python-Paket zu erstellen und Bewerten von Modellen in beliebigen Windows-basierten rechenkontexten, einschließlich einer Instanz von SQL Server, die Machine Learning-Erweiterungen. aktiviert.

    Allerdings **Microsoftml** for Python erfordert, dass einen Verweis auf **Revoscalepy** und ihre Funktionen zum Verwenden von remotecomputekontexten.

Weitere Informationen zu Revoscalepy finden Sie unter:

+ [Was ist Revoscalepy](python/what-is-revoscalepy.md)

+ [die Revoscalepy-Funktion-Bibliothek](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
