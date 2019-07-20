---
title: Installieren neuer python-Sprachpakete
description: Fügen Sie SQL Server 2017 Machine Learning Services (in-Database) und Machine Learning Server (eigenständig) neue Python-Pakete hinzu.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/16/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0e305f778ee132c06e9a2b08c8cec64f0535846a
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345515"
---
# <a name="install-new-python-packages-on-sql-server"></a>Installieren neuer Python-Pakete auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie neue Python-Pakete auf einer Instanz von SQL Server 2017 Machine Learning Services installieren. Im Allgemeinen ähnelt der Prozess zum Installieren neuer Pakete dem in einer python-Standardumgebung. Es sind jedoch einige zusätzliche Schritte erforderlich, wenn der Server nicht über eine Internetverbindung verfügt.

Weitere Informationen zum Speicherort und zu den Installations Pfaden finden [Sie unter Informationen zu R-oder python-Paketen](../package-management/installed-package-information.md).

## <a name="prerequisites"></a>Vorraussetzungen

+ [SQL Server 2017 Machine Learning Services (in-Database)](../install/sql-machine-learning-services-windows-install.md) mit der python-Sprachoption. 

+ Pakete müssen Python 3,5-kompatibel sein und unter Windows ausgeführt werden. 

+ Der Administrator Zugriff auf den-Server ist erforderlich, um-Pakete zu installieren.

## <a name="considerations"></a>Weitere Überlegungen

Berücksichtigen Sie vor dem Hinzufügen von Paketen, ob das Paket für die SQL Server Umgebung geeignet ist. Ein Datenbankserver ist in der Regel ein frei gegebenes Asset, das mehrere Workloads unter Wenn Sie Pakete hinzufügen, die zu viel Rechen Auslastung auf dem Server mit sich bringen, wird die Leistung beeinträchtigt. 

Darüber hinaus führen einige beliebte Python-Pakete (wie Flask) Aufgaben wie die Webentwicklung aus, die für eine eigenständige Umgebung besser geeignet sind. Es wird empfohlen, python in-Database für Aufgaben zu verwenden, die von einer engen Integration in die Datenbank-Engine profitieren, z. b. Machine Learning, anstatt von Tasks, die die Datenbank einfach Abfragen.

Datenbankserver sind häufig gesperrt. In vielen Fällen wird der Internet Zugriff vollständig blockiert. Bei Paketen mit einer langen Liste von Abhängigkeiten müssen Sie diese Abhängigkeiten im Voraus identifizieren und bereit sein, Sie manuell zu installieren.

## <a name="add-a-new-python-package"></a>Hinzufügen eines neuen python-Pakets

Bei diesem Beispiel wird davon ausgegangen, dass Sie ein neues Paket direkt auf dem SQL Server Computer installieren möchten.

Die Paketinstallation erfolgt pro Instanz. Wenn Sie über mehrere Instanzen von Machine Learning Services verfügen, müssen Sie das Paket jedem hinzufügen.

