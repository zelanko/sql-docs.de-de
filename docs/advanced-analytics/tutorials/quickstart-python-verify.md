---
title: Schnellstart zum Überprüfen, ob python in SQL Server vorhanden ist
description: Schnellstart zum Überprüfen, ob python und Machine Learning Services in SQL Server vorhanden sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 98e89cf61e5c53793108a455873382da00a8ea35
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715452"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>Schnellstart: Überprüfen der Verfügbarkeit von Python in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server bietet Unterstützung für die Python-Sprache für Data Science Analytics in Residenten SQL Server Daten. Die Skriptausführung erfolgt mithilfe gespeicherter Prozeduren, wobei eine der folgenden Ansätze verwendet wird:

+ Integrierte gespeicherte Prozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) , die das Python-Skript in als Eingabeparameter übergibt.
+ Wrappen Sie das Python-Skript in einer von Ihnen erstellten [benutzerdefinierten gespeicherten Prozedur](sqldev-in-database-r-for-sql-developers.md) .

In dieser Schnellstartanleitung überprüfen Sie, ob [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) installiert und konfiguriert ist.

## <a name="prerequisites"></a>Vorraussetzungen

Diese Übung erfordert Zugriff auf eine Instanz von SQL Server, auf der [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) installiert ist.

Ihre SQL Server Instanz kann sich auf einem virtuellen Azure-Computer oder lokal befinden. Beachten Sie, dass das Feature für die externe Skripterstellung standardmäßig deaktiviert ist. Daher müssen Sie möglicherweise [externe Skripterstellung aktivieren](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen, ob **SQL Server-Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen. Sie können die python-Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="verify-python-exists"></a>Überprüfen von python vorhanden

Sie können überprüfen, ob Machine Learning Services (für Ihre SQL Server Instanz aktiviert ist und welche Version von Python installiert ist. Führen Sie die folgenden Schritte aus.

1. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit Ihrer SQL Server Instanz her

2. Führen Sie den folgenden Code aus. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. Die python `print` -Funktion gibt die Version an das Fenster **Meldungen** zurück. In der Beispielausgabe unten sehen Sie, dass in diesem Fall die Python-Version 3.5.2 in SQL Server installiert ist.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

Wenn Sie Fehler erhalten, können Sie sicherstellen, dass die Instanz und die python kommunizieren können.

Schließen Sie zunächst alle Installationsprobleme aus. Die Konfiguration nach der Installation ist erforderlich, um die Verwendung externer Codebibliotheken zu aktivieren. Siehe [Install SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md). Stellen Sie auch sicher, dass der Launchpad-Dienst ausgeführt wird.

Sie müssen auch die Windows-Benutzergruppe `SQLRUserGroup` als Anmelde Namen für die-Instanz hinzufügen, um sicherzustellen, dass Launchpad die Kommunikation zwischen Python und SQL Server bereitstellen kann. (Dieselbe Gruppe wird für die Ausführung von R-und Python-Code verwendet.) Weitere Informationen finden Sie unter [Create a Login for sqlrusergroup](../security/create-a-login-for-sqlrusergroup.md).

Außerdem müssen Sie möglicherweise Netzwerkprotokolle aktivieren, die deaktiviert wurden, oder die Firewall öffnen, damit SQL Server mit externen Clients kommunizieren kann. Weitere Informationen finden Sie unter [Problem](../common-issues-external-script-execution.md)Behandlung beim Setup.

## <a name="call-revoscalepy-functions"></a>Revoscalepy-Funktionen aufzurufen

Um zu überprüfen, ob **revoscalepy** verfügbar ist, führen Sie ein Beispielskript aus, das [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) enthält, das statistische Zusammenfassungs Daten erzeugt. Das folgende Skript veranschaulicht, wie eine Sample. Xdf-Datendatei aus integrierten Beispielen in revoscalepy abgerufen wird. Die rxoptions-Funktion stellt den **sampledatadir** -Parameter bereit, der den Speicherort der Beispieldateien zurückgibt.

Da rx_summary ein Objekt vom Typ `class revoscalepy.functions.RxSummary.RxSummaryResults`zurückgibt, das mehrere Elemente enthält, können Sie Pandas verwenden, um nur den Datenrahmen in einem Tabellenformat zu extrahieren.

```sql
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

## <a name="list-python-packages"></a>Auflisten von Python-Paketen

Microsoft stellt eine Reihe von Python-Paketen bereit, die mit Machine Learning Services in Ihrer SQL Server Instanz vorinstalliert sind. Führen Sie die folgenden Schritte aus, um eine Liste der installierten Python-Pakete anzuzeigen, einschließlich der Version.

1. Führen Sie das folgende Skript auf Ihrer SQL Server Instanz aus.

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. Die Ausgabe erfolgt `pip.get_installed_distributions()` in Python und wird als `STDOUT` Nachrichten zurückgegeben.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    xlwt 1.2.0
    XlsxWriter 0.9.6
    xlrd 1.0.0
    win-unicode-console 0.5
    widgetsnbextension 2.0.0
    wheel 0.29.0
    Werkzeug 0.12.1
    wcwidth 0.1.7
    unicodecsv 0.14.1
    traitlets 4.3.2
    tornado 4.4.2
    toolz 0.8.2
    testpath 0.3
    tables 3.2.2
    sympy 1.0
    statsmodels 0.8.0
    sqlparse 0.1.19
    SQLAlchemy 1.1.9
    snowballstemmer 1.2.1
    six 1.10.0
    simplegeneric 0.8.1
    seaborn 0.7.1
    scipy 0.19.0
    scikit-learn 0.18.1
    ...
    ```

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun bestätigt haben, dass Ihre Instanz für die Arbeit mit Python bereit ist, sollten Sie sich einen genaueren Einblick in die grundlegende python-Interaktion ansehen.

> [!div class="nextstepaction"]
> [Schnellstart: "Hello World"-Python-Skript in SQL Server](quickstart-python-run-using-t-sql.md)
