---
title: Einrichten eines Data Science Clients für die Python-Entwicklung
description: Richten Sie eine lokale python-Umgebung (Jupyter Notebook oder pycharm) für Remote Verbindungen mit SQL Server Machine Learning Services mit python ein.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6f40f04d677d5dcfa758a13321009da3e535c5d4
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69634537"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Einrichten eines Data Science Clients für die Python-Entwicklung auf SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die python-Integration ist ab SQL Server 2017 oder höher verfügbar, wenn Sie die python-Option in einer [Machine Learning Services-Installation (in-Database)](../install/sql-machine-learning-services-windows-install.md)einschließen. 

Zum entwickeln und Bereitstellen von python-Lösungen für SQL Server müssen Sie die [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) -und andere python-Bibliotheken von Microsoft für Ihre entwicklungsarbeits Station installieren. Die revoscalepy-Bibliothek, die sich auch auf der Remote SQL Server Instanz befindet, koordiniert das Berechnen von Anforderungen zwischen beiden Systemen. 

In diesem Artikel erfahren Sie, wie Sie eine python-Entwicklungs Arbeitsstation so konfigurieren, dass Sie mit einer Remote SQL Server interagieren können, die für die Machine Learning-und python-Integration aktiviert ist. Nachdem Sie die Schritte in diesem Artikel ausgeführt haben, verfügen Sie über dieselben python-Bibliotheken wie auf SQL Server. Sie wissen auch, wie Berechnungen aus einer lokalen python-Sitzung an eine Python-Remote Sitzung auf SQL Server Übertragung erfolgt.

![Client-Server-Komponenten](media/sqlmls-python-client-revo.png "Lokale und Remote-python-Sitzungen und-Bibliotheken")

