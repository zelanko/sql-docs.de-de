---
title: Wie echtzeitbewertung oder nativen Bewertung in SQL Server-Machine Learning | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dfea308f268d666ce070c21a7dd9afa513f95406
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2018
ms.locfileid: "40393233"
---
# <a name="how-to-perform-real-time-scoring-or-native-scoring-in-sql-server"></a>Echtzeitbewertung oder nativen Bewertung in SQL Server ausführen.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird veranschaulicht, dass es sich bei beiden Ansätzen ist in SQL Server für die Vorhersage von Ergebnissen in Echtzeit mithilfe von vorab trainierte Modelle, die in r geschrieben in der Nähe Sowohl echtzeitbewertung nativen Bewertung sind darauf ausgelegt, können Sie ein Machine learning-Modell ohne Installation von r verwenden. Erhalten ein vorab trainiertes Modell in einem kompatiblen Format - gespeichert, die mit einer SQL Server-Datenbank - können standard Datenzugriffsverfahren Sie zum schnellen Generieren von vorhersagebewertungen für neue Eingaben.

## <a name="choose-a-scoring-method"></a>Wählen Sie eine Bewertungsmethode

Die folgenden Optionen sind für schnelle batchvorhersage unterstützt:

+ **Native Bewertung**: T-SQL PREDICT-Funktion in SQL Server 2017-Windows, SQL Server 2017 unter Linux und Azure SQL-Datenbank.
+ **Echtzeitbewertung**: mithilfe der gespeicherten Prozedur\_RxPredict gespeicherte Prozedur in SQL Server 2016 oder SQL Server 2017 (nur Windows).

> [!NOTE]
> Die PREDICT-Funktion wird in SQL Server 2017 empfohlen.
> Verwenden von sp\_RxPredict erfordert, dass Sie SQLCLR-Integration aktivieren. Beachten Sie die Sicherheitsrisiken, bevor Sie diese Option aktivieren.

Der allgemeine Prozess Vorbereiten des Modells, und klicken Sie dann Generieren von Bewertungen ähnelt:

1. Erstellen Sie ein Modell mit einem unterstützten Algorithmus an.
2. Das Modell mit einem speziellen Binärformat zu serialisieren.
3. Stellen Sie das Modell mit SQL Server zur Verfügung. In der Regel bedeutet dies das serialisierte Modell in einer SQL Server-Tabelle gespeichert werden sollen.
4. Rufen Sie die Funktion oder gespeicherte Prozedur, und übergeben Sie das Modell und die Eingabedaten.

### <a name="requirements"></a>Anforderungen

+ Die PREDICT-Funktion ist in allen Editionen von SQL Server 2017 verfügbar und ist standardmäßig aktiviert. Sie müssen sich nicht zum Installieren von R oder zusätzliche Funktionen aktivieren.

