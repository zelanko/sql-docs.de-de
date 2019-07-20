---
title: Installieren von vorab trainierten Machine Learning-Modellen
description: Fügen Sie Vortrainierte Modelle für die Stimmungs Analyse und Bild featurearisierung SQL Server 2017 Machine Learning Services (r oder python) oder SQL Server 2016 R Services hinzu.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 2045d6611d5f418a9ed102a1d776080973c08659
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344968"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Installieren von vorab trainierten Machine Learning-Modellen auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie mithilfe von PowerShell kostenlose vorab trainierte Machine Learning-Modelle für die *Stimmungs Analyse* und *Bild featurearisierung* in einer SQL Server Instanz mit R-oder python-Integration hinzufügen. Die vorab trainierten Modelle werden von Microsoft erstellt und können einer Instanz als nach der Installation hinzugefügt werden. Weitere Informationen zu diesen Modellen finden Sie im Abschnitt " [Ressourcen](#bkmk_resources) " in diesem Artikel.

Nach der Installation werden die vorab trainierten Modelle als Implementierungsdetail betrachtet, das bestimmte Funktionen in den MicrosoftML-(R) und MicrosoftML-Bibliotheken (python) unterstellt. Sie sollten die Modelle nicht anzeigen, anpassen oder erneut trainieren, und Sie können Sie auch nicht als unabhängige Ressource in benutzerdefiniertem Code oder in gekoppelten anderen Funktionen behandeln. 

Um die vortrainierten Modelle zu verwenden, rufen Sie die in der folgenden Tabelle aufgeführten Funktionen auf.

| R-Funktion (microsoftml) | Python-Funktion (microsoftml) | Verwendung |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Generiert eine positive negative Stimmungs Bewertung gegenüber Texteingaben. |
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Extrahiert Textinformationen aus Bild Datei Eingaben. |

## <a name="prerequisites"></a>Vorraussetzungen

Machine Learning-Algorithmen sind Rechen intensiv. Es wird empfohlen, 16 GB RAM für Low-to-Mittel-Workloads zu verwenden, einschließlich des Abschlusses der exemplarischen Vorgehensweisen für das Tutorial, das alle Beispiel Daten verwendet.

Sie müssen über Administratorrechte auf dem Computer verfügen und SQL Server, um vorab trainierte Modelle hinzuzufügen.

Externe Skripts müssen aktiviert sein, und SQL Server Launchpad-Dienst muss ausgeführt werden. Installationsanweisungen enthalten die Schritte zum Aktivieren und Überprüfen dieser Funktionen. 

Das [MicrosoftML-R-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) oder das [MicrosoftML-Python-Paket](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) enthält die vorab trainierten Modelle.

+ [SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md) enthält beide Sprachversionen der Machine Learning-Bibliothek. diese Voraussetzung wird also ohne weitere Aktion in Ihrem Bereich erfüllt. Da die Bibliotheken vorhanden sind, können Sie das in diesem Artikel beschriebene PowerShell-Skript verwenden, um diesen Bibliotheken die vorab trainierten Modelle hinzuzufügen.

+ [SQL Server 2016 r Services](sql-r-services-windows-install.md), d. h. nur R, enthält kein [microsoftml-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) . Zum Hinzufügen von microsoftml müssen Sie ein [Komponenten Upgrade](../install/upgrade-r-and-python.md)durchführen. Ein Vorteil des Komponenten Upgrades besteht darin, dass Sie die vorab trainierten Modelle gleichzeitig hinzufügen können, sodass die Ausführung des PowerShell-Skripts unnötig ist. Wenn Sie jedoch bereits ein Upgrade durchgeführt haben, aber das Hinzufügen der vorab trainierten Modelle beim ersten Mal verpasst haben, können Sie das PowerShell-Skript ausführen, wie in diesem Artikel beschrieben. Dies funktioniert für beide Versionen von SQL Server. Vergewissern Sie sich, dass die microsoftml-Bibliothek unter c:\Programme\Microsoft SQL server\mssql13. vorhanden ist. MSSQLSERVER\R_SERVICES\library.


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Überprüfen, ob Vortrainierte Modelle installiert sind

Die Installations Pfade für R-und python-Modelle lauten wie folgt:

+ Für R:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Für python:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Modell Dateinamen sind unten aufgeführt:

+ Alexnet\_aktualisiert. Modell
+ ImageNet1K\_Mean. XML
+ pretrained.model
+ RESNET\_101\_aktualisiert. Modell
+ RESNET\_18\_aktualisiert. Modell
+ RESNET\_50\_aktualisiert. Modell

Wenn die Modelle bereits installiert sind, fahren Sie mit dem Überprüfungs [Schritt](#verify) fort, um die Verfügbarkeit zu bestätigen.

## <a name="download-the-installation-script"></a>Herunterladen des Installations Skripts

Klicken [https://aka.ms/mlm4sql](https://aka.ms/mlm4sql) Sie hier, um die Datei **install-MLModels. ps1**herunterzuladen.

## <a name="execute-with-elevated-privileges"></a>Ausführen mit erhöhten Rechten

1. Starten Sie PowerShell. Klicken Sie in der Taskleiste mit der rechten Maustaste auf das PowerShell-Programmsymbol, und wählen Sie **als Administrator ausführen**aus.
2. Geben Sie einen voll qualifizierten Pfad zur Installationsskript Datei ein, und schließen Sie den Instanznamen ein. Wenn der Ordner Downloads und eine Standard Instanz angenommen werden, könnte der Befehl wie folgt aussehen:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Ausgabe**

Bei einem SQL Server 2017 Machine Learning Standard Instanz mit Internetverbindung mit R und python sollten Meldungen ähnlich der folgenden angezeigt werden.

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

Überprüfen Sie zunächst, ob die neuen Dateien im [Ordner "mxlisb](#file-location)" angezeigt werden. Führen Sie anschließend Democode aus, um zu bestätigen, dass die Modelle installiert und funktionsfähig sind. 

### <a name="r-verification-steps"></a>R-Überprüfungs Schritte

1. Starten Sie die **rgui. EXE** unter c:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES\bin\x64.

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

3. Drücken Sie die EINGABETASTE, um die Stimmungs Ergebnisse anzuzeigen. Die Ausgabe sollte wie folgt lauten:

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

### <a name="python-verification-steps"></a>Python-Überprüfungs Schritte

1. Starten Sie " **python. exe** " unter "c:\Programme\Microsoft SQL server\mssql14.". MSSQLSERVER\PYTHON_SERVICES.

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

3. Drücken Sie die EINGABETASTE, um die Ergebnisse zu drucken. Die Ausgabe sollte wie folgt lauten:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Wenn Demoskripts fehlschlagen, überprüfen Sie zuerst den Datei Speicherort. Bei Systemen mit mehreren Instanzen von SQL Server oder bei Instanzen, die parallel mit eigenständigen Versionen ausgeführt werden, ist es möglich, dass das Installationsskript die Umgebung falsch liest und die Dateien am falschen Speicherort platziert. Normalerweise wird das Problem durch manuelles Kopieren der Dateien in den richtigen mxlib-Ordner behoben.

## <a name="examples-using-pre-trained-models"></a>Beispiele für die Verwendung von vortrainierten Modellen

Der folgende Link enthält Beispielcode zum Aufrufen der vorab trainierten Modelle.

+ [Code Beispiel: Standpunktanalyse mithilfe von Text featurizer](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Forschung und Ressourcen

Derzeit sind die verfügbaren Modelle Deep Neural Network (DNN)-Modelle für die Stimmungs Analyse und Bild Klassifizierung. Alle vorab trainierten Modelle wurden mit dem [Berechnungs Netzwerk-Toolkit](https://cntk.ai/Features/Index.html)von Microsoft oder mit **cntk**trainiert.

Die Konfiguration jedes Netzwerks basiert auf den folgenden Referenzimplementierungen:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Weitere Informationen zu den Algorithmen, die in diesen Deep Learning-Modellen verwendet werden, und wie Sie mit cntk implementiert und trainiert werden, finden Sie in den folgenden Artikeln:

+ [Der Algorithmus von Microsoft-Forschern legt imagenet Challenge Meilenstein fest.](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Das Microsoft compunetwork-Toolkit bietet die effizienteste, verteilte Deep Learning-Rechenleistung.](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>Siehe auch

+ [SQL Server 2016 R-Dienste](sql-r-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md)
+ [Aktualisieren von R-und python-Komponenten in SQL Server Instanzen](../install/upgrade-r-and-python.md)
+ [Microsoftml-Paket für R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [microsoftml-Paket für python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
