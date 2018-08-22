---
title: Einrichten von Python-Client-Tools für die Verwendung mit SQL Server-Machine Learning | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6f6823870060992586756dffa93aac6937d27d65
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40401300"
---
# <a name="set-up-python-client-tools-for-use-with-sql-server-machine-learning"></a>Einrichten von Python-Clienttools für die Verwendung mit SQL Server-Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Integration von Python ist verfügbar in SQL Server 2017 oder höher, wenn Sie Python, Machine Learning Services (Datenbankintern)-Unterstützung hinzufügen. Weitere Informationen finden Sie unter [Installieren von SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

Erfahren Sie in diesem Artikel, wie Entwicklungsarbeitsstationen so konfigurieren, dass Sie mit einem SQL-Remoteserver aktiviert für Python eine Verbindung herstellen können.

### <a name="evaluation-and-independent-development"></a>Evaluierungs- und unabhängige Entwicklung
 
Wenn Sie haben die Developer Edition und den Plan auf Python-Skript lokal arbeiten Sie mit SQL Server verschieben möchten, fahren Sie zum [Installieren einer IDE](#install-ide) und zeigen Sie das Tool auf lokalen Python-Bibliotheken, die von SQL Server verwendet.

> [!Tip]
> Eine Demonstration und video zur exemplarischen Vorgehensweise finden Sie [Ausführen von R als auch Remote in SQL Server von Jupyter-Notebooks oder eine beliebige IDE Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) oder [YouTube-Video](https://youtu.be/D5erljpJDjE).

## <a name="1---install-python-packages"></a>1: Installieren von Python-Pakete

Lokale Arbeitsstationen müssen die gleichen Versionen der Python-Paket wie die auf SQL Server: Revoscalepy und Microsftml. Zusätzliche Python-Pakete sind verfügbar, aber häufiger mit anderen Szenarien, in einem eigenständigen (nicht-Instanz) Machine Learning Server-Kontext verwendet werden. 

1. Laden Sie das Shellskript aus [ https://aka.ms/mls93-py ](https://aka.ms/mls93-py) (oder verwenden Sie [ https://aka.ms/mls-py ](https://aka.ms/mls-py) für die 9.2. die Version). Das Skript installiert, Anaconda 4.2.0, einschließlich Python 3.5.2, zusammen mit allen Paketen, die zuvor aufgeführten.

  Python-Komponenten werden bereitgestellt, über [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033). Wenn Sie eine andere Version benötigen, finden Sie unter [CAB-Downloads](../install/sql-ml-cab-downloads.md)

2. Öffnen der PowerShell-Fenster mit Administratorberechtigungen (mit der rechten Maustaste **als Administrator ausführen**).

3. Wechseln Sie zu dem Ordner, in dem Sie das Installationsprogramm heruntergeladen haben, und führen Sie das Skript. Hinzufügen der `-InstallFolder` Befehlszeilenargument an einen Ordner als Speicherort für die Bibliotheken. Zum Beispiel: 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls")
   ```

   Die Installation dauert einige Zeit in Anspruch. Sie können den Fortschritt im PowerShell-Fenster überwachen. Wenn Setup abgeschlossen ist, müssen Sie einen vollständigen Satz von Paketen. Wenn Sie angegeben haben z. B. `C:\mspythonlibs` als Ordnername, sehen Sie, dass die Pakete auf `C:\mspythonlibs\Lib\site-packages`. Andernfalls ist der Standardordner `C:\Program Files\Microsoft\PyForMLS1`.

Das Installationsskript ändert nicht die PATH-Umgebungsvariablen auf dem Computer, damit die neuen Python-Interpreter und die Module, die Sie soeben installiert haben, nicht automatisch für Ihre Tools verfügbar sind. Hilfe zum Verknüpfen der Python-Interpreter und Bibliotheken, Tools, finden Sie unter [5 – Installieren einer IDE](#install-ide).

<a name="python-tool"></a>
 
## <a name="2---open-a-python-prompt"></a>2: Öffnen Sie eine Python-Eingabeaufforderung

Integration von Python in Microsoft enthält integrierte Tools und Daten, zusätzlich zu den produktspezifische-Bibliotheken wie Revoscalepy und Microsoftml. Die folgenden Elemente sind in Client- und Server-Instanzen verfügbar, wenn Setup abgeschlossen wurde:

+ Python-Beispieldaten
+ 4.2 zur Anaconda-distribution 
+ Python ausführbare Dateien python.exe "und" pythonw.exe

> [!Tip] 
> Wir empfehlen die [Python für Windows – häufig gestellte Fragen](https://docs.python.org/3/faq/windows.html) allgemeine Purppose Informationen zum Ausführen von Python-Programmen für Windows.

### <a name="on-client-workstations"></a>Auf Clientarbeitsstationen

So verwenden Sie die Python-ausführbare-Datei installiert, indem Sie das Setupskript aus:

1. Wechseln Sie zu `C:\Program Files\Microsoft\PyForMLS\python.exe` oder welcher Position-Installationspfad.

2. Mit der rechten Maustaste **Python.exe** , und wählen Sie **als Administrator ausführen** ein interaktives Befehlszeilentools-Fenster zu öffnen.

### <a name="on-sql-server"></a>In SQLServer

SQL Server-Setup fügt die standard-Python-Tools und Ressourcen auf einer Serverinstanz. Wenn Sie die Developer Edition verwenden, und überprüfen Sie die Python-Version oder ad-hoc-Befehle ausführen möchten:

1. Wechseln Sie zu `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

2. Mit der rechten Maustaste **Python.exe** , und wählen Sie **als Administrator ausführen** ein interaktives Befehlszeilentools-Fenster zu öffnen.

> [!Note]
> In der Regel, um Ressourcenkonflikte zu vermeiden, sollten Sie **nicht** Python aus der Bibliothek für die Instanz auf dem Server ausführen, wenn Sie vermuten, ist es möglich ist SQL Server-Instanz Python-Code ausführen. Mit den Tools in der Bibliothek für die Instanz möglicherweise jedoch nützlich, wenn Sie versuchen, ein Problem, das auftritt, nur bei der Ausführung in SQL Server zu debuggen und ausführlichere Fehlermeldungen anzuzeigen, oder stellen Sie sicher, dass alle erforderlichen Pakete installiert werden soll.

## <a name="3---permissions"></a>3 - Berechtigungen

Herstellen der Verbindung mit einer Instanz von SQL Server zum Ausführen von Skripts und Daten hochzuladen, müssen Sie eine gültige Anmeldung auf dem Datenbankserver verfügen. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird empfohlen, dass Sie die integrierte Windows-Authentifizierung verwenden, mit der SQL-Anmeldung ist jedoch einfacher für einige Szenarien.

Mindestens muss das Konto zum Ausführen von Code verwendet die Berechtigung zum Lesen aus den Datenbanken, mit dem Sie arbeiten, sowie die speziellen Berechtigungen ausgeführt, ANY EXTERNAL SCRIPT haben. Die meisten Entwickler auch benötigen Berechtigungen zum Erstellen neuer Objekte in Form von gespeicherten Prozeduren, die mit Ihrem Skript, und Schreiben von Daten in Tabellen mit den Trainingsdaten oder Daten bewertet. 

Bitten Sie den Datenbankadministrator, konfigurieren Sie die folgenden Berechtigungen für das Konto in der Datenbank, in dem Sie Python verwenden:

+ **EXECUTE ANY EXTERNAL SCRIPT** zum Ausführen von Python auf dem Server.
+ **Db_datareader** Privilegien zum Ausführen von Abfragen zum Trainieren des Modells verwendet.
+ **Db_datawriter** Trainings- oder ausgewerteten Daten schreiben.
+ **Db_owner** zum Erstellen von Objekten, z. B. gespeicherte Prozeduren, Tabellen, Funktionen. 
  Sie müssen auch **Db_owner** Beispiel und Test-Datenbanken erstellen. 

Wenn Ihr Code Pakete, die nicht standardmäßig mit SQL Server installiert sind erfordert, ordnen Sie den Datenbankadministrator, um die mit der Instanz installierten Pakete zu erhalten. SQL Server ist eine sichere Umgebung, und es gibt Einschränkungen für die Pakete installiert werden können. Ad-hoc-Installation von Paketen als Teil des Codes wird nicht empfohlen, auch wenn Sie über Zugriffsrechte verfügen. Darüber hinaus immer sorgfältig Auswirkungen auf die Sicherheit vor der Installation neuer Pakete in der Serverbibliothek.

## <a name="4---test-connections"></a>4: Testen von Verbindungen

Nach der Installation alle Tools und Bibliotheken können Sie eine Verbindung mit dem Server herstellen, und stellen Sie sicher, dass Sie einen computekontext erstellen können, oder Python mit SQL Server kommunizieren kann.

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Überprüfen Sie, ob diese Revoscalepy von der Python-Befehlszeile aus funktioniert.

Zum Überprüfen, ob die **Revoscalepy** Modul kann geladen werden, den folgende Code über eine interaktive Python-Eingabeaufforderung ausführen. Der Code generiert eine datenzusammenfassung unter Verwendung der Python-Beispieldaten und [Rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). 

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

Beispielpfad Daten wird ausgegeben, sodass Sie bestimmen können, welche Instanz von Python aufgerufen wird.

### <a name="verify-that-python-can-be-called-from-a-local-sql-server"></a>Stellen Sie sicher, dass von einem lokalen SQL Server Python aufgerufen werden kann

Für eine lokale Entwicklungsumgebung, stellen Sie sicher, dass Python mit lokalen kommuniziert [SQL Server-Instanz, die für die externe Skripts konfiguriert](../install/sql-machine-learning-services-windows-install.md). Verwenden Sie zum Öffnen eines neuen SQL Server Management Studio **Abfrage** Fenster, und führen Sie alle einfachen Python-im Kontext einer gespeicherten Prozedur Befehl:

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

Es dauert eine Weile, um die Python-Laufzeit zum ersten Mal starten, aber wenn keine Fehler vorliegen, Sie wissen, dass der SQL Server Launchpad funktioniert und Python in SQL Server gestartet werden kann.

Zum Überprüfen, ob **Revoscalepy** finden Sie in der SQL Server-Instanz-Bibliothek, führen Sie das Skript basierend auf [Rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary), mit einigen geringfügigen Änderungen zum Generieren von Ergebnissen, die mit SQL Server kompatibel. 

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

Da Rx_summary ein Objekt des Typs zurückgibt `class revoscalepy.functions.RxSummary.RxSummaryResults`, enthält mehrere Elemente, um die Ergebnisse in SQL Server zu behandeln, können Sie nur den Datenrahmen in einem tabellarischen Format extrahieren.

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>Überprüfen Sie die Ausführung von Python in SQL Server als dem entfernten computekontext

Wenn Sie installiert haben **Revoscalepy** in Ihrer lokalen Python-Entwicklungsumgebung, sollten Sie zu einer Remoteinstanz von SQL Server 2017 eine Verbindung herstellen können, Python aktiviert wurde, und führen Sie ein ähnliches Codebeispiel, das mit dem Server als die Compute Context verwenden. 

Geben Sie für dieses Skript ausführen einen gültigen Servernamen ein, und eine vorhandene Datenbank aus. Dieses Skript verwendet nicht die Datenbank, aber die Verbindungszeichenfolge ist erforderlich.

```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=<server-name>;Database=TestDB;Trusted_Connection=True"
sqlcc = RxInSqlServer(
    connection_string = sql_conn_string,
    num_tasks = 1,
    auto_cleanup = False,
    console_output = True,
    execution_timeout_seconds = 0,
    wait = True
    )
rx_set_compute_context(sqlcc)

# get sample data and path
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

# generate summary
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

In diesem Beispiel wird die Zusammenfassung Objekt auf der Konsole statt zurückgeben wohlgeformte Tabellendaten zu SQL Server zurückgegeben. 

Darüber hinaus da [Rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) war aufgerufen wird, werden die Beispieldaten aus dem Ordner "Samples" auf dem SQL Server-Computer und nicht von diesem lokalen Ordner geladen.


<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5: Installieren einer IDE

Wenn Sie Skripts über die Befehlszeile einfach Debuggen, können Sie mit der standardmäßigen Python-Tools abrufen, indem. Wenn Sie neue Lösungen entwickeln, oder von einem Remoteclient aus arbeitet, empfehlen wir jedoch mit einem Python-IDE mit vollem Funktionsumfang. Beliebte Optionen sind:

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) mit Python
+ [KI-Tools für Visual Studio](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
+ Beliebten Drittanbieter-Tools wie Eclipse, PyCharm und Spyder

Visual Studio wird empfohlen, da es sich um Datenbankprojekte als auch für Machine Learning-Projekten unterstützt. Hilfe zum Konfigurieren einer Python-Umgebung finden Sie [Verwalten von Python-Umgebungen in Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

Da Entwickler häufig mit mehreren Versionen von Python arbeiten, wird Python von Setup nicht zu Ihrem Pfad hinzufügen. Um die Python-ausführbare-Datei und die Bibliotheken, die von Setup installiert zu verwenden, verknüpfen Sie Ihre IDE **Python.exe** unter dem Pfad, der auch Revoscalepy und Microsoftml bereitstellt. Z. B. für ein Python-Projekt in Visual Studio Ihrer benutzerdefinierten Umgebung würde angeben `C:\Program Files\Microsoft\PyForMLS`, `C:\Program Files\Microsoft\PyForMLS\python.exe` und `C:\Program Files\Microsoft\PyForMLS\pythonw.exe` für **Pfadpräfix**, **cesta k interpretu**, und  **Fenstermodus-Interpreter**bzw.

Weitere Anleitungen finden Sie unter [Link-Python-Tools und IDEs](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Der Artikel ist für die Microsoft Machine Learning Server geschrieben, damit die Python-Pfade unterscheiden, aber es zeigt, wie Sie mit Python-Bibliotheken aus verschiedenen Tools zu verknüpfen.

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie über Tools und eine funktionierende Verbindung mit SQL Server verfügen, durchlaufen Sie ein Tutorial, um eine genauere Betrachtung Revoscalepy-Funktionen und zwischen computekontexten wechseln zu erhalten.

> [!div class="nextstepaction"]
> [Erstellen eines Modells mithilfe von Revoscalepy und einem remotecomputekontext](../tutorials/use-python-revoscalepy-to-create-model.md)