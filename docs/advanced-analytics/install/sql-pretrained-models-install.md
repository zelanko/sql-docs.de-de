---
title: Installieren Sie die vorab trainiertes Machine learning-Modelle – SQL Server Machine Learning
description: SQL Server 2017 Machine Learning Services (R oder Python) oder SQL Server 2016 R Services vortrainierte Modelle für Sentiment Analysis "und" Image-featurebereitstellung hinzugefügt.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fe0cfc855f1a231654c3e31ec3924d9754ef4970
ms.sourcegitcommit: c60784d1099875a865fd37af2fb9b0414a8c9550
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58645572"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Installieren von vorab trainierten Machine learning-Modelle in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie Powershell verwenden, um das Hinzufügen von kostenlosen vorab trainierten Machine learning-Modelle für *standpunktanalyse* und *Image featurebereitstellung* , R oder Python-Integration mit SQL Server-Instanz. Die vorab trainierte Modelle werden von Microsoft und sofort zu bedienende, erstellt eine Instanz als Task nach der Installation hinzugefügt. Weitere Informationen zu diesen Modellen finden Sie unter den [Ressourcen](#bkmk_resources) Abschnitt dieses Artikels.

Nach Abschluss der Installation werden die vorab trainierte Modelle ein Implementierungsdetail, die bestimmte Funktionen im MicrosoftML (R) und Microsoftml (Python) Bibliotheken power berücksichtigt. Sie sollten nicht (und kann nicht) anzeigen, anpassen oder die Modelle erneut trainieren, noch kann Sie behandelt sie als unabhängige Ressource in benutzerdefiniertem Code oder anderen Funktionen kombiniert. 

Um die vorab trainierten Modelle zu verwenden, rufen Sie die Funktionen in der folgenden Tabelle aufgeführt sind.

| R-Funktion (MicrosoftML) | Python-Funktion (Microsoftml) | Verwendung |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Negative positiven stimmungswert Texteingaben generiert. |
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Extrahiert Textinformationen aus der Image-Datei-Eingaben. |

## <a name="prerequisites"></a>Erforderliche Komponenten

Machine Learning-Algorithmen, die rechenintensiv sind. Es wird empfohlen, 16 GB RAM für niedrig bis mittlere Workloads, einschließlich der Ergänzung der Tutorial exemplarischen Vorgehensweisen unter Verwendung aller der Beispieldaten.

Sie müssen über Administratorrechte auf dem Computer und SQL Server vorab trainierte Modelle hinzufügen.

Externe Skripts aktiviert werden müssen, und SQL Server LaunchPad-Dienst muss ausgeführt werden. Anweisungen zur Installation geben Sie die Schritte zum Aktivieren und überprüfen diese Funktionen. 

[MicrosoftML-R-Paket](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) oder [Microsoftml-Python-Paket](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) enthalten die vorab trainierte Modelle.

