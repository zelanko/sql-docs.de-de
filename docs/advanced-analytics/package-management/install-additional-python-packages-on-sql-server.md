---
title: Installieren von Python-Paketen mit PIP
description: Erfahren Sie, wie Sie python PIP verwenden, um neue Python-Pakete auf einer Instanz von SQL Server Machine Learning Services zu installieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: dc5addca9c9bbf01408cea89f85676813b97506c
ms.sourcegitcommit: 52d3902e7b34b14d70362e5bad1526a3ca614147
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70109757"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Installieren von Python-Paketen mit sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Funktionen im [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) -Paket verwenden, um neue Python-Pakete in einer Instanz von SQL Server Machine Learning Services zu installieren. Die Pakete, die Sie installieren, können in python-Skripts verwendet werden, die in-Database mit der T-SQL [-Anweisung SP-Execute-extern-Script-Transact-SQL](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ausgeführt werden.

Weitere Informationen zu Paket Speicherort und Installations Pfaden finden [Sie unter Get python Package Information](../package-management/python-package-information.md).

> [!NOTE]
> Der Python `pip install` -Standardbefehl wird nicht zum Hinzufügen von Python-Paketen auf SQL Server empfohlen. Verwenden Sie stattdessen **sqlmlutils** , wie in diesem Artikel beschrieben.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ Es muss [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der python-Sprachoption installiert sein.

+ Installieren Sie [python](https://www.python.org/) auf dem Client Computer, den Sie für die Verbindung mit SQL Server verwenden. Möglicherweise möchten Sie auch eine python-Entwicklungsumgebung wie [Visual Studio Code](https://code.visualstudio.com/download) mit der [python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python). 

+ Installieren Sie [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) oder [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) auf dem Client Computer, den Sie verwenden, um eine Verbindung mit SQL Server herzustellen. Sie können andere Daten Bank Verwaltungs-oder Abfrage Tools verwenden, aber in diesem Artikel wird davon ausgegangen, Azure Data Studio oder SSMS zu verwenden.

### <a name="other-considerations"></a>Andere Überlegungen

+ Pakete müssen Python 3,5-kompatibel sein und unter Windows ausgeführt werden.

+ Die python-paketbibliothek befindet sich im Ordner "Programme" Ihrer SQL Server Instanz. Standardmäßig sind für die Installation von in diesem Ordner Administrator Berechtigungen erforderlich. Weitere Informationen finden Sie unter [Speicherort der paketbibliothek](../package-management/python-package-information.md#default-python-library-location).

+ Die Paketinstallation erfolgt pro Instanz. Wenn Sie über mehrere Instanzen von Machine Learning Services verfügen, müssen Sie das Paket jedem hinzufügen.

+ Bevor Sie ein Paket hinzufügen, sollten Sie überprüfen, ob das Paket für die SQL Server Umgebung geeignet ist.

  + Es wird empfohlen, python in-Database für Aufgaben zu verwenden, die von einer engen Integration in die Datenbank-Engine profitieren, z. b. Machine Learning, anstatt von Tasks, die die Datenbank einfach Abfragen.

  + Wenn Sie Pakete hinzufügen, die zu viel Rechen Auslastung auf dem Server mit sich bringen, wird die Leistung beeinträchtigt.

  + In einer SQL Server Umgebung mit verstärkter Sicherheit sollten Sie Folgendes vermeiden:
    + Pakete, für die Netzwerk Zugriff erforderlich ist
    + Pakete, für die ein erhöhter Dateisystem Zugriff erforderlich ist
    + Pakete, die für die Webentwicklung oder andere Aufgaben verwendet werden, die nicht von der Ausführung innerhalb SQL Server profitieren

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installieren von sqlmlutils auf dem Client Computer

Um **sqlmlutils**verwenden zu können, müssen Sie es zunächst auf dem Client Computer installieren, mit dem Sie eine Verbindung mit SQL Server herstellen.

1. Laden Sie die aktuelle **sqlmlutils** -Zip https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist -Datei von auf den Client Computer herunter. Entzippen Sie die Datei nicht.

1. Öffnen Sie eine **Eingabeaufforderung** , und führen Sie den folgenden Befehl aus, um das **sqlmlutils** -Paket zu installieren. Ersetzen Sie den vollständigen Pfad der heruntergeladenen ZIP-Datei von **sqlmlutils** . in diesem Beispiel wird `c:\temp\sqlmlutils_0.6.0.zip`davon ausgegangen, dass die heruntergeladene Datei ist.

   ```console
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils_0.6.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>Hinzufügen eines python-Pakets auf SQL Server

Im folgenden Beispiel fügen Sie das [Text-Tools-](https://pypi.org/project/text-tools/) Paket SQL Server hinzu.

### <a name="add-the-package-online"></a>Paket online hinzufügen

Wenn der Client Computer, mit dem Sie eine Verbindung mit SQL Server herstellen, über Internet Zugriff verfügt, können Sie **sqlmlutils** verwenden, um das texttoolspaket und alle Abhängigkeiten über das Internet zu finden, und das Paket dann Remote auf einer SQL Server Instanz installieren.

1. Öffnen Sie auf dem Client Computer **python** oder eine python-Umgebung.

1. Verwenden Sie die folgenden Befehle, um das **Text Tools-** Paket zu installieren. Ersetzen Sie Ihre eigenen SQL Server Daten bankverbindungs Informationen.

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="yoursqluser", pwd="yoursqlpassword")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>Paket Offline hinzufügen

Wenn der Client Computer, den Sie für die Verbindung mit SQL Server verwenden, über keine Internetverbindung verfügt, können Sie **PIP** auf einem Computer mit Internet Zugriff verwenden, um das Paket und alle abhängigen Pakete in einen lokalen Ordner herunterzuladen. Anschließend kopieren Sie den Ordner auf den Client Computer, auf dem Sie das Paket Offline installieren können.

#### <a name="on-a-computer-with-internet-access"></a>Auf einem Computer mit Internetzugriff

1. Öffnen Sie eine **Eingabeaufforderung** , und führen Sie den folgenden Befehl aus, um einen lokalen Ordner zu erstellen, der das **Text-Tools-** Paket enthält. In diesem Beispiel wird der `c:\temp\text-tools`Ordner erstellt.

   ```console
   pip download text-tools -d c:\temp\text-tools
   ```

1. Kopieren Sie `text-tools` den Ordner auf den Client Computer. Im folgenden Beispiel wird davon ausgegangen, dass `c:\temp\packages\text-tools`Sie es in kopiert haben.

#### <a name="on-the-client-computer"></a>Auf dem Client Computer

Verwenden Sie **sqlmlutils** , um jedes Paket (WHL-Datei) zu installieren, das Sie im lokalen Ordner finden, den Sie erstellt haben. Es spielt keine Rolle, in welcher Reihenfolge Sie die Pakete installieren.

In diesem Beispiel gibt es keine Abhängigkeiten von **Text Tools** , daher gibt es nur eine Datei aus dem `text-tools` Ordner, die Sie installieren können. Im Gegensatz dazu enthält ein Paket, wie z. b. **scikit-Plot** , 11 Abhängigkeiten. Sie finden also 12 Dateien im Ordner (das **scikit-Plot-** Paket und die 11 abhängigen Pakete), und Sie installieren jede dieser Dateien.

Führen Sie das folgende Python-Skript aus. Ersetzen Sie Ihre eigenen SQL Server Daten bankverbindungs Informationen sowie den tatsächlichen Dateipfad und-Namen des Pakets. Wiederholen `sqlmlutils.SQLPackageManager` Sie die Anweisung für jede Paketdatei im Ordner.

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="yoursqluser", pwd="yoursqlpassword")
sqlmlutils.SQLPackageManager(connection).install("c:/temp/packages/text-tools/text_tools-1.0.0-py3-none-any.whl")
```

## <a name="use-the-package-in-sql-server"></a>Verwenden Sie das Paket in SQL Server

Sie können das Paket jetzt in einem Python-Skript in SQL Server verwenden. Zum Beispiel:

```python
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
from text_tools.finders import find_best_string
corpus = "Lorem Ipsum text"
query = "Ipsum"
first_match = find_best_string(query, corpus)
print(first_match)
  '
```

## <a name="remove-the-package-from-sql-server"></a>Entfernen Sie das Paket aus SQL Server

Wenn Sie das **Text-Tools-** Paket entfernen möchten, verwenden Sie den folgenden python-Befehl auf dem Client Computer, und verwenden Sie dabei dieselbe Verbindungs Variable, die Sie zuvor definiert haben.

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>Siehe auch

+ Informationen zu python-Paketen, die in SQL Server Machine Learning Services installiert sind, finden [Sie unter Informationen zum Python-Paket](../package-management/python-package-information.md).

+ Informationen zum Installieren von r-Paketen in SQL Server Machine Learning Services finden Sie unter [Installieren neuer r-Pakete auf SQL Server](../r/install-additional-r-packages-on-sql-server.md).