Um die Installation zu überprüfen, können Sie integrierte jupyter-Notebooks verwenden, wie in diesem Artikel beschrieben, oder Sie können [die Bibliotheken](#install-ide) mit pycharm oder einer anderen IDE verknüpfen, die Sie normalerweise verwenden.

> [!Tip]
> Eine Videovorführung dieser Übungen finden Sie unter [Ausführen von R und python in SQL Server von jupyter-Notebooks aus](https://youtu.be/D5erljpJDjE).

> [!Note]
> Eine Alternative zur Installation der Client Bibliothek ist die Verwendung eines [eigenständigen Servers](../install/sql-machine-learning-standalone-windows-install.md) als Rich Client, den einige Kunden für eine tiefere szenarioarbeit bevorzugen. Ein eigenständiger Server ist vollständig von SQL Server entkoppelt, aber da er über dieselben python-Bibliotheken verfügt, können Sie ihn als Client für SQL Server in-Database-Analyse verwenden. Sie können Sie auch für nicht-SQL-bezogene Arbeiten verwenden, einschließlich der Möglichkeit, Daten von anderen Daten Plattformen zu importieren und zu modellieren. Wenn Sie einen eigenständigen Server installieren, finden Sie die ausführbare python-Datei an `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`diesem Speicherort:. Öffnen Sie zum Überprüfen der Installation [ein jupyter-Notebook](#python-tools) , um Befehle mithilfe von "python. exe" an diesem Speicherort auszuführen.

## <a name="commonly-used-tools"></a>Häufig verwendete Tools

Egal, ob Sie ein Python-Entwickler sind, der neu bei SQL ist, oder ein SQL-Entwickler, der in Python und in-Database-Analysen neu ist, Sie benötigen sowohl ein python-Entwicklungs Tool als auch einen T-SQL-Abfrage-Editor wie [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) , um alle Funktionen von Daten bankübergreifende Analyse.

Für die Python-Entwicklung können Sie jupyter Notebooks verwenden, das in der von SQL Server installierten Anaconda-Distribution gebündelt ist. In diesem Artikel wird erläutert, wie jupyter-Notebooks gestartet werden, sodass Sie Python-Code lokal und Remote auf SQL Server ausführen können.

SSMS ist ein separater Download, der zum Erstellen und Ausführen gespeicherter Prozeduren auf SQL Server nützlich ist, einschließlich derjenigen, die Python-Code enthalten. Fast jeder Python-Code, den Sie in jupyter-Notebooks schreiben, kann in eine gespeicherte Prozedur eingebettet werden. Sie können andere Schnellstarts schrittweise durchlaufen, um mehr über [SSMS und eingebettete python](../tutorials/quickstart-python-verify.md)zu erfahren.

## <a name="1---install-python-packages"></a>1: Installieren von Python-Paketen

Lokale Arbeitsstationen müssen die gleichen python-Paketversionen wie auf SQL Server aufweisen, einschließlich der Basis-Anaconda 4.2.0 mit der Python 3.5.2-Verteilung und Microsoft-spezifischen Paketen.

Mit einem Installationsskript werden drei Microsoft-spezifische Bibliotheken zum Python-Client hinzugefügt. Das Skript installiert [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), das zum Definieren von Datenquellen Objekten und des computekontexts verwendet wird. Es installiert [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) , das Machine Learning-Algorithmen bereitstellt. Das [azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) -Paket wird ebenfalls installiert, es gilt jedoch für operationalisierungsaufgaben, die einem eigenständigen Machine Learning Server Kontext zugeordnet sind, und kann für Daten bankübergreifende Analysen eingeschränkt verwendet werden.

1. Herunterladen eines Installations Skripts.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py)installiert die Version 9.2.1 der Microsoft Python-Pakete. Diese Version entspricht einem Standard SQL Server-Instanz. 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py)installiert Version 9,3 der Microsoft Python-Pakete. Diese Version ist eine bessere Wahl, wenn Ihre Remote SQL Server-Instanz [an Machine Learning Server 9,3 gebunden](../install/upgrade-r-and-python.md)ist.

2. Öffnen Sie ein PowerShell-Fenster mit erhöhten Administratorrechten (Klicken Sie mit der rechten Maustaste auf **als Administrator ausführen**).

3. Wechseln Sie zu dem Ordner, in dem Sie den Installer heruntergeladen haben, und führen Sie das Skript aus. Fügen Sie `-InstallFolder` das Befehlszeilenargument hinzu, um einen Ordner Speicherort für die Bibliotheken anzugeben. Zum Beispiel: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Wenn Sie den Installationsordner weglassen, lautet der Standardwert c:\programme\microsoft\pyformls.

Die Installation nimmt einige Zeit in Anspruch. Sie können den Fortschritt im PowerShell-Fenster überwachen. Wenn das Setup abgeschlossen ist, verfügen Sie über einen vollständigen Satz von Paketen. 

> [!Tip] 
> Wir empfehlen die häufig gestellten Fragen zu [python für Windows](https://docs.python.org/3/faq/windows.html) für allgemeine Informationen zum Ausführen von Python-Programmen unter Windows.

## <a name="2---locate-executables"></a>2\. ausführbare Dateien suchen

Auflisten Sie in PowerShell den Inhalt des-Installations Ordners, um zu bestätigen, dass python. exe, Skripts und andere Pakete installiert sind. 

1. Geben `cd \` Sie ein, um zum Stamm Laufwerk zu wechseln, und geben Sie dann den `-InstallFolder` Pfad ein, den Sie im vorherigen Schritt angegeben haben. Wenn Sie diesen Parameter während der Installation ausgelassen haben, lautet `cd C:\Program Files\Microsoft\PyForMLS`der Standardwert.

2. Geben `dir *.exe` Sie ein, um die ausführbaren Dateien aufzulisten. " **Python. exe**", " **pythonw. exe**" und " **Uninstall-Anaconda. exe**" sollten angezeigt werden.

  ![Liste der ausführbaren python-Dateien](media/powershell-python-exe.png)
   
Denken Sie bei Systemen mit mehreren Versionen von python daran, diese spezielle python. exe-Datei zu verwenden, wenn Sie **revoscalepy** -und andere Microsoft-Pakete laden möchten.

> [!Note] 
> Mit dem Installationsskript wird die PATH-Umgebungsvariable auf dem Computer nicht geändert. Dies bedeutet, dass die neuen Python-Interpreter und-Module, die Sie soeben installiert haben, nicht automatisch für andere Tools verfügbar sind, die Sie möglicherweise haben. Hilfe zum Verknüpfen des Python-Interpreters und der Bibliotheken mit Tools finden Sie unter [Installieren einer IDE](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3: Öffnen von jupyter-Notebooks

Anaconda umfasst jupyter Notebooks. Erstellen Sie im nächsten Schritt ein Notebook, und führen Sie einen Python-Code aus, der die soeben installierten Bibliotheken enthält.

1. Öffnen Sie an der PowerShell-Eingabeaufforderung im Verzeichnis "c:\programme\microsoft\pyformls" jupyter Notebooks aus dem Ordner "Scripts":

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  Ein Notebook sollte in Ihrem Standardbrowser unter `https://localhost:8889/tree`geöffnet werden.

  Eine andere Möglichkeit zum Starten ist, dass Sie auf **jupyter-Notebook. exe**doppelklicken. 

2. Klicken Sie auf **neu** und dann auf **python 3**.

  ![jupyter Notebook mit neuer python 3-Auswahl](media/jupyter-notebook-new-p3.png)

3. Geben `import revoscalepy` Sie ein, und führen Sie den Befehl aus, um eine der Microsoft-spezifischen Bibliotheken zu laden.

4. Geben Sie ein `print(revoscalepy.__version__)` und führen Sie aus, um die Versionsinformationen zurückzugeben 9\.2.1 oder 9.3.0 sollte angezeigt werden. Sie können eine dieser Versionen mit [revoscalepy auf dem Server](../package-management/r-package-information.md)verwenden.

4. Geben Sie eine komplexere Reihe von Anweisungen ein. In diesem Beispiel werden zusammenfassende Statistiken mithilfe von [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) über ein lokales DataSet generiert. Andere Funktionen rufen den Speicherort der Beispiel Daten ab und erstellen ein Datenquellen Objekt für eine lokale Xdf-Datei.

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

Der folgende Screenshot zeigt die Eingabe und einen Teil der Ausgabe, die aus Gründen der Kürze gekürzt wurden.

  ![jupyter-Notebook, das revoscalepy-Eingaben und-Ausgaben anzeigt](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4: SQL-Berechtigungen erhalten

Zum Herstellen einer Verbindung mit einer Instanz von SQL Server zum Ausführen von Skripts und Hochladen von Daten müssen Sie über einen gültigen Anmelde Namen auf dem Daten Bank Server verfügen. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird empfohlen, die integrierte Windows-Authentifizierung zu verwenden, aber die Verwendung der SQL-Anmeldung ist für einige Szenarien einfacher, insbesondere wenn Ihr Skript Verbindungs Zeichenfolgen zu externen Daten enthält.

Das zum Ausführen von Code verwendete Konto muss mindestens über die Berechtigung zum Lesen der Datenbanken verfügen, mit denen Sie arbeiten, sowie über die spezielle Berechtigung zum Ausführen externer Skripts. Die meisten Entwickler benötigen auch Berechtigungen zum Erstellen gespeicherter Prozeduren und zum Schreiben von Daten in Tabellen, die Trainingsdaten oder bewertete Daten enthalten. 

Bitten Sie den Datenbankadministrator, [die folgenden Berechtigungen für Ihr Konto](../security/user-permission.md)in der Datenbank zu konfigurieren, in der Sie python verwenden:

+ **Führen Sie ein beliebiges externes Skript** zum Ausführen von python auf dem Server aus.
+ **db_datareader** Berechtigungen zum Ausführen der Abfragen, die zum Trainieren des Modells verwendet werden.
+ **db_datawriter** Schreiben von Trainingsdaten oder bewerteten Daten.
+ **db_owner** Erstellen von Objekten, wie z. b. gespeicherte Prozeduren, Tabellen und Funktionen. 
  Außerdem benötigen Sie **db_owner** , um Beispiel-und Testdatenbanken zu erstellen. 

Wenn für den Code Pakete erforderlich sind, die nicht standardmäßig mit SQL Server installiert werden, müssen Sie mit dem Datenbankadministrator anordnen, damit die Pakete mit der-Instanz installiert werden. SQL Server ist eine gesicherte Umgebung, und es gibt Einschränkungen hinsichtlich der Installation von Paketen. Die Ad-hoc-Installation von Paketen als Teil Ihres Codes wird nicht empfohlen, auch wenn Sie über Rechte verfügen. Berücksichtigen Sie auch immer die Sicherheitsrisiken, bevor Sie neue Pakete in der Server Bibliothek installieren.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5: Erstellen von Testdaten

Wenn Sie über Berechtigungen zum Erstellen einer Datenbank auf dem Remote Server verfügen, können Sie den folgenden Code ausführen, um die Iris-Demo Datenbank zu erstellen, die für die restlichen Schritte in diesem Artikel verwendet wird.

### <a name="1---create-the-irissql-database-remotely"></a>1: Remote Erstellung der irissql-Datenbank

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

### <a name="2---import-iris-sample-from-sklearn"></a>2: Importieren von IRIS-Beispielen aus "sklearn"

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3\. Verwenden von revoscalepy-APIs zum Erstellen einer Tabelle und Laden der Iris-Daten

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6: Testen der Remote Verbindung

Stellen Sie vor dem Ausführen des nächsten Schritts sicher, dass Sie über Berechtigungen für die SQL Server-Instanz und eine Verbindungs Zeichenfolge für die [IRIS-Beispieldatenbank](../tutorials/demo-data-iris-in-sql.md)verfügen. Wenn die Datenbank nicht vorhanden ist und Sie über ausreichende Berechtigungen verfügen, können Sie [mithilfe dieser Inline Anweisungen eine Datenbank erstellen](#create-iris-remotely).

Ersetzen Sie die Verbindungs Zeichenfolge durch gültige Werte. Der Beispielcode verwendet `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` , aber der Code sollte einen Remote Server, möglicherweise mit einem Instanznamen, und eine Anmelde Informationen-Option angeben, die der Datenbank-Benutzeranmeldung zugeordnet wird.

### <a name="define-a-function"></a>Definieren einer Funktion

Im folgenden Code wird eine Funktion definiert, die Sie in einem späteren Schritt an SQL Server senden. Bei der Ausführung werden Daten und Bibliotheken (revoscalepy, Pandas, matplotlib) auf dem Remote Server verwendet, um Punkt Diagramme des IRIS-Datasets zu erstellen. Der Bytestream der PNG-Datei wird an jupyter-Notebooks zurückgegeben, um Sie im Browser zu Rendering.

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

Erstellen Sie in diesem Beispiel den remotecomputekontext, und senden Sie die Ausführung der Funktion mit [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec)an SQL Server. Die **rx_exec** -Funktion ist hilfreich, da Sie einen computekontext als Argument akzeptiert. Jede Funktion, die Sie Remote ausführen möchten, muss über ein computecontext-Argument verfügen. Einige Funktionen, z. b. [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) , unterstützen dieses Argument direkt. Für Vorgänge, die nicht verwendet werden, können Sie **rx_exec** verwenden, um Ihren Code in einem remotecomputekontext bereitzustellen.

In diesem Beispiel mussten keine Rohdaten aus SQL Server in den Jupyter Notebook übertragen werden. Alle Berechnungen erfolgen innerhalb der Iris-Datenbank, und nur die Bilddatei wird an den Client zurückgegeben.

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

Der folgende Screenshot zeigt die Ausgabe des Eingabe-und Punkt Diagramms.

  ![jupyter-Notebook mit Punkt Diagramm Ausgabe](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7: Starten von python aus Tools

Da Entwickler häufig mit mehreren Versionen von Python arbeiten, fügt das Setup python nicht zu Ihrem Pfad hinzu. Wenn Sie die von Setup installierten ausführbaren python-Dateien und Bibliotheken verwenden möchten, verknüpfen Sie Ihre IDE mit " **python. exe** " unter dem Pfad, der auch **revoscalepy** und **microsoftml**bereitstellt. 

### <a name="command-line"></a>Befehlszeile

Wenn Sie " **python. exe** " aus "c:\programme\microsoft\pyformls" (oder einem beliebigen Speicherort, den Sie für die Installation der Python-Client Bibliothek angegeben haben) ausführen, haben Sie Zugriff auf die vollständige Anaconda-Distribution sowie die Microsoft Python-Module, **revoscalepy.** und **microsoftml**.

1. Wechseln Sie zu "c:\programme\microsoft\pyformls", und doppelklicken Sie auf " **python. exe**".
2. Interaktive Hilfe öffnen:`help()`
3. Geben Sie den Namen eines Moduls an der Eingabeaufforderung ein `help> revoscalepy`:. Hilfe gibt den Namen, den Paket Inhalt, die Version und den Datei Speicherort zurück.
4. Rückgabe von Versions-und Paketinformationen an der Eingabeaufforderung `revoscalepy`der **Hilfe >** :. Drücken Sie mehrmals die EINGABETASTE, um die Hilfe zu beenden.
5. Importieren eines Moduls:`import revoscalepy`


### <a name="jupyter-notebooks"></a>Jupyter-Notebooks

In diesem Artikel werden integrierte jupyter-Notebooks verwendet, um Funktionsaufrufe von **revoscalepy**zu veranschaulichen. Wenn Sie mit diesem Tool noch nicht vertraut sind, wird im folgenden Screenshot veranschaulicht, wie die Teile zusammenpassen und warum alles "funktioniert". 

Der übergeordnete Ordner "c:\programme\microsoft\pyformls" enthält Anaconda sowie die Microsoft-Pakete. Jupyter Notebooks sind in Anaconda unter dem Ordner Scripts enthalten, und die ausführbaren python-Dateien werden automatisch bei jupyter-Notebooks registriert. Pakete, die unter Website Paketen gefunden werden, können in ein Notebook importiert werden, einschließlich der drei Microsoft-Pakete, die für Data Science und Machine Learning verwendet werden.

  ![Ausführbare Dateien und Bibliotheken](media/jupyter-notebook-python-registration.png)

Wenn Sie eine andere IDE verwenden, müssen Sie die ausführbaren python-Dateien und Funktionsbibliotheken mit Ihrem Tool verknüpfen. In den folgenden Abschnitten finden Sie Anweisungen zu häufig verwendeten Tools.

### <a name="visual-studio"></a>Visual Studio

Wenn Sie [python in Visual Studio](https://code.visualstudio.com/docs/languages/python)verwenden, verwenden Sie die folgenden Konfigurationsoptionen zum Erstellen einer python-Umgebung, die die Microsoft Python-Pakete enthält.

| Konfigurationseinstellung | Wert |
|-----------------------|-------|
| **Präfix Pfad** | C:\programme\microsoft\pyformls |
| **Interpreterpfad** | C:\programme\microsoft\pyformls\python.exe |
| **Windowed-Interpreter** | C:\programme\microsoft\pyformls\pythonw.exe |

Hilfe zum Konfigurieren einer python-Umgebung finden Sie unter [Verwalten von python-Umgebungen in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

Legen Sie den Interpreter in pycharm auf die von Machine Learning Server installierte python-ausführbare Datei fest.

1. Klicken Sie in einem neuen Projekt unter Einstellungen auf **lokale hinzufügen**.

2. Geben `C:\Program Files\Microsoft\PyForMLS\`Sie ein.

Sie können jetzt die Module **revoscalepy**, **microsoftml**oder **azureml** importieren. Sie können auch **Tools** > **python Console** auswählen, um ein interaktives Fenster zu öffnen.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie über Tools und eine funktionierende Verbindung mit SQL Server verfügen, erweitern Sie Ihre Fähigkeiten, indem Sie die python-Schnellstarts mit [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)ausführen.

> [!div class="nextstepaction"]
> [Schnellstart: Überprüfen, ob python vorhanden ist SQL Server](../tutorials/quickstart-python-verify.md)