+ Bei Verwendung von sp\_RxPredict, sind einige zusätzliche Schritte erforderlich. Finden Sie unter [aktivieren echtzeitbewertung](#bkmk_enableRtScoring).

+ Zu diesem Zeitpunkt können nur RevoScaleR und MicrosoftML kompatiblen Modelle erstellen. Zusätzliche Modelltypen können in Zukunft verfügbar sein. Die Liste der derzeit unterstützten Algorithmen, finden Sie unter [echtzeitbewertung](../real-time-scoring.md).

### <a name="serialization-and-storage"></a>Serialisierung und Speicherung

Um ein Modell mit der schnellen Bewertung Optionen zu verwenden, speichern Sie das Modell mithilfe von einem speziellen serialisierte Format für Größe optimiert wurde und die Bewertung der Effizienz.

+ Rufen Sie `rxSerializeModel` ein unterstütztes Modell zum Schreiben der **unformatierten** Format.
+ Rufen Sie `rxUnserializeModel` wiederherstellen, kann das Modell für die Verwendung in anderen R-Code oder das Modell anzuzeigen.

Weitere Informationen finden Sie unter [RxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel).

**Mithilfe von SQL**

Von SQL-Code können Sie trainieren das Modell, indem `sp_execute_external_script`, und fügen Sie direkt die trainierten Modelle in einer Tabelle in einer Spalte vom Typ **'varbinary(max)'**.

Ein einfaches Beispiel finden Sie unter [in diesem Tutorial](../tutorials/rtsql-create-a-predictive-model-r.md)

**Mithilfe von R**

Von R-Code gibt es zwei Möglichkeiten, die das Modell in einer Tabelle speichern:

+ Rufen Sie die `rxWriteObject` aus der RevoScaleR-Paket, das Modell direkt an die Datenbank zu schreiben.

  Die `rxWriteObject()` Funktion R-Objekte aus einer ODBC-Datenquelle wie SQL Server, oder Schreiben von Objekten in SQL Server. Die API wird nach einem einfachen Schlüssel-Wert-Speicher modelliert.
  
  Wenn Sie diese Funktion verwenden, achten Sie darauf, dass Sie das Modell zunächst mit die neue Serialisierungsfunktion serialisiert. Legen Sie dann die *Serialisieren* -Argument in `rxWriteObject` auf "false", um zu vermeiden, wiederholen den Schritt für die Serialisierung.

+ Sie können auch das Modell im raw-Format in eine Datei speichern und klicken Sie dann in SQL Server aus der Datei gelesen. Diese Option kann nützlich sein, wenn Sie verschieben oder kopieren die Modelle zwischen Umgebungen.

## <a name="native-scoring-with-predict"></a>Native Bewertung mit VORHERSAGEN

In diesem Beispiel stellen Sie ein Modell erstellen, und rufen dann die echtzeitvorhersage-Funktion von T-SQL.

### <a name="step-1-prepare-and-save-the-model"></a>Schritt 1: Bereiten Sie vor und Speichern des Modells

Führen Sie den folgenden Code zum Erstellen der Beispieldatenbank und die erforderlichen Tabellen.

```SQL
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

Verwenden Sie die folgende Anweisung zum Auffüllen der Datentabelle mit Daten aus der **Iris** Dataset.

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

Erstellen Sie nun eine Tabelle zum Speichern von Modellen.

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

Der folgende Code erstellt ein Modell basierend auf den **Iris** Dataset und speichert es in der Tabelle, die mit dem Namen **Modelle**.

```SQL
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> Verwenden Sie die [RxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) Funktion von RevoScaleR, um das Modell zu speichern. Die R-Standardfunktion `serialize` Funktion kann nicht das erforderliche Format generiert werden.

Sie können eine Anweisung ähnlich der folgenden im Binärformat an das gespeicherte Modell ausführen:

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>Schritt 2: Führen Sie VORHERSAGEN für das Modell

Die folgende einfache PREDICT-Anweisung ruft eine Klassifizierung ab, von der Entscheidung Tree-Modell unter Verwendung der **nativen Bewertung** Funktion. Es sagt die Iris-Arten basierend auf Attribute, die Sie bereitstellen, des kelchblatts sowie Länge und Breite.

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

Wenn Sie eine Fehlermeldung erhalten, Fehler"bei der Ausführung der PREDICT-Funktion. Modell ist beschädigt oder ungültig.", es in der Regel bedeutet, dass die Abfrage ein Modell zurückgegeben wurden. Überprüfen Sie, ob Sie den Modellnamen richtig eingegeben, oder die Modelle Tabelle leer ist.

> [!NOTE]
> Da die Spalten und Werte von zurückgegeben **PREDICT** je nach Modelltyp variieren kann, definieren Sie das Schema der zurückgegebenen Daten mithilfe einer **WITH** Klausel.

## <a name="real-time-scoring-with-sprxpredict"></a>Echtzeitbewertung mit sp_rxPredict

In diesem Abschnitt wird beschrieben, die erforderlichen Schritte zum Einrichten von **in Echtzeit** Vorhersage und ein Beispiel dafür, wie die Funktion von T-SQL aufgerufen.

### <a name ="bkmk_enableRtScoring"></a> Schritt 1. Aktivieren Sie das Real-Time scoring Verfahren

Sie müssen diese Funktion für jede Datenbank aktivieren, die Sie für die Bewertung verwenden möchten. Der Server-Administrator sollten die Befehlszeile-Hilfsprogramm RegisterRExt.exe, ausführen und die in das RevoScaleR-Paket enthalten ist.

> [!NOTE]
> In der Reihenfolge für die echtzeitbewertung funktioniert muss SQL CLR-Funktionalität in der Instanz aktiviert werden; Darüber hinaus muss die Datenbank als vertrauenswürdig gekennzeichnet werden. Wenn Sie das Skript ausführen, werden diese Aktionen für Sie durchgeführt. Jedoch sollten Sie Auswirkungen auf die zusätzliche Sicherheit ein, bevor Sie dies tun!

1. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und navigieren Sie zu dem Ordner, in denen RegisterRExt.exe befindet. Der folgende Pfad kann in einer Standardinstallation verwendet werden:
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. Führen Sie den folgenden Befehl aus, und Ersetzen Sie dabei den Namen Ihrer Instanz und die Zieldatenbank, in dem Sie die erweiterten gespeicherten Prozeduren aktivieren möchten:

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    Geben Sie z. B. zum Hinzufügen der erweiterten gespeicherten Prozedur mit der Datenbank CLRPredict auf der Standardinstanz:

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    Der Instanzname ist optional, wenn die Datenbank für die Standardinstanz ist. Wenn Sie eine benannte Instanz verwenden, müssen Sie den Namen der Instanz angeben.

3. RegisterRExt.exe erstellt die folgenden Objekte:

    + Vertrauenswürdige Assemblys
    + Die gespeicherte Prozedur `sp_rxPredict`
    + Eine neue Datenbankrolle `rxpredict_users`. Der Datenbankadministrator kann diese Rolle verwenden, Benutzern Berechtigungen gewähren, die die Funktionalität des Real-Time scoring verwenden.

4. Fügen Sie alle Benutzer, die auszuführenden `sp_rxPredict` der neuen Rolle.

> [!NOTE]
> 
> Sind in SQL Server 2017 zusätzliche Sicherheitsmaßnahmen, um Probleme mit der CLR-Integration zu verhindern. Diese Measures geben zusätzliche Einschränkungen für die Verwendung dieser gespeicherten Prozedur ebenfalls. 

### <a name="step-2-prepare-and-save-the-model"></a>Schritt 2: Bereiten Sie vor und Speichern des Modells

Das Binärformat sp erforderlichen\_RxPredict ist, entspricht das Datendateiformat dem Format erforderlich, um der PREDICT-Funktion verwenden. Fügen Sie daher in Ihrem R-Code einen Aufruf [RxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel), und geben Sie unbedingt `realtimeScoringOnly = TRUE`, wie in diesem Beispiel:

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>Schritt 3: Rufen Sie sp_rxPredict

Rufen Sie sp\_RxPredict wie würde alle anderen gespeicherten Prozedur. In der aktuellen Version, die gespeicherte Prozedur akzeptiert nur zwei Parameter:  _\@Modell_ für das Modell im binären Format und  _\@InputData_ als für die Daten in die Bewertung mit definiert eine gültige SQL-Abfrage.

Da das binäre Format, die von der PREDICT-Funktion verwendet wird übereinstimmt, können Sie in der Tabelle Modelle und Daten aus dem vorherigen Beispiel.

```SQL
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> Der Aufruf von sp\_RxPredict schlägt fehl, wenn die Eingabedaten für die Bewertung keine Spalten enthalten sind, die die Anforderungen des Modells entsprechen. Derzeit werden nur die folgenden .NET Datentypen unterstützt: double, Float, Short, Ushort, long, Ulong und Zeichenfolge.
> 
> Aus diesem Grund müssen Sie nicht unterstützte Typen in Ihre Daten herausfiltern, bevor Sie ihn für die echtzeitbewertung verwenden.
> 
> Weitere Informationen zu den entsprechenden SQL-Datentypen, finden Sie unter [SQL-CLR-Typzuordnung](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oder [Zuordnen von CLR-Parameterdaten](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data).

## <a name="disable-real-time-scoring"></a>Deaktivieren Sie die echtzeitbewertung

Um in Echtzeit Bewertung Funktionalität deaktivieren, öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und führen Sie den folgenden Befehl: `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="real-time-scoring-in-other-microsoft-product"></a>Echtzeitbewertung in andere Microsoft-Produkt

Wenn Sie anstelle von SQL Server in-Database-Analyse des eigenständigen Servers oder einer Microsoft Machine Learning-Server verwenden, müssen Sie die anderen Optionen außer gespeicherte Prozeduren und T-SQL-Funktionen zum Generieren von Vorhersagen.

Dem eigenständigen Server und dem Machine Learning Server unterstützen das Konzept einer *Webdienst* für die codebereitstellung. Können Sie eine R bündeln oder Python von vortrainierten Modell als Webdienst, zur Laufzeit zum Auswerten von neuen Dateneingaben aufgerufen wird. Weitere Informationen dazu finden Sie in diesen Artikeln:

+ [Was sind Webdienste im Machine Learning Server?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [Was ist die operationalisierung?](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Bereitstellen eines Python-Modells als Webdienst mit Azure ml-Modell-Management-sdk](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [Veröffentlichen Sie ein R-Code-Block oder ein Modell in Echtzeit als neuen Webdienst](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [Mrsdeploy-Paket für R](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
