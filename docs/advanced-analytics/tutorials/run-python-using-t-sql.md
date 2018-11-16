---
title: Führen Sie Python mit T-SQL für SQL Server | Microsoft-Dokumentation
description: Enthält die Grundlagen für die Ausführung von Python-Code, die mithilfe von T-SQL und gespeicherte Prozeduren auf eine Instanz des SQL Server-Datenbank-Engine für die Integration von Python aktiviert ist.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 59897cbe6abc13b9842dc148ef8c2de4413926d0
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702955"
---
# <a name="run-python-using-t-sql"></a>Ausführen von Python mit T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie Python-Code in SQL Server 2017 ausführen können. Es führt Sie durch die Grundlagen des Verschiebens von Daten zwischen SQL Server und Python: Anforderungen, Datenstrukturen, Eingaben und Ausgaben. Außerdem wird erläutert, wie Sie Python-Code wohlgeformt in einer gespeicherten Prozedur umschließen [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) zu erstellen, Trainieren und Verwenden von Machine Learning-Modelle in SQL Server.

## <a name="prerequisites"></a>Erforderliche Komponenten

Zum Ausführen des Beispiels den Codes in diesen Übungen müssen Sie zunächst installieren Sie SQL Server 2017 und Machine Learning-Dienste auf der Serverinstanz zu aktivieren, siehe [installieren Sie SQL Server 2017 Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md). 

Außerdem sollten Sie installieren [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). Alternativ können Sie ein anderes Tool der Datenbank Management oder Abfrage, solange es einen Server und Datenbank herstellen und ein T-SQL-Abfrage oder gespeicherte Prozedur ausgeführt werden kann.

Wenn Ihre Umgebung bereit ist, geben Sie auf dieser Seite können Sie Informationen zum Ausführen von Python-Codes im Kontext einer gespeicherten Prozedur zurück. 

## <a name="verify-python-exists"></a>Stellen Sie sicher, dass Python vorhanden ist.

Die folgenden Schritte sicherstellen, dass Python aktiviert ist, und der SQL Server Launchpad-Dienst ausgeführt wird.

1. Überprüfen Sie, ob die Integration von Python in der Datenbank-Engine-Instanz installiert ist. Sie werden feststellen **python.exe** in einem Ordner namens **PYTHON_SERVICES** unter C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\. Dies ist die Python-ausführbare Datei, die SQL Server verwendet, um Python-Code auszuführen.

