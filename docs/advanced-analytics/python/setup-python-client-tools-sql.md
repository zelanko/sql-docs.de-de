---
title: Einrichten eines Python-Clients für die Verwendung mit SQL Server-Machine Learning | Microsoft-Dokumentation
description: Richten Sie eine lokale Python-Umgebung für Remoteverbindungen zur SQL Server-Machine-Learning-Services mit Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/25/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b328d6c44dd8f75e3d74a3abe74f3324f31e1409
ms.sourcegitcommit: 12779bddd056a203d466d83c4a510a97348fe9d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216624"
---
# <a name="set-up-a-python-client-for-use-with-sql-server-machine-learning"></a>Einrichten eines Python-Clients für die Verwendung mit SQL Server-Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Integration von Python finden Sie in SQL Server 2017 oder später gestartet werden, während Sie die Python-Option in einschließen einer [Machine Learning Services (Datenbankintern) Installation](../install/sql-machine-learning-services-windows-install.md). 

Erfahren Sie in diesem Artikel, wie eine Python-Entwicklung Clientarbeitsstation so konfigurieren, dass Sie mit einem SQL-Remoteserver für Machine Learning und die Integration von Python eine Verbindung herstellen können. In dieser Übung verwendet Jupyter-Notebooks zum Ausführen von Python-Code. Nach Abschluss der Schritte in diesem Artikel müssen Sie die gleichen Python-Bibliotheken wie die auf SQL Server. Außerdem lernen Sie, wie Sie Berechnungen in einer lokalen Python-Sitzung an eine Remotesitzung von Python auf SQL Server zu senden.

> [!Tip]
> Eine Videodemo Übungen in diesem Artikel finden Sie unter [Ausführen von R und Python Remote in SQL Server über Jupyter-Notebooks](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/).

> [!Note]
> Eine Alternative zur Installation nur der Clientbibliotheken verwendet einen eigenständigen Server. Mithilfe eines eigenständigen Computers-Server als rich Client ist eine Option, die auf weitere Arbeit für End-to-End-Szenario einige Kunden bevorzugen. Wenn Sie haben eine [eigenständiger Server](../install/sql-machine-learning-standalone-windows-install.md) wie in SQL Server-Setup bereitgestellt, Sie haben einen Python-Server, der von einer Instanz von SQL Server-Datenbank-Engine vollständig entkoppelt wird. Ein Server Standalon umfasst die Open-Source-base-Verteilung von Anaconda sowie die Microsoft-spezifische Bibliotheken. Sie finden die Python-ausführbare Datei an diesem Speicherort: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Öffnen Sie als Validierung der die rich-Client-Installation, eine [Jupyter-Notebook](#python-tools) zum Ausführen von Befehlen, die mit der Python.exe auf dem Server.

## <a name="1---install-python-packages"></a>1: Installieren von Python-Pakete

Lokale Arbeitsstationen müssen die gleichen Versionen der Python-Paket wie die auf SQL Server, einschließlich der Basis-Verteilung und der Microsoft-spezifische Pakete [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [Microsftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). Die [Azure ml-modellverwaltung](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) Paket ist ebenfalls installiert, aber dies gilt für die operationalisierung Aufgaben im Zusammenhang mit einem Machine Learning Server-Kontext von eigenständigen (nicht-Instanz). Für in-Database-Analyse in einer SQL Server-Instanz ist operationalisierung mithilfe von gespeicherten Prozeduren ein.

1. Laden das Installationsskript, um Anaconda 4.2.0 mit Python 3.5.2 zu installieren, und die drei oben aufgeführten Microsoft-Pakete.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) SQL Server 2017 ist nicht gebunden (meistens). Wählen Sie dieses Skript aus, wenn Sie nicht sicher sind.

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) ist der SQL Server-Remoteinstanz [an Machine Learning Server 9.3 gebunden](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

2. Öffnen Sie ein PowerShell-Fenster mit Administratorberechtigungen (mit der rechten Maustaste **als Administrator ausführen**).

3. Wechseln Sie zu dem Ordner, in dem Sie das Installationsprogramm heruntergeladen haben, und führen Sie das Skript. Hinzufügen der `-InstallFolder` Befehlszeilenargument an einen Ordner als Speicherort für die Bibliotheken. Zum Beispiel: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Wenn Sie den Installationsordner weglassen, ist die Standardeinstellung c:\Programme\Microsoft Files\Microsoft\PyForMLS an.

Die Installation dauert einige Zeit in Anspruch. Sie können den Fortschritt im PowerShell-Fenster überwachen. Wenn Setup abgeschlossen ist, müssen Sie einen vollständigen Satz von Paketen. 

> [!Tip] 
> Wir empfehlen die [Python für Windows – häufig gestellte Fragen](https://docs.python.org/3/faq/windows.html) allgemeine Purppose Informationen zum Ausführen von Python-Programmen für Windows.

## <a name="2---locate-executables"></a>2: Suchen von ausführbaren Dateien

Navigieren Sie in den Installationsordner, um den Speicherort der Python.exe, Skripts und andere Pakete überprüfen, immer noch in PowerShell. 

1. Geben Sie `cd \` in das Stammlaufwerk, und geben dann den Pfad für die angegebene `-InstallFolder` im vorherigen Schritt. Wenn Sie während der Installation dieser Parameter nicht angegeben, wird der Standardwert ist `cd C:\Program Files\Microsoft\PyForMLS`.

2. Geben Sie `dir *.exe` die ausführbaren Dateien auflisten. Daraufhin sollte **python.exe**, **pythonw.exe**, und **deinstallieren anaconda.exe**.

  ![Liste der ausführbaren Python-Dateien](media/powershell-python-exe.png)
   
Auf Systemen, die mehrere Versionen von Python, denken Sie daran, diese bestimmte Python.exe zu verwenden, wenn Sie laden möchten **Revoscalepy** und andere Microsoft-Pakete.

> [!Note] 
> Das Installationsskript ändert nicht die PATH-Umgebungsvariablen auf dem Computer, was bedeutet, dass die neuen Python-Interpreter und die Module, die Sie gerade installiert nicht automatisch zur Verfügung, mit anderen Tools sind möglicherweise. Hilfe zum Verknüpfen der Python-Interpreter und Bibliotheken, Tools, finden Sie unter [Installieren einer IDE](#install-ide).

<a name="python-tool"></a>

## <a name="3---open-jupyter-notebooks"></a>3: Öffnen von Jupyter-Notebooks

Anaconda umfasst die Jupyter-Notebooks. Klicken Sie im nächsten Schritt erstellen Sie ein Notebook, und führen Sie einige Python-Code, enthält die Bibliotheken, die Sie soeben installiert haben.

1. Navigieren Sie in der Powershell-Eingabeaufforderung zum Ordner "Scripts" zum Öffnen von Jupyter-Notebooks:

   ```powershell
   .\Scripts\jupyter-notebook
   ```

  Sollte ein Notebook in Ihrem Standardbrowser an öffnen `http://localhost:8889/tree`.

2. Klicken Sie auf **neu** , und klicken Sie dann auf **Python 3**.

  ![Jupyter-Notebook mit neuen Python-3-Auswahl](media/jupyter-notebook-new-p3.png)

3. Geben Sie `import revoscalepy` , und führen Sie den Befehl zum Laden eines Microsoft-spezifische Bibliotheken.

4. Geben Sie eine komplexere Reihe von Anweisungen aus. In diesem Beispiel wird mithilfe von Statistiken über Zusammenfassungen von [Rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) über ein lokales DataSet. Andere Funktionen erhalten den Speicherort der Beispieldaten an, und erstellen ein Datenquellenobjekt für eine lokale xdf-Datei.

  ```Python
  import os
  from revoscalepy import rx_summary
  from revoscalepy import RxXdfData
  from revoscalepy import RxOptions
  sample_data_path = RxOptions.get_option("sampleDataDir")
  print(sample_data_path)
  ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
  summary = rx_summary("ArrDelay+DayOfWeek", ds)
  print(summary)
  ```

Der folgende Screenshot zeigt die Eingabe und einen Teil der Ausgabe, die aus Gründen der Übersichtlichkeit gekürzt.

  ![Jupyter-Notebook mit Revoscalepy-Eingaben und Ausgaben](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4: Abrufen von SQL-Berechtigungen

Herstellen der Verbindung mit einer Instanz von SQL Server zum Ausführen von Skripts und Daten hochzuladen, müssen Sie eine gültige Anmeldung auf dem Datenbankserver verfügen. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird empfohlen, dass Sie die integrierte Windows-Authentifizierung verwenden, mit der SQL-Anmeldung ist jedoch einfacher für einige Szenarien, insbesondere dann, wenn Ihr Skript Verbindungszeichenfolgen zu externen Daten enthält.

Mindestens muss das Konto zum Ausführen von Code verwendet die Berechtigung zum Lesen aus den Datenbanken, mit dem Sie arbeiten, sowie die speziellen Berechtigungen ausgeführt, ANY EXTERNAL SCRIPT haben. Die meisten Entwickler auch benötigen Berechtigungen zum Erstellen von gespeicherter Prozeduren und zum Schreiben von Daten in Tabellen mit Daten oder Daten bewertet. 

Bitten Sie den Datenbankadministrator, konfigurieren Sie die folgenden Berechtigungen für das Konto in der Datenbank, in dem Sie Python verwenden:

+ **EXECUTE ANY EXTERNAL SCRIPT** zum Ausführen von Python auf dem Server.
+ **Db_datareader** Privilegien zum Ausführen von Abfragen zum Trainieren des Modells verwendet.
+ **Db_datawriter** Trainings- oder ausgewerteten Daten schreiben.
+ **Db_owner** zum Erstellen von Objekten, z. B. gespeicherte Prozeduren, Tabellen, Funktionen. 
  Sie müssen auch **Db_owner** Beispiel und Test-Datenbanken erstellen. 

Wenn Ihr Code Pakete, die nicht standardmäßig mit SQL Server installiert sind erfordert, ordnen Sie den Datenbankadministrator, um die mit der Instanz installierten Pakete zu erhalten. SQL Server ist eine sichere Umgebung, und es gibt Einschränkungen für die Pakete installiert werden können. Ad-hoc-Installation von Paketen als Teil des Codes wird nicht empfohlen, auch wenn Sie über Zugriffsrechte verfügen. Darüber hinaus immer sorgfältig Auswirkungen auf die Sicherheit vor der Installation neuer Pakete in der Serverbibliothek.

## <a name="5---test-remote-connection"></a>5: Testen der Remoteverbindung

Bevor Sie versuchen, diesen nächsten Schritt, stellen Sie sicher, dass Berechtigungen für SQL Server-Instanz und eine Verbindungszeichenfolge für die [Iris-Beispieldatenbank](../tutorials/demo-data-iris-in-sql.md). Wenn die Datenbank ist nicht vorhanden, und Sie über ausreichende Berechtigungen verfügen, können Sie [erstellen Sie eine Datenbank mithilfe der inlineanweisungen](#create-iris-remotely).

Ersetzen Sie die Verbindungszeichenfolge mit gültigen Werten. Der Beispielcode verwendet `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` , aber Ihr Code sollte die Remoteserver angeben, in der möglicherweise von einen Instanznamen an, und eine Option der Anmeldeinformationen, die Datenbank-Benutzeranmeldung zugeordnet ist.

### <a name="define-a-function"></a>Definieren Sie eine Funktion

Der folgende Code definiert eine Funktion, die in einem späteren Schritt an SQL Server gesendet wird. Bei der Ausführung verwendet diese Daten und -Bibliotheken (Revoscalepy, Pandas, Matplotlib) auf dem Remoteserver Punktdiagrammen, der das Iris-DataSet zu erstellen. Gibt den Bytestream, der die PNG zurück zu Jupyter-Notebooks im Browser gerendert.

```python
def send_this_func_to_sql():
    from revoscalepy import RxSqlServerData, rx_import
    from pandas.tools.plotting import scatter_matrix
    import matplotlib.pyplot as plt
    import io
    
    # remember the scope of the variables in this func are within our SQL Server Python Runtime
    connection_string = "Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"
    
    # specify a query and load into pandas dataframe df
    sql_query = RxSqlServerData(connection_string=connection_string, sql_query = "select * from iris_data")
    df = rx_import(sql_query)
    
    scatter_matrix(df)
    
    # return bytestream of image created by scatter_matrix
    buf = io.BytesIO()
    plt.savefig(buf, format="png")
    buf.seek(0)
    
    return buf.getvalue()
```

### <a name="send-the-function-to-sql-server"></a>Senden Sie die Funktion an SQL Server

In diesem Beispiel den entfernten computekontext erstellen, und klicken Sie dann die Ausführung der Funktion von SQL Server mit senden [Rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). Die **Rx_exec** Funktion ist nützlich, da es sich um einen computekontext als Argument akzeptiert. Alle Funktionen, die Sie Remote ausführen möchten, benötigen ein Compute Context-Argument. Einige Funktionen, z. B. [Rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) unterstützt Sie dieses Argument direkt. Für Vorgänge, die Sie nicht, können Sie **Rx_exec** Ihren Code in einem remotecomputekontext zu übermitteln.

In diesem Beispiel musste keine unformatierten Daten aus SQL Server auf den Jupyter-Notebook übertragen werden. Alle Berechnungen innerhalb der Iris-Datenbank auftreten, und nur die Image-Datei an den Client zurückgegeben wird.

```python
from IPython import display
import matplotlib.pyplot as plt 
from revoscalepy import RxInSqlServer, rx_exec

# create a remote compute context with connection to SQL Server
sql_compute_context = RxInSqlServer(connection_string=connection_string.format(new_db_name))

# use rx_exec to send the function execution to SQL Server
image = rx_exec(send_this_func_to_sql, compute_context=sql_compute_context)[0]

# only an image was returned to my jupyter client. All data remained secure and was manipulated in my db.
display.Image(data=image)
```

Der folgende Screenshot zeigt die Eingabe und Punktdiagrammen Plot-Ausgabe.

  ![Jupyter-Notebook mit XY-Diagramm-Ausgabe](media/jupyter-notebook-scatterplot.png)

## <a name="6---link-ide-to-pythonexe"></a>6 - Link python.exe-IDE

Wenn Sie Skripts über die Befehlszeile einfach Debuggen, können Sie mit der standardmäßigen Python-Tools abrufen, indem. Wenn Sie neue Lösungen entwickeln, können Sie jedoch eine Python-IDE mit vollem Funktionsumfang erforderlich. Beliebte Optionen sind:

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) mit Python
+ [KI-Tools für Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
+ Beliebten Drittanbieter-Tools wie Eclipse, PyCharm und Spyder

Visual Studio wird empfohlen, da es sich um Datenbankprojekte als auch für Machine Learning-Projekten unterstützt. Hilfe zum Konfigurieren einer Python-Umgebung finden Sie [Verwalten von Python-Umgebungen in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

Da Entwickler häufig mit mehreren Versionen von Python arbeiten, wird Python von Setup nicht zu Ihrem Pfad hinzufügen. Um die Python-ausführbare-Datei und die Bibliotheken, die von Setup installiert zu verwenden, verknüpfen Sie Ihre IDE **Python.exe** unter dem Pfad, die auch ermöglicht **Revoscalepy** und **Microsoftml**. 

Für ein Python-Projekt in Visual Studio würden Ihrer benutzerdefinierten Umgebung die folgenden Werte, die bei einer Standardinstallation angeben.

| Konfigurationseinstellung | Wert |
|-----------------------|-------|
| **Präfixpfad** | C:\Programme\Microsoft Files\Microsoft\PyForMLS |
| **Cesta k interpretu** | C:\Programme\Microsoft Files\Microsoft\PyForMLS\python.exe |
| **Fenstermodus-interpreter** | C:\Programme\Microsoft Files\Microsoft\PyForMLS\pythonw.exe |

<a name="create-iris-remotely"></a>

## <a name="optional-create-the-iris-database-remotely"></a>Optional: Erstellen der Datenbank Iris per Remotezugriff

Wenn Sie Berechtigungen zum Erstellen einer Datenbank auf dem Remoteserver verfügen, können Sie den folgenden Code zum Erstellen der für die Beispiele in diesem Artikel verwendeten Iris-Demo-Datenbank ausführen.

### <a name="1---create-the-irissql-database"></a>1: Erstellen der Datenbank irissql

```Python
import pyodbc

# creating a new db to load Iris sample in
new_db_name = "irissql"
connection_string = "Driver=SQL Server;Server=localhost;Database={0};Trusted_Connection=Yes;" 
                        # you can also swap Trusted_Connection for UID={your username};PWD={your password}
cnxn = pyodbc.connect(connection_string.format("master"), autocommit=True)
cnxn.cursor().execute("IF EXISTS(SELECT * FROM sys.databases WHERE [name] = '{0}') DROP DATABASE {0}".format(new_db_name))
cnxn.cursor().execute("CREATE DATABASE " + new_db_name)
cnxn.close()

print("Database created")
```

### <a name="2---import-iris-sample-from-sklearn"></a>2 – Beispiel "Iris" aus der von "sklearn" Importieren

```Python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3 – verwenden Sie Revoscalepy-APIs, um eine Tabelle erstellen und Laden Sie die Iris-Daten

```Python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

<a name="install-ide"></a>

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie über Tools und eine funktionierende Verbindung mit SQL Server verfügen, durchlaufen Sie ein Tutorial, um eine genauere Betrachtung Revoscalepy-Funktionen und zwischen computekontexten wechseln zu erhalten.

> [!div class="nextstepaction"]
> [Erstellen eines Modells mithilfe von Revoscalepy und einem remotecomputekontext](../tutorials/use-python-revoscalepy-to-create-model.md)