Das in diesem Beispiel installierte Paket ist [cntk](https://docs.microsoft.com/cognitive-toolkit/), ein Framework für Deep Learning von Microsoft, das die Anpassung, das Training und die Freigabe verschiedener Typen von neuronalen Netzwerken unterstützt.

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Schritt 1: Herunterladen der Windows-Version des python-Pakets

+ Wenn Sie Python-Pakete auf einem Server ohne Internet Zugriff installieren, müssen Sie die WHL-Datei auf einen anderen Computer herunterladen und dann auf den-Server kopieren.

    Beispielsweise können Sie auf einem separaten Computer die WHL-Datei von diesem Standort [https://cntk.ai/PythonWheel/CPU-Only](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl)herunterladen und die Datei `cntk-2.1-cp35-cp35m-win_amd64.whl` dann in einen lokalen Ordner auf dem SQL Server-Computer kopieren.

+ SQL Server 2017 verwendet python 3,5. 

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie die Windows-Version des Pakets erhalten. Wenn die Datei in. gz endet, ist Sie wahrscheinlich nicht die richtige Version.

Diese Seite enthält Downloads für mehrere Plattformen und für mehrere Python-Versionen: [Einrichten von cntk](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Schritt 2: Öffnen Sie eine python-Eingabeaufforderung.

Suchen Sie den von SQL Server verwendeten Standard Speicherort der Python-Bibliothek. Wenn Sie mehrere Instanzen installiert haben, suchen Sie den Ordner PYTHON_SERVICE für die Instanz, in der Sie das Paket hinzufügen möchten.

Wenn Machine Learning Services beispielsweise mit Standardeinstellungen installiert wurde und Machine Learning auf der Standard Instanz aktiviert ist, lautet der Pfad wie folgt:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Öffnen Sie die python-Eingabeaufforderung, die der-Instanz zugeordnet ist.

> [!TIP]
> Für das zukünftige Debuggen und testen empfiehlt es sich, eine python-Umgebung einzurichten, die für die instanzbibliothek spezifisch ist.

### <a name="step-3-install-the-package-using-pip"></a>Schritt 3: Installieren des Pakets mit PIP

+ Wenn Sie daran gewöhnt sind, die python-Befehlszeile zu verwenden, verwenden Sie PIP. exe, um neue Pakete zu installieren. Sie finden das **PIP** -Installationsprogramm im `Scripts` Unterordner. 

  SQL Server-Setup fügt dem Systempfad keine Skripts hinzu. Wenn Sie einen Fehler `pip` erhalten, der nicht als interner oder externer Befehl erkannt wird, können Sie den Ordner "Scripts" der PATH-Variablen in Windows hinzufügen.

  Der vollständige Pfad des Ordners " **Scripts** " in einer Standardinstallation lautet wie folgt:

    C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Wenn Sie Visual Studio 2017 oder Visual Studio 2015 mit den Python-Erweiterungen verwenden, können Sie im Fenster `pip install` python- **Umgebungen** ausführen. Klicken Sie auf **Pakete**, und geben Sie im Textfeld den Namen oder Speicherort des zu installierenden Pakets an. Sie müssen nicht eingeben `pip install`. es wird automatisch ausgefüllt. 

    - Wenn der Computer über Internet Zugriff verfügt, geben Sie den Namen des Pakets oder die URL eines bestimmten Pakets und einer bestimmten Version an. 
    
    Geben Sie z. b. die Download-URL an, um die Version von cntk zu installieren, die für Windows und Python 3,5 unterstützt wird:`https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Wenn der Computer nicht über Internet Zugriff verfügt, müssen Sie die WHL-Datei herunterladen, bevor Sie mit der Installation beginnen. Geben Sie dann den Pfad und den Namen der lokalen Datei an. Fügen Sie z. b. den folgenden Pfad und die Datei ein, um die von der Website heruntergeladene WHL-Datei zu installieren:`"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Möglicherweise werden Sie aufgefordert, Berechtigungen zum Abschluss der Installation zu erhöhen.

Im Verlauf der Installation können Sie Statusmeldungen im Eingabe Aufforderungs Fenster sehen:

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```


### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Schritt 4. Laden des Pakets oder seiner Funktionen als Teil Ihres Skripts

Wenn die Installation beendet ist, können Sie sofort mit der Verwendung des Pakets beginnen, wie im nächsten Schritt beschrieben.

Beispiele für Deep Learning mit cntk finden Sie in den folgenden Tutorials: [Python-API für cntk](https://cntk.ai/pythondocs/tutorials.html)

Wenn Sie Funktionen aus dem Paket in Ihrem Skript verwenden möchten, fügen `import <package_name>` Sie die Standard Anweisung in die ersten Zeilen des Skripts ein:

```python
import numpy as np
import cntk as cntk
cntk._version_
```

## <a name="list-installed-packages-using-conda"></a>Auflisten installierter Pakete mithilfe von "Configuration Manager"

Es gibt verschiedene Möglichkeiten, eine Liste der installierten Pakete zu erhalten. Beispielsweise können Sie die installierten Pakete im Fenster " **python-Umgebungen** " von Visual Studio anzeigen.

Wenn Sie die python-Befehlszeile verwenden, können Sie entweder **PIP** oder **den Paket-** Manager von Configuration Manager verwenden, der in der Anaconda python-Umgebung enthalten ist, die durch SQL Server-Setup hinzugefügt wurde.

1. Wechseln Sie zu "c:\Programme\Microsoft SQL server\mssql14.". MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Klicken Sie mit der rechten Maustaste auf die **Datei** > ""**als Administrator ausführen**, und geben `conda list` Sie ein, um eine Liste der in der aktuellen Umgebung installierten Pakete zurückzugeben.

1. Klicken Sie mit der rechten Maustaste auf **PIP. exe** > **als Administrator ausführen**, `pip list` und geben Sie ein, um die gleichen Informationen zurückzugeben. 

Weitere Informationen zu "Configuration Manager **" und deren** Verwendung zum Erstellen und Verwalten mehrerer python-Umgebungen finden Sie unter [Verwalten von Umgebungen mit](https://conda.io/docs/user-guide/tasks/manage-environments.html)einem anderen Konfigurations-Manager.

> [!Note]
> Wenn SQL Server-Setup dem Systempfad und einer Produktions SQL Server Instanz PIP oder das nicht hinzugefügt wird, empfiehlt es sich, nicht erforderliche ausführbare Dateien aus dem Pfad zu behalten. Für Entwicklungs-und Testumgebungen können Sie jedoch den Ordner "Scripts" der systempath-Umgebungsvariable hinzufügen, um den Befehl "Pip" und "Configuration on" an einem beliebigen Speicherort auszuführen.
