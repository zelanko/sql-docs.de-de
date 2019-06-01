---
title: Schnellstart für die Überprüfung von Python ist in SQL Server vorhanden.
description: Schnellstart für das sicherstellen, dass Python und Machine Learning Services in SQL Server vorhanden sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 09b96f6934fec9e24ca4a254a1d14c23327ebe5b
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454706"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>Schnellstart: Überprüfen der Verfügbarkeit von Python in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server umfasst die Python-sprachunterstützung für Data Science-Analyse in residenten SQL Server-Daten. Ausführung des Skripts wird mithilfe von gespeicherten Prozeduren, die mit einem der folgenden Methoden:

+ Integrierte [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) gespeicherte Prozedur, die Python-Skript in als Eingabeparameter übergeben.
+ Umschließen von Python-Skript in einem [benutzerdefinierte gespeicherte Prozedur](sqldev-in-database-r-for-sql-developers.md) , die Sie erstellen.

In diesem Schnellstart werden Sie sicherstellen, dass [SQL Server 2017-Machine Learning Services](../what-is-sql-server-machine-learning.md) installiert und konfiguriert ist.

## <a name="prerequisites"></a>Erforderliche Komponenten

Diese Übung ist erforderlich, den Zugriff auf eine Instanz von SQL Server mit [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) installiert.

Ihre SQL Server-Instanz kann in einer Azure-VM oder lokal sein. Machen Sie sich bewusst, dass das Feature "external Skripterstellung" standardmäßig deaktiviert ist. Sie müssen möglicherweise [aktivieren externer Skripts](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen Sie, ob **SQL Server Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

Sie benötigen außerdem ein Tool für die Ausführung von SQL-Abfragen. Sie können führen Sie die Python-Skripts, die alle datenbankverwaltung mit oder Tool Abfragen, solange es eine Verbindung mit SQL Server-Instanz herstellen kann, und führen Sie eine T-SQL-Abfrage oder gespeicherte Prozedur. Dieser Schnellstart verwendet [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-python-exists"></a>Stellen Sie sicher, dass Python vorhanden ist.

Sie können bestätigen, Machine Learning-Dienste (ist aktiviert für Ihre SQL Server-Instanz und welche Version von Python installiert ist. Führen Sie die folgenden Schritte aus.

1. Öffnen Sie SQL Server Management Studio, und Verbinden mit Ihrer SQL Server-Instanz.

2. Führen Sie den folgenden Code ein. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. Die Python `print` Funktionsergebnis ist die Version, die **Nachrichten** Fenster. In der folgenden Beispielausgabe sehen Sie, dass SQL Server in diesem Fall Python Version 3.5.2 installiert haben.

    **Ergebnisse**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

Wenn Sie eine Fehlermeldung erhalten, gibt es verschiedene Dinge, die Sie tun können, um sicherzustellen, dass die Instanz und Python kommunizieren kann.

Probleme bei der Installation zunächst auszuschließen. Konfiguration nach der Installation ist erforderlich, um die Verwendung externer Codebibliotheken zu aktivieren. Finden Sie unter [Installieren von SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md). Ebenso, stellen Sie sicher, dass der Launchpad-Dienst ausgeführt wird.

Außerdem müssen Sie die Windows-Benutzergruppe hinzufügen `SQLRUserGroup` als Anmeldung auf der Instanz, um sicherzustellen, dass Launchpad Kommunikation zwischen Python und SQL Server bereitstellen kann. (Die gleiche Gruppe wird verwendet, für beide R und Python-code die Ausführung). Weitere Informationen finden Sie unter [Erstellen eines Anmeldenamens für SQLRUserGroup](../security/create-a-login-for-sqlrusergroup.md).

Darüber hinaus müssen Sie zum Aktivieren von Netzwerkprotokollen, die deaktiviert wurden oder öffnen Sie die Firewall, damit SQL Server mit externen Clients kommunizieren können. Weitere Informationen finden Sie unter [Problembehandlungseinrichtung](../common-issues-external-script-execution.md).

## <a name="call-revoscalepy-functions"></a>Die Revoscalepy-Funktionen aufrufen

Zum Überprüfen, ob **Revoscalepy** verfügbar ist, führen Sie ein Beispielskript, das enthält [Rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) , die eine statistischen Zusammenfassungen Daten erzeugt. Das folgende Skript veranschaulicht, wie eine Datei mit Beispieldaten xdf aus integrierten Beispiele im Revoscalepy abgerufen wird. Die RxOptions-Funktion bietet die **SampleDataDir** Parameter, der den Speicherort der Beispieldateien zurückgibt.

Da Rx_summary ein Objekt des Typs zurückgibt `class revoscalepy.functions.RxSummary.RxSummaryResults`, die mehrere Elemente enthält, können Sie nur den Datenrahmen in einem tabellarischen Format extrahieren Pandas.

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

## <a name="list-python-packages"></a>Auflisten von Python-Pakete

Microsoft bietet eine Anzahl von Python-Pakete vorinstalliert mit Machine Learning-Dienste in Ihrer SQL Server-Instanz. Führen Sie zum Anzeigen einer Liste von der, die Python Pakete installiert sind, einschließlich Version, die folgenden Schritte aus.

1. Führen Sie das folgende Skript für Ihre SQL Server-Instanz.

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. Die Ausgabe stammt aus `pip.get_installed_distributions()` in Python und als zurückgegeben `STDOUT` Nachrichten.

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

Nun, da Sie bestätigt haben, dass die Instanz mit Python verwendet werden kann, nehmen Sie einen genaueren Blick auf eine grundlegende Python-Interaktion.

> [!div class="nextstepaction"]
> [Schnellstart: "Hello World"-Python-Skript in SQL Server](quickstart-python-run-using-t-sql.md)