+ [SQL Server 2017-Machine Learning-Dienste](sql-machine-learning-services-windows-install.md) beide Sprachversionen von der Machine Learning-Bibliothek enthält, damit diese Voraussetzung, ohne weitere Aktion Ihrerseits erfüllt ist. Da die Bibliotheken vorhanden sind, können Sie das PowerShell-Skript, das in diesem Artikel beschriebenen verwenden, die vorab trainierte Modelle zur diese Bibliotheken hinzufügen.

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md), d.h. R nur umfasst keine [MicrosoftML-Pakets](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) vorkonfiguriert. Um MicrosoftML hinzuzufügen, müssen Sie eine [Upgrade von Integrationskomponenten](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Ein Vorteil der Aktualisierung der Komponente ein ist, dass Sie gleichzeitig das vorab trainierte Modelle, hinzufügen können, wodurch das Ausführen der PowerShell-Skripts, die nicht erforderlich. Aber wenn Sie bereits ein Upgrade ausgeführt, aber verpasst haben, die vorab trainierte Modelle beim ersten Mal hinzufügen, können Sie das PowerShell-Skript ausführen, wie in diesem Artikel beschrieben. Dies funktioniert für beide Versionen von SQL Server. Vor dem Ausführen, vergewissern Sie sich, dass die MicrosoftML-Bibliothek unter C:\Program Files\Microsoft SQL Server\MSSQL13 vorhanden ist. MSSQLSERVER\R_SERVICES\library.


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Überprüfen Sie, ob das vorab trainierte Modelle installiert sind

Die Installationspfade für R und Python-Modellen lauten wie folgt aus:

+ Für r `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Für Python: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Modell-Dateinamen sind unten aufgeführt:

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

Wenn die Modelle bereits installiert sind, fahren Sie mit der [Überprüfungsschritt](#verify) um Verfügbarkeit zu bestätigen.

## <a name="download-the-installation-script"></a>Laden Sie das Installationsskript

Klicken Sie auf [ https://aka.ms/mlm4sql ](https://aka.ms/mlm4sql) zum Herunterladen der Datei **Install-MLModels.ps1**.

## <a name="execute-with-elevated-privileges"></a>Mit erhöhten Rechten ausführen

1. Starten Sie PowerShell. Klicken Sie auf der Taskleiste mit der rechten Maustaste in des PowerShell-Programm-Symbols, und wählen **als Administrator ausführen**.
2. Geben Sie einen vollqualifizierten Pfad zu der Skriptdatei, und schließen Sie den Instanznamen. Wenn den Ordner "Downloads" und eine Standardinstanz, kann der Befehl wie folgt aussehen:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Ausgabe**

Auf eine Internetverbindung SQL Server 2017-Machine-Learning-Standardinstanz mit R und Python sollte ähnlich der folgenden Meldungen angezeigt werden.

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

Überprüfen Sie zunächst für die neuen Dateien in die [Mxlibs Ordner](#file-location). Führen Sie anschließend die Demo-Code, um sicherzustellen, dass die Modelle installiert und funktionsfähig sind. 

### <a name="r-verification-steps"></a>Überprüfungsschritte für R

1. Starten Sie **RGUI. EXE-Datei** unter C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\bin\x64.

2. Fügen Sie in den folgenden R-Skript an der Eingabeaufforderung ein.

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

3. Drücken Sie EINGABETASTE, um die Stimmung Ergebnisse anzuzeigen. Ausgabe sollte wie folgt aussehen:

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

### <a name="python-verification-steps"></a>Überprüfungsschritte für Python

1. Starten Sie **Python.exe** unter C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES.

2. Fügen Sie in den folgenden Python-Skript an der Eingabeaufforderung

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

3. Drücken Sie EINGABETASTE, um die besten Ergebnisse zu drucken. Ausgabe sollte wie folgt aussehen:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Wenn demoskripts Fehler auftreten, überprüfen Sie zunächst den Dateispeicherort. Auf Systemen müssen Sie mehrere Instanzen von SQL Server oder -Instanzen mit Seite-an-Seite mit eigenständigen Versionen, es ist möglich, dass das Installationsskript falsch Lesen der umgebungs, und platzieren Sie die Dateien im falschen Speicherort. In der Regel manuell die Dateien in den richtigen Mxlib-Ordner kopieren, wird das Problem behebt.

## <a name="examples-using-pre-trained-models"></a>Beispiele zur Verwendung von vorab trainierten Modelle

Im folgende Link enthalten Beispielcode, die die vorab trainierten Modellen aufrufen.

+ [Codebeispiel: Standpunktanalyse mithilfe von Text Featurizer](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Forschung und Ressourcen

Aktuell sind die Modelle, die verfügbar sind, deep neural Networks (DNN) Modelle für Sentiment Analysis und bildklassifizierung. Alle vorab trainierte Modelle trainiert wurden, mithilfe von Microsoft [Berechnung Network Toolkit](https://cntk.ai/Features/Index.html), oder **CNTK**.

Die Konfiguration jedes Netzwerks basiert auf der folgenden referenzimplementierungen:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Weitere Informationen zu den Algorithmen in diese deep Learning-Modelle und ihre Implementierung und trainiert mit CNTK, finden Sie in diesen Artikeln:

+ [Microsoft-Forscher Algorithmus legt ImageNet-Challenge-Meilenstein](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft Computational Network Toolkit bietet die effizienteste verteilte Deep learning-rechenleistung](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>Siehe auch

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md)
+ [SQL Server 2017-Machine Learning-Dienste](sql-machine-learning-services-windows-install.md)
+ [Aktualisieren Sie R- und Python-Komponenten in SQL Server-Instanzen](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
+ [MicrosoftML-Pakets für R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [Microsoftml-Pakets für Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