2. Überprüfen Sie, ob externe Skripts aktiviert ist. Führen Sie in Management Studio die folgende Anweisung aus:

    ```sql
    sp_configure 'external scripts enabled'
    ```

    Wenn **Run_value** 1 ist, die Machine Learning-Funktion ist installiert und einsatzbereit.

    Eine häufige Ursache von Fehlern ist, die die [SQL Server Launchpad-Dienst](../concepts/extensibility-framework.md#launchpad), verwaltet die Kommunikation zwischen SQL Server und Python, wurde beendet. Sie können den Launchpad-Status anzeigen, indem Sie mithilfe der Windows **Services** Bereich, oder öffnen Sie SQL Server-Konfigurations-Manager. Wenn der Dienst beendet wurde, starten Sie ihn neu.

3. Stellen Sie sicher, dass die Python-Laufzeit arbeiten und Kommunikation mit SQL Server. Zu diesem Zweck öffnen Sie ein neues **Abfrage** Fenster in SQL Server Management Studio, und Verbinden mit der Instanz, in denen Python installiert wurde.

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    Wenn alles funktioniert gut, sollte eine Ergebnisnachricht wie diese angezeigt werden.

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. Wenn Sie eine Fehlermeldung erhalten, gibt es verschiedene Dinge, die Sie tun können, um sicherzustellen, dass der Server und Python kommunizieren können. 

    Sie müssen die Windows-Benutzergruppe hinzufügen `SQLRUserGroup` als Anmeldung auf der Instanz, um sicherzustellen, dass Launchpad Kommunikation zwischen Python und SQL Server bereitstellen kann. (Die gleiche Gruppe wird verwendet, für beide R und Python-code die Ausführung). Weitere Informationen finden Sie unter [implizite Authentifizierung aktiviert](../security/add-sqlrusergroup-to-database.md).
    
    Darüber hinaus müssen Sie zum Aktivieren von Netzwerkprotokollen, die deaktiviert wurden oder öffnen Sie die Firewall, damit SQL Server mit externen Clients kommunizieren können. Weitere Informationen finden Sie unter [Problembehandlungseinrichtung](../common-issues-external-script-execution.md).

### <a name="call-revoscalepy-functions"></a>Die Revoscalepy-Funktionen aufrufen

Zum Überprüfen, ob **Revoscalepy** verfügbar ist, führen Sie ein Skript, das umfasst [Rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) , die eine statistischen Zusammenfassungen Daten erzeugt. Dieses Skript veranschaulicht, wie eine Datei mit Beispieldaten xdf aus integrierten Beispiele im Revoscalepy abgerufen wird. Die RxOptions-Funktion bietet die **SampleDataDir** Parameter, der den Speicherort der Beispieldateien zurückgibt.

Da Rx_summary ein Objekt des Typs zurückgibt `class revoscalepy.functions.RxSummary.RxSummaryResults`, die mehrere Elemente enthält, können Sie nur den Datenrahmen in einem tabellarischen Format extrahieren Pandas.

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

## <a name="basic-python-interaction"></a>Grundlegende Python-Interaktion

Es gibt zwei Möglichkeiten zum Ausführen von Python-Code in SQL Server:

+ Fügen Sie ein Python-Skript als Argument der gespeicherten Systemprozedur, [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Aus einer [Python-Remoteclient](../python/setup-python-client-tools-sql.md), Verbinden mit SQL Server und Code mithilfe von SQL Server als Compute Context ausführen. Dies erfordert [Revoscalepy](../python/what-is-revoscalepy.md).

In der folgenden Übung konzentriert sich auf das erste Interaktionsmodell: wie Python-Code an eine gespeicherte Prozedur übergeben.

1. Führen Sie Beispielcode dahingehend, wie Daten zwischen SQL Server und Python hin und her übergeben werden.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. Vorausgesetzt, dass alles ordnungsgemäß eingerichtet haben, und Python und SQL Server sind miteinander reden, das richtige Ergebnis wird berechnet, und die Python- `print` Funktionsergebnis ist das Ergebnis der **Nachrichten** Windows.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```
    
    Beim Abrufen der **"stdout"** Nachrichten ist nützlich, beim Testen Ihres Codes, häufig müssen Sie die Ergebnisse in tabellarischer Form vorliegen, zurückgeben, damit Sie in einer Anwendung verwenden können, oder in einer Tabelle zu schreiben. 

Denken Sie jetzt an diese Regeln:

+ Alles innerhalb der `@script` Argument muss ein gültiger Python-Code sein. 
+ Der Code muss es sich um alle Python-Regeln in Bezug auf den Einzug, Variablennamen usw. entsprechen. Wenn Sie eine Fehlermeldung erhalten, überprüfen Sie die Leerzeichen und die Groß-/Kleinschreibung aus.
+ Wenn Sie alle Bibliotheken verwenden, die nicht standardmäßig geladen werden, müssen Sie eine Import-Anweisung am Anfang des Skripts verwenden, um sie zu laden. SQL Server fügt verschiedene produktspezifische-Bibliotheken hinzu. Weitere Informationen finden Sie unter [Python-Bibliotheken](../python/python-libraries-and-data-types.md).
+ Wenn die Bibliothek noch nicht installiert ist, beenden, und installieren Sie das Python-Paket außerhalb von SQL Server, wie hier beschrieben: [Installieren neuer Python-Pakete unter SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>Eingaben und Ausgaben

In der Standardeinstellung [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) akzeptiert ein einzelnes Eingabe-Dataset, das Sie in der Regel in Form von einer gültigen SQL-Abfrage zu geben. 

Andere Arten von Eingaben, die als SQL-Variablen übergeben werden können: beispielsweise, Sie können übergeben ein trainiertes Modells als Variable mithilfe einer Serialisierungsfunktion wie [Pickle](https://docs.python.org/3.0/library/pickle.html) oder [Rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) , schreiben das Modell ein binäres Format.

Die gespeicherte Prozedur gibt ein einzelnen Python [Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) Datenrahmen als Ausgabe, aber Sie können auch skalare und Modelle als Variablen ausgeben. Sie können z. B. die Ausgabe eines trainierten Modells als binäre Variable und übergeben, um eine T-SQL INSERT-Anweisung, um das Modell in einer Tabelle zu schreiben. Sie können auch Diagramme (im binären Format) oder skalare generieren (einzelne Werte, z. B. Datum und Uhrzeit, die verstrichene Zeit zum Trainieren des Modells und so weiter).

Jetzt sehen wir uns nur um die Standardeinstellung Eingabe- und Variablen von Sp_execute_external_script: `InputDataSet` und `OutputDataSet`. 

1. Führen Sie den folgenden Code zum anstellen einiger Berechnungen und die Ergebnisse ausgeben.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    OutputDataSet = c
    '
    WITH RESULT SETS ((ResultValue float))
    ```

2. Sie sollten einen Fehler erhalten, da der Python-Code einen Skalarwert, der nicht in einen dataframe generiert.

    **Ergebnisse**

    ```text
    line 43, in transform
        raise TypeError('OutputDataSet should be of type pandas.DataFrame')
    ```

3. Jetzt sehen, was geschieht, wenn ein tabellarisches Dataset zu Python, übergeben Sie mit der Standard-Eingabevariablen `InputDataSet`. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    Die gespeicherte Prozedur gibt einen Datenrahmen (Data.Frame) automatisch, ohne dass Sie zusätzliche Python-Code nichts zurück.

    **Ergebnisse**

    | kein Spaltenname|
    |------|
    | 1|

    Standardmäßig verfügt das einzelne tabellarische Eingabe-Dataset den Namen, `InputDataSet`. Jedoch können Sie diesen Namen ändern, indem Sie eine Zeile wie folgt hinzufügen: `@input_data_1_name = N'myResultName'`.

    Python ein, die Spaltennamen werden nie in der Ausgabe beibehalten. Obwohl die Eingabeabfrage der Spaltenname angegeben `Col1`, diesen Namen wird nicht zurückgegeben, es sind auch Spaltenüberschriften, die von Ihrer Python-Skript verwendet. Verwenden, um eine Spalte und den angegebenen Datentyp anzugeben, wenn Sie die Daten in SQL Server zurückgeben das T-SQL `WITH RESULT SETS` Klausel.

4. Dieses Beispiel enthält die neue Namen für die Eingabe- und Variablen.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    MyOutput = MyInput
    ',
    @input_data_1_name = N'MyInput',
    @input_data_1 = N'SELECT 1 as Col1',
    @output_data_1_name = N'MyOutput'
    WITH RESULT SETS ((ResultValue int))
    ```

    Die WITH RESULT SET-Klausel definiert das Schema für die Ausgabe an, da Python Spaltennamen nie mit dem Datenrahmen (Data.Frame) zurückgegeben werden.

    **Ergebnisse**

    | ResultValue|
    |------|
    | 1|

5. Jetzt sehen wir uns einen typischen Python-Fehler. Ändern Sie die Zeile im vorherigen Beispiel von `@input_data_1_name = N'MyInput'` zu `@input_data_1_name = N'myinput'`.

    Python-Fehler werden als Nachrichten, durch den Satelliten-Dienst von SQL Server verwendeten an Sie übergeben. Nachrichten können lang sein und SQL Server-Fehler oder Launchpad-Fehler zusätzlich zu den Python-Anwendungsfehlern, gehören also etwas Geduld in Schlüsseln, durch den Text. Die schlüsselmeldung ist in dieser Zeile:

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    Denken Sie daran, dass Python, wie R die Groß-und Kleinschreibung beachtet. Wenn Sie eine beliebige Art von Fehler erhalten, achten Sie daher, überprüfen Sie Ihre Namen von Variablen, und suchen Sie nach Problemen mit Abstand und Einzug von Datentypen.

## <a name="python-data-structures"></a>Python-Datenstrukturen

SQL Server ist abhängig von der Python **Pandas** -Paket, das ist großartig für die Arbeit mit Tabellendaten. Allerdings haben Sie bereits gesehen, dass Sie keinen Skalarwert aus Python mit SQL Server zu übergeben und erwarten, es einfach dass "sauber arbeiten". In diesem Abschnitt sehen wir uns einige grundlegende Datentypdefinitionen, um weitere Probleme zu vorzubereiten, denen Sie möglicherweise über beim Übergeben von Tabellendaten zwischen Python und SQL Server.

+ Ein Datenrahmen ist eine Tabelle mit _mehrere_ Spalten.
+ Eine einzelne Spalte mit den DataFrame ist eine Liste Objekt mit dem Namen einer Serie.
+ Ein einzelner Wert ist eine Zelle eines und nach Index aufgerufen werden muss.

Wie würden Sie das einzelne Ergebnis einer Berechnung als Datenrahmen, verfügbar machen, wenn für einen Datenrahmen (Data.Frame) eine tabellarischen Struktur erforderlich ist? Eine Antwort ist, um die einzelnen skalaren Wert als eine Reihe, darzustellen, die einfach zu einem Datenrahmen konvertiert wird. 

1. In diesem Beispiel werden einige einfache mathematische und konvertiert einen Skalar in eine Reihe. Eine Reihe erfordert einen Index, die Sie wie folgt manuell oder programmgesteuert zuweisen können.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    s = pandas.Series(c, index =["simple math example 1"])
    print(s)
    '
    ```

2. Da der Reihe wurde nicht in eine data.frame konvertiert wurde, die Werte werden im Meldungsfenster zurückgegeben, aber Sie sehen, dass die Ergebnisse in einem Tabellenformat mehr sind.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Um die Länge der Reihe zu erhöhen, können Sie neue Werte hinzufügen, mit einem Array. 

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    '
    ```

    Wenn Sie einen Index nicht angeben, wird ein Index generiert, die Werte, die mit 0 beginnt und endet mit der Länge des Arrays enthält.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Wenn Sie die Anzahl der erhöhen **Index** Werte jedoch nicht neu hinzufügen **Daten** Werte, die Datenwerte werden wiederholt, um die Reihen auszufüllen.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    '
    ```

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    simple math example 2    0.5
    dtype: float64
    ```

### <a name="convert-series-to-data-frame"></a>Reihe in Datenrahmen zu konvertieren.

Konvertiert unsere skalare mathematischen Ergebnisse müssen zu einer tabellarischen Struktur, müssen wir sie in ein Format zu konvertieren, die SQL Server verarbeiten kann. 

1. Um eine Reihe in eine data.frame zu konvertieren, rufen Sie die Pandas [DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) Methode.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s)
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

2. Beachten Sie, dass die Indexwerte Ausgabe nicht, selbst wenn Sie den Index verwenden, um bestimmte Werte aus den Datenrahmen (Data.Frame) abzurufen.

    **Ergebnisse**

    |ResultValue|
    |------|
    |0.5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>Ausgabewerte in Datenrahmen (Data.Frame) mit einem index

Sehen wir uns an, wie die Konvertierung in einen Datenrahmen (Data.Frame) mit unseren zwei Reihen mit den Ergebnissen der einfachen mathematischen Vorgängen funktioniert. Die erste hat den Index von sequenziellen Werten, die von Python generiert. Der zweite verwendet einen beliebigen Index von Zeichenfolgenwerten.

1. In diesem Beispiel ruft einen Wert ab, aus der Reihe, die einen ganzzahligen Index verwendet.

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    df = pd.DataFrame(s, index=[1])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    Denken Sie daran, dass der Index automatisch generierter bei 0 beginnt. Versuchen Sie es mit einem Wert außerhalb des Gültigkeitsbereichs Index, und sehen, was passiert.

2. Jetzt rufen wir einen einzelnen Wert aus anderen Datenrahmen, die einen String-Index verfügt. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    **Ergebnisse**

    |ResultValue|
    |------|
    |0.5|

    Wenn Sie versuchen, einen numerischen Index verwenden, um einen Wert aus dieser Reihe zu erhalten, erhalten Sie eine Fehlermeldung an.

In dieser Übung soll Ihnen einen Hinweis zum Arbeiten mit verschiedenen Python-Datenstrukturen, und stellen Sie sicher, dass Sie das richtige Ergebnis als Datenrahmen erhalten. Sie können diese Ausgabe eines einzelnen Werts als ein Datenrahmen mehr Probleme bringt als lohnt ist geschlossen haben! Glücklicherweise können Sie problemlos alle Arten von Werten in und aus der gespeicherten Prozedur als Variablen übergeben. Finden Sie in der nächsten Lektion.

## <a name="tips"></a>Tipps

+ Zwischen Programmiersprachen Python ist eine der flexibelsten im Hinblick auf die einfachen Anführungszeichen und doppelte Anführungszeichen eingeschlossen werden. Diese sind ziemlich austauschbar. 

    T-SQL verwendet jedoch einfache Anführungszeichen für die nur bestimmte Dinge, und die `@script` Argument verwendet einfache Anführungszeichen, um den Python-Code als Unicode-Zeichenfolge einzuschließen. Aus diesem Grund müssen Sie zum Überprüfen von Python-Code, und ändern Sie einige einfache Anführungszeichen in doppelte Anführungszeichen.

+ Die gespeicherte Prozedur wurde nicht gefunden `sp_execute_external_script`? Dies bedeutet, dass Sie wahrscheinlich noch nicht mit dem Konfigurieren fertig die Instanz, um die Ausführung des externen Skripts zu unterstützen. Nach dem Ausführen von SQL Server 2017-Setup aus, und Auswählen von Python als die Machine learning-Sprache, Sie müssen auch explizit aktivieren die Funktion mit `sp_configure`, und klicken Sie dann die Instanz neu starten. 

    Weitere Informationen finden Sie unter [installieren Sie SQL Server 2017 Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md).

## <a name="next-steps"></a>Nächste Schritte

[Richten Sie das Iris-Demo-dataset](demo-data-iris-in-sql.md)