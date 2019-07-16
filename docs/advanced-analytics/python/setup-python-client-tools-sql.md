---
title: 'Richten Sie eine Data Science-Client für SQL Server-Machine Learning Python-Entwicklung:'
description: Richten Sie eine lokale Python-Umgebung (Jupyter-Notebook oder PyCharm) für Remoteverbindungen mit SQL Server-Machine-Learning-Services mit Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6c302f7cc9830b15ed058c160618ea0e40705444
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962733"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Richten Sie eine Data Science-Client für die Python-Entwicklung für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Integration von Python finden Sie in SQL Server 2017 oder später gestartet werden, während Sie die Python-Option in einschließen einer [Machine Learning Services (Datenbankintern) Installation](../install/sql-machine-learning-services-windows-install.md). 

Installieren Sie zum Entwickeln und Bereitstellen von Python-Lösungen für SQL Server, Microsoft [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und andere Python-Bibliotheken Ihre Entwicklungsarbeitsstation. Die Revoscalepy-Bibliothek, die auch auf der Remoteinstanz von SQL Server, koordiniert Compute-Anforderungen zwischen den beiden Systemen. 

Erfahren Sie in diesem Artikel, wie eine Python-Entwicklungsarbeitsstation so konfigurieren, dass Sie mit einem SQL-Remoteserver für Machine Learning und Python-Integration aktiviert interagieren können. Nach Abschluss der Schritte in diesem Artikel müssen Sie die gleichen Python-Bibliotheken wie die auf SQL Server. Außerdem lernen Sie, wie Sie Berechnungen in einer lokalen Python-Sitzung an eine Remotesitzung von Python auf SQL Server zu senden.

![Client / Server-Komponenten](media/sqlmls-python-client-revo.png "lokalen und Remotesitzungen von Python und Bibliotheken")

Um die Installation zu überprüfen, können Sie integrierte Jupyter Notebooks verwenden, wie in diesem Artikel beschrieben oder [verknüpfen Sie die Bibliotheken](#install-ide) PyCharm oder alle eine andere IDE, die Sie normalerweise verwenden.

> [!Tip]
> Eine Videodemo diesen Übungen Bezug finden Sie unter [führen Sie R- und Python Remote in SQL Server über Jupyter-Notebooks](https://youtu.be/D5erljpJDjE).

> [!Note]
> Eine Alternative zur Installation des Client-Bibliothek ist die Verwendung einer [eigenständiger Server](../install/sql-machine-learning-standalone-windows-install.md) als rich-Clients, die für die Arbeit für umfangreichere Szenario einige Kunden bevorzugen. Ein eigenständiger Server wird von SQL Server vollständig entkoppelt, aber da sie die gleichen Python-Bibliotheken verfügt, können Sie sie als Client für SQL Server in-Database-Analyse. Außerdem können Sie sie für nicht-SQL-bezogenen arbeiten, einschließlich der Fähigkeit zum Importieren und Modellieren von Daten von anderen Data-Plattformen. Wenn Sie einen eigenständigen Server installieren, finden Sie die Python-ausführbare Datei an diesem Speicherort: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. So überprüfen Sie Ihre Installation, [öffnen Sie ein Jupyter-Notebook](#python-tools) zum Ausführen von Befehlen, die mit der Python.exe an diesem Speicherort.

## <a name="commonly-used-tools"></a>Häufig verwendete tools

Sind Sie ein Python-Entwickler, die noch nicht mit SQL oder SQL-Entwickler noch nicht mit Python und in-Database-Analyse, benötigen Sie sowohl eine Python-Entwicklungstools und einen T-SQL-Abfrage-Editor wie z. B. [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) So führen Sie alle aus die Funktionen der datenbankinternen Analysen.

Python-Entwicklung können Sie für Jupyter-Notebooks, der gebündelten in die Anaconda-Distribution, die von SQL Server installiert ist. In diesem Artikel wird erläutert, wie Jupyter-Notebooks gestartet, damit Sie Python-Code lokal und Remote auf SQL Server ausführen können.

SSMS ist ein separater Download, der nützlich zum Erstellen und Ausführen von gespeicherten Prozeduren in SQL Server, einschließlich derjenigen, die Python-Code enthält. Beinahe jeder Python-Code, den Sie in Jupyter-Notebooks zu schreiben, kann in einer gespeicherten Prozedur eingebettet werden. Sie können schrittweise durchlaufen, andere schnellstartanleitungen Informationen [SSMS und eingebetteten Python](../tutorials/quickstart-python-verify.md).

## <a name="1---install-python-packages"></a>1: Installieren von Python-Pakete

Lokale Arbeitsstationen müssen die gleichen Versionen der Python-Paket wie die auf SQL Server, einschließlich der grundlegenden Anaconda 4.2.0 mit Python 3.5.2-Distribution und Microsoft-spezifische Pakete.

Skript für eine Installation hinzugefügt der Python-Client drei Microsoft-spezifische Bibliotheken. Installiert das Skript [Revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), die zum Definieren von Datenquellenobjekten und den computekontext verwendet. Installiert [Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) Bereitstellen von Machine Learning-Algorithmen. Die [Azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) Paket ist ebenfalls installiert, aber es gilt für die operationalisierung Aufgaben im Zusammenhang mit einem Machine Learning Server-Kontext von eigenständigen (nicht-Instanz) und kann nur von begrenztem Nutzen für in-Database-Analyse.

1. Laden Sie ein Installationsskript herunter.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) Version 9.2.1 der Microsoft-Python-Pakete installiert. Diese Version entspricht, mit einer Standardinstanz von SQL Server 2017. 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) Version 9.3 der Microsoft-Python-Pakete installiert. Diese Version ist die bessere Wahl, wenn die Remoteinstanz von SQL Server 2017 ist [an Machine Learning Server 9.3 gebunden](../install/upgrade-r-and-python.md).

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

Immer noch in PowerShell Listen Sie den Inhalt der Installationsordner zu bestätigen, dass Python.exe, Skripts und andere Pakete installiert sind auf. 

1. Geben Sie `cd \` in das Stammlaufwerk, und geben dann den Pfad für die angegebene `-InstallFolder` im vorherigen Schritt. Wenn Sie während der Installation dieser Parameter nicht angegeben, wird der Standardwert ist `cd C:\Program Files\Microsoft\PyForMLS`.

2. Geben Sie `dir *.exe` die ausführbaren Dateien auflisten. Daraufhin sollte **python.exe**, **pythonw.exe**, und **deinstallieren anaconda.exe**.

  ![Liste der ausführbaren Python-Dateien](media/powershell-python-exe.png)
   
Auf Systemen, die mehrere Versionen von Python, denken Sie daran, diese bestimmte Python.exe zu verwenden, wenn Sie laden möchten **Revoscalepy** und andere Microsoft-Pakete.

> [!Note] 
> Das Installationsskript ändert nicht die PATH-Umgebungsvariablen auf dem Computer, was bedeutet, dass die neuen Python-Interpreter und die Module, die Sie gerade installiert nicht automatisch zur Verfügung, mit anderen Tools sind möglicherweise. Hilfe zum Verknüpfen der Python-Interpreter und Bibliotheken, Tools, finden Sie unter [Installieren einer IDE](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3: Öffnen von Jupyter-Notebooks

Anaconda umfasst die Jupyter-Notebooks. Klicken Sie im nächsten Schritt erstellen Sie ein Notebook, und führen Sie einige Python-Code, enthält die Bibliotheken, die Sie soeben installiert haben.

1. Öffnen Sie in der Powershell-Eingabeaufforderung immer noch im Verzeichnis c:\Programme\Microsoft Files\Microsoft\PyForMLS Jupyter-Notebooks über den skriptsordner aus:

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  Sollte ein Notebook in Ihrem Standardbrowser an öffnen `https://localhost:8889/tree`.

  Ist eine weitere Möglichkeit zum Starten, doppelklicken Sie auf **Jupyter-notebook.exe**. 

2. Klicken Sie auf **neu** , und klicken Sie dann auf **Python 3**.

  ![Jupyter-Notebook mit neuen Python-3-Auswahl](media/jupyter-notebook-new-p3.png)

3. Geben Sie `import revoscalepy` , und führen Sie den Befehl zum Laden eines Microsoft-spezifische Bibliotheken.

4. Geben Sie ein, und führen Sie `print(revoscalepy.__version__)` die Versionsinformationen zurückgegeben. 9\.2.1 oder 9.3.0 sollte angezeigt werden. Verwenden Sie entweder diese Versionen mit [Revoscalepy auf dem Server](../package-management/installed-package-information.md). 

4. Geben Sie eine komplexere Reihe von Anweisungen aus. In diesem Beispiel wird mithilfe von Statistiken über Zusammenfassungen von [Rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) über ein lokales DataSet. Andere Funktionen erhalten den Speicherort der Beispieldaten an, und erstellen ein Datenquellenobjekt für eine lokale xdf-Datei.

  ```python
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

Bitten Sie den Datenbankadministrator, [konfigurieren Sie die folgenden Berechtigungen für Ihr Konto](../security/user-permission.md), in der Datenbank, in dem Sie Python verwenden:

+ **EXECUTE ANY EXTERNAL SCRIPT** zum Ausführen von Python auf dem Server.
+ **Db_datareader** Privilegien zum Ausführen von Abfragen zum Trainieren des Modells verwendet.
+ **Db_datawriter** Trainings- oder ausgewerteten Daten schreiben.
+ **Db_owner** zum Erstellen von Objekten, z. B. gespeicherte Prozeduren, Tabellen, Funktionen. 
  Sie müssen auch **Db_owner** Beispiel und Test-Datenbanken erstellen. 

Wenn Ihr Code Pakete, die nicht standardmäßig mit SQL Server installiert sind erfordert, ordnen Sie den Datenbankadministrator, um die mit der Instanz installierten Pakete zu erhalten. SQL Server ist eine sichere Umgebung, und es gibt Einschränkungen für die Pakete installiert werden können. Ad-hoc-Installation von Paketen als Teil des Codes wird nicht empfohlen, auch wenn Sie über Zugriffsrechte verfügen. Darüber hinaus immer sorgfältig Auswirkungen auf die Sicherheit vor der Installation neuer Pakete in der Serverbibliothek.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5: Erstellen von Testdaten

Wenn Sie Berechtigungen zum Erstellen einer Datenbank auf dem Remoteserver verfügen, können Sie den folgenden Code zum Erstellen der Iris-Demo-Datenbank verwendet wird, für die restlichen Schritte in diesem Artikel ausführen.

### <a name="1---create-the-irissql-database-remotely"></a>1: Erstellen Sie die Datenbank Irissql Remote

```python
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

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3 – verwenden Sie Revoscalepy-APIs, um eine Tabelle erstellen und Laden Sie die Iris-Daten

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6: Testen der Remoteverbindung

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


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7: Starten Sie die Python-Tools

Da Entwickler häufig mit mehreren Versionen von Python arbeiten, wird Python von Setup nicht zu Ihrem Pfad hinzufügen. Um die Python-ausführbare-Datei und die Bibliotheken, die von Setup installiert zu verwenden, verknüpfen Sie Ihre IDE **Python.exe** unter dem Pfad, die auch ermöglicht **Revoscalepy** und **Microsoftml**. 

### <a name="command-line"></a>Befehlszeile

Beim Ausführen von **Python.exe** aus c:\Programme\Microsoft Files\Microsoft\PyForMLS (oder den Speicherort, die Sie für die Installation der Python-Bibliothek angegeben), haben Sie Zugriff auf die vollständige Anaconda-Distribution sowie die Python-Microsoft Module, **Revoscalepy** und **Microsoftml**.

1. Wechseln Sie zu c:\Programme\Microsoft Files\Microsoft\PyForMLS, und doppelklicken Sie auf **Python.exe**.
2. Öffnen Sie die interaktive Hilfe: `help()`
3. Geben Sie den Namen eines Moduls an der Eingabeaufforderung Help: `help> revoscalepy`. Help gibt zurück, der Name, Inhalt des Pakets, Version und Speicherort.
4. Zurückgeben von Informationen zur Version und das Paket an die **Hilfe >** Eingabeaufforderung: `revoscalepy`. Drücken Sie mehrmals die EINGABETASTE zum Beenden der Hilfe.
5. Importieren Sie ein Modul: `import revoscalepy`


### <a name="jupyter-notebooks"></a>Jupyter-Notebooks

In diesem Artikel verwendet integrierte Jupyter Notebooks zur Veranschaulichung der Funktionsaufrufe **Revoscalepy**. Wenn Sie dieses Tool vertraut sind, wird der folgende Screenshot veranschaulicht, wie die einzelnen Teile zusammenpassen und aus welchem Grund alles "einfach funktioniert". 

Der übergeordnete Ordner c:\Programme\Microsoft Files\Microsoft\PyForMLS enthält Anaconda sowie die Microsoft-Pakete. Jupyter-Notebooks in Anaconda, enthalten ist, unter dem Ordner "Scripts", und die ausführbaren Python-Dateien werden automatisch mit Jupyter-Notebooks registriert. Finden Sie unter der Site-Packages-Pakete können in einem Notizbuch, einschließlich der drei Microsoft-Paketen für Data Science- und Machine Learning verwendet importiert werden.

  ![Ausführbare Dateien und Bibliotheken](media/jupyter-notebook-python-registration.png)

Wenn Sie eine andere IDE verwenden, müssen Sie die Python-Bibliotheken für ausführbare Dateien und die Funktion mit dem Tool zu verknüpfen. Die folgenden Abschnitte enthalten Anweisungen für häufig verwendete Tools.

### <a name="visual-studio"></a>Visual Studio

Wenn man [Python in Visual Studio](https://code.visualstudio.com/docs/languages/python), verwenden Sie die folgenden Konfigurationsoptionen, um eine Python-Umgebung zu erstellen, die Microsoft-Python-Pakete enthält.

| Konfigurationseinstellung | Wert |
|-----------------------|-------|
| **Präfixpfad** | C:\Programme\Microsoft Files\Microsoft\PyForMLS |
| **Cesta k interpretu** | C:\Programme\Microsoft Files\Microsoft\PyForMLS\python.exe |
| **Fenstermodus-interpreter** | C:\Programme\Microsoft Files\Microsoft\PyForMLS\pythonw.exe |

Hilfe zum Konfigurieren einer Python-Umgebung finden Sie [Verwalten von Python-Umgebungen in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

Legen Sie PyCharm des Interpreters die ausführbaren Python-Datei von Machine Learning-Server installiert.

1. Klicken Sie in ein neues Projekt unter "Einstellungen" auf **lokale hinzufügen**.

2. Geben Sie `C:\Program Files\Microsoft\PyForMLS\`.

Sie können nun importieren **Revoscalepy**, **Microsoftml**, oder **Azureml** Module. Sie können auch **Tools** > **Python-Konsole** ein interaktives Fenster öffnen.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie Tools und eine funktionierende Verbindung mit SQL Server haben, erweitern Sie Ihre Kenntnisse mit über die Python-Schnellstarts mit [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

> [!div class="nextstepaction"]
> [Schnellstart: Stellen Sie sicher, dass Python in SQL Server vorhanden ist.](../tutorials/quickstart-python-verify.md)