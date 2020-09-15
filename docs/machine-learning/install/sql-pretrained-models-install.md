---
title: Installieren von vortrainierten Modellen
description: Fügen Sie vortrainierte Modelle für Standpunktanalysen und Bildfeaturebereitstellungen zu SQL Server Machine Learning Services (R oder Python) oder SQL Server R Services hinzu.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/30/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 86aad616cc8c9fc54adc2fffd14bfc663acf3887
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88179723"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Installieren von vortrainierten Machine Learning-Modellen unter SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

In diesem Artikel wird erläutert, wie einer SQL Server-Instanz mit R- oder Python-Integration mithilfe von PowerShell kostenlose vorinstallierte Machine Learning-Modelle für *Standpunktanalysen* und *Bildfeaturebereitstellungen* hinzugefügt werden. Die vortrainierten Modelle werden von Microsoft erstellt und können einer Instanz im Rahmen einer Aufgabe nach der Installation hinzugefügt werden. Weitere Informationen zu diesen Modellen finden Sie im Abschnitt [Ressourcen](#bkmk_resources) in diesem Artikel.

Nach der Installation werden die vortrainierten Modelle als Implementierungsdetail betrachtet, das bestimmte Funktionen in den Bibliotheken MicrosoftML (R) und microsoftml (Python) unterstützt. Diese Modelle dürfen (und können) nicht angezeigt, angepasst oder erneut trainiert werden. Zudem können sie in benutzerdefiniertem Code oder gekoppelten anderen Funktionen auch nicht als unabhängige Ressource behandelt werden. 

Wenn Sie die vortrainierten Modelle verwenden möchten, rufen Sie die in der folgenden Tabelle aufgeführten Funktionen auf.

| R-Funktion (MicrosoftML) | Python-Funktion (microsoftml) | Verwendung |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Generiert positive/negative Stimmungsbewertungen über Texteingaben. |
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Extrahiert Textinformationen aus Bilddateieingaben. |

## <a name="prerequisites"></a>Voraussetzungen

Machine Learning-Algorithmen sind rechenintensiv. Für geringfügige bis mittlere Arbeitsauslastungen wie etwa für die Durchführung der exemplarischen Vorgehensweisen in den Tutorials mit Nutzung aller Beispieldaten werden 16 GB RAM empfohlen.

Wenn Sie vortrainierte Modelle hinzuzufügen möchten, müssen Sie über Administratorrechte auf dem Computer sowie für SQL Server verfügen.

Externe Skripts müssen aktiviert sein, und der SQL Server LaunchPad-Dienst muss ausgeführt werden. Die Schritte zum Aktivieren und Überprüfen dieser Funktionen sind in den Installationsanleitungen enthalten. 

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Die vortrainierten Modelle sind im [MicrosoftML R-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) oder im [microsoftml Python-Paket](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) enthalten.

[SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md) enthält beide Sprachversionen der Machine Learning-Bibliothek. Diese Voraussetzung ist also erfüllt, ohne dass Sie weitere Maßnahmen ergreifen müssen. Da die Bibliotheken vorhanden sind, können Sie das in diesem Artikel beschriebene PowerShell-Skript verwenden, um diesen Bibliotheken die vortrainierten Modelle hinzuzufügen.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Die vortrainierten Modelle sind im [MicrosoftML R-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) enthalten.

In [SQL Server R Services](sql-r-services-windows-install.md), die es nur in R gibt, ist das [MicrosoftML-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) nicht standardmäßig enthalten. Wenn Sie MicrosoftML hinzufügen möchten, müssen Sie ein [Komponentenupgrade](../install/upgrade-r-and-python.md) durchführen. Ein Komponentenupgrade hat unter anderem den Vorteil, dass die vortrainierten Modelle simultan hinzugefügt werden können, sodass das PowerShell-Skript nicht ausgeführt werden muss. Wenn Sie jedoch bereits ein Upgrade durchgeführt und dabei vergessen haben, die vortrainierten Modelle hinzuzufügen, können Sie das PowerShell-Skript wie in diesem Artikel beschrieben hinzufügen. Dies funktioniert bei beiden Versionen von SQL Server. Vergewissern Sie sich jedoch zuvor, dass die Bibliothek MicrosoftML unter `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library` vorhanden sind.
::: moniker-end

<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Überprüfen, ob vortrainierte Modelle installiert sind

Die Installationspfade für R- und Python-Modelle lauten wie folgt:

+ Für R: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Für Python: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Die Modelldateinamen sind im Folgenden aufgeführt:

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

Wenn die Modelle bereits installiert sind, fahren Sie mit dem [Überprüfungsschritt](#verify), um die Verfügbarkeit zu bestätigen.

## <a name="download-the-installation-script"></a>Herunterladen des Installationsskripts

Klicken Sie auf [https://aka.ms/mlm4sql](https://aka.ms/mlm4sql), um die Datei **Install-MLModels.ps1** herunterzuladen.

## <a name="execute-with-elevated-privileges"></a>Ausführen mit erhöhten Rechten

1. Starten Sie PowerShell. Klicken Sie in der Taskleiste mit der rechten Maustaste auf das PowerShell-Programmsymbol, und wählen Sie **Als Administrator ausführen** aus.
2. Geben Sie einen voll qualifizierten Pfad zur Installationsskriptdatei ein, und beziehen Sie dabei den Instanznamen ein. Wenn Sie den Ordner „Downloads“ und eine Standardinstanz angeben, sieht der Befehl beispielsweise wie folgt aus:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Ausgabe**

Bei einer mit dem Internet verbundenen SQL Server Machine Learning Services-Standardinstanz mit R und Python werden Meldungen wie die folgenden angezeigt.

   ```powershell
   MSSQL14.MSSQLSERVER
        Verifying R models [9.2.0.24]
        Downloading R models [C:\Users\<user-name>\AppData\Local\Temp]
        Installing R models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\]
        Verifying Python models [9.2.0.24]
        Installing Python models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\]
   PS C:\WINDOWS\system32>
   ```

<a name="verify"> </a>

## <a name="verify-installation"></a>Überprüfen der Installation

Prüfen Sie zunächst, ob die neuen Dateien im Ordner [mxlibs](#file-location) vorhanden sind. Führen Sie anschließend Democode aus, um zu prüfen, ob die Modelle installiert und funktionsfähig sind. 

### <a name="r-verification-steps"></a>R-Überprüfungsschritte

1. Starten Sie **RGUI.EXE** unter „C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64“.

2. Fügen Sie das folgende R-Skript an der Eingabeaufforderung ein.

    ```R
    # Create the data
    CustomerReviews <- data.frame(Review = c(
    "I really did not like the taste of it",
    "It was surprisingly quite good!",
    "I will never ever ever go to that place again!!"),
    stringsAsFactors = FALSE)

    # Get the sentiment scores
    sentimentScores <- rxFeaturize(data = CustomerReviews, 
                                    mlTransforms = getSentiment(vars = list(SentimentScore = "Review")))

    # Let's translate the score to something more meaningful
    sentimentScores$PredictedRating <- ifelse(sentimentScores$SentimentScore > 0.6, 
                                            "AWESOMENESS", "BLAH")

    # Let's look at the results
    sentimentScores
    ```

3. Drücken Sie die EINGABETASTE, um die Stimmungsbewertungen anzuzeigen. Die Ergebnisse sollten wie folgt lauten:

    ```R
    > sentimentScores
                                            Review SentimentScore
    1           I really did not like the taste of it      0.4617899
    2                 It was surprisingly quite good!      0.9601924
    3 I will never ever ever go to that place again!!      0.3103435
    PredictedRating
    1            BLAH
    2     AWESOMENESS
    3            BLAH
    ```

### <a name="python-verification-steps"></a>Python-Überprüfungsschritte

1. Starten Sie **Python.exe** unter „C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES“.

2. Fügen Sie das folgende Python-Skript an der Eingabeaufforderung ein.

    ```python
    import numpy
    import pandas
    from microsoftml import rx_logistic_regression, rx_featurize, rx_predict, get_sentiment

    # Create the data
    customer_reviews = pandas.DataFrame(data=dict(review=[
                "I really did not like the taste of it",
                "It was surprisingly quite good!",
                "I will never ever ever go to that place again!!"]))
                
    # Get the sentiment scores
    sentiment_scores = rx_featurize(
        data=customer_reviews,
        ml_transforms=[get_sentiment(cols=dict(scores="review"))])
        
    # Let's translate the score to something more meaningful
    sentiment_scores["eval"] = sentiment_scores.scores.apply(
                lambda score: "AWESOMENESS" if score > 0.6 else "BLAH")
    print(sentiment_scores)
    ```

3. Drücken Sie die EINGABETASTE, um die Bewertungen zu drucken. Die Ergebnisse sollten wie folgt lauten:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Wenn bei Demoskripts ein Fehler auftritt, überprüfen Sie zuerst den Dateispeicherort. Bei Systemen mit mehreren Instanzen von SQL Server oder bei Instanzen, die parallel mit eigenständigen Versionen ausgeführt werden, kann es vorkommen, dass das Installationsskript die Umgebung falsch liest und die Dateien am falschen Speicherort ablegt. Normalerweise wird das Problem durch manuelles Kopieren der Dateien in den richtigen „mxlib“-Ordner behoben.

## <a name="examples-using-pre-trained-models"></a>Beispiele für die Verwendung von vortrainierten Modellen

Über den folgenden Link gelangen Sie zu Codebeispielen zum Aufrufen der vortrainierten Modelle.

+ [Codebeispiel: Standpunktanalyse mithilfe von Textfeaturebereitstellung](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Recherche und Ressourcen

Derzeit sind für die Standpunktanalyse und Bildklassifizierung die DNN-Modelle (Deep Neural Network) verfügbar. Alle vortrainierten Modelle wurden mit dem [Computation Network Toolkit](https://cntk.ai/Features/Index.html) bzw. **CNTK** von Microsoft trainiert.

Die Konfiguration der einzelnen Netzwerke basiert auf den folgenden Verweisimplementierungen:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Weitere Informationen zu den in diesen Deep Learning-Modellen verwendeten Algorithmen sowie zu deren Implementierung und Training mit CNTK finden Sie in den folgenden Artikeln:

+ [Algorithmus von Recherchemitarbeitern bei Microsoft definiert ImageNet Challenge-Meilenstein](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Das Computational Network Toolkit von Microsoft bietet äußerst effiziente verteilte Deep Learning-Rechenleistung](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>Weitere Informationen

+ [SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md)
+ [Upgrade von R- und Python-Komponenten in SQL Server-Instanzen](../install/upgrade-r-and-python.md)
+ [MicrosoftML-Paket für R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [microsoftml-Paket für Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
