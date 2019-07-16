---
title: Installieren Sie neuer Python-Sprachpakete – SQL Server-Machine Learning
description: Neue Python-Paketen zu SQL Server 2017-Machine Learning Services (Datenbankintern) und Machine Learning Server (eigenständig) hinzufügen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/16/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f30c00503a0dd183619550d3ab0e92c0be1449dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962774"
---
# <a name="install-new-python-packages-on-sql-server"></a>Installieren Sie neuer Python-Pakete unter SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie zum Installieren neuer Python-Pakete auf einer Instanz von SQL Server 2017-Machine Learning Services wird. Im Allgemeinen ähnelt der Prozess zum Installieren neuer Pakete, die in einer Python-standardumgebung. Allerdings sind einige zusätzliche Schritte erforderlich, wenn der Server nicht über eine Internetverbindung verfügt.

Weitere Informationen zu Paket-Speicherort und die Installation Pfaden finden Sie unter [erhalten R- oder Python-Paketinformationen](../package-management/installed-package-information.md).

## <a name="prerequisites"></a>Vorraussetzungen

+ [SQL Server 2017-Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md) mit der Python-Sprache-Option. 

+ Pakete müssen Python 3.5-kompatibel, und führen auf Windows sein. 

+ Administratorzugriff auf dem Server ist erforderlich, um Pakete zu installieren.

## <a name="considerations"></a>Weitere Überlegungen

Hinzufügen von Paketen, berücksichtigen Sie, ob das Paket für SQL Server-Umgebung geeignet ist. Ein Datenbankserver ist in der Regel eine freigegebene Ressource, sodass mehrere arbeitsauslastungen. Wenn Sie Pakete hinzufügen, die zu viel rechenleistung Druck auf dem Server gestellt wird, wird die Leistung beeinträchtigt werden. 

Darüber hinaus ausführen einige beliebte Python-Pakete (z. B. Flask) Aufgaben, z. B. Webentwicklung, die besser für eine eigenständige Umgebung geeignet sind. Es wird empfohlen, dass Sie in der Datenbank Python für Aufgaben, die eine enge Integration profitieren, mit der Datenbank-Engine, wie Machine Learning anstelle von Aufgaben, die die Datenbank einfach Abfragen verwenden.

Datenbankserver sind häufig gesperrt. In vielen Fällen wird der Zugriff auf das Internet vollständig blockiert. Für Pakete mit einer langen Liste von Abhängigkeiten müssen Sie diese Abhängigkeiten im Voraus zu identifizieren und werden jeweils manuell zu installieren.

## <a name="add-a-new-python-package"></a>Hinzufügen eines neuen Python-Pakets

In diesem Beispiel wird davon ausgegangen, dass Sie ein neues Paket direkt auf dem SQL Server-Computer installieren möchten.

Paketinstallation wird pro Instanz. Wenn Sie mehrere Instanzen von Machine Learning-Dienste verfügen, müssen Sie das Paket jeder hinzufügen.

Das Paket installiert, die in diesem Beispiel wird [CNTK](https://docs.microsoft.com/cognitive-toolkit/), ein Framework für deep Learning von Microsoft, die Anpassung unterstützt Trainings- und Freigabe von verschiedenen Typen von neuronalen Netzwerken.

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Schritt 1: Laden Sie die Windows-Version des Python-Pakets

+ Wenn Sie Python-Pakete auf einem Server ohne Internetzugang installieren, müssen Sie die WHL-Datei auf einen anderen Computer herunterladen und klicken Sie dann auf den Server kopieren.

    Z. B. auf einem separaten Computer, Sie können die WHL-Datei von diesem Standort [ https://cntk.ai/PythonWheel/CPU-Only ](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), und klicken Sie dann kopieren Sie die Datei `cntk-2.1-cp35-cp35m-win_amd64.whl` in einen lokalen Ordner auf dem SQL Server-Computer.

+ SQL Server 2017 wird Python 3.5 verwendet. 

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie die Windows-Version des Pakets zu erhalten. Wenn die Datei im GZ endet, ist es wahrscheinlich nicht die richtige Version.

Diese Seite enthält Downloads für mehrere Plattformen und für mehrere Python-Versionen: [Einrichten von CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Schritt 2: Öffnen Sie eine Python-Eingabeaufforderung

Suchen Sie die Python-Bibliothek am Standardspeicherort von SQL Server verwendet. Wenn Sie mehrere Instanzen installiert haben, suchen Sie den PYTHON_SERVICE-Ordner, für die Instanz, in dem Sie das Paket hinzufügen möchten.

Beispielsweise, wenn beispielsweise Machine Learning-Dienste mit Standardeinstellungen installiert wurde, und Machine Learning für die Standardinstanz aktiviert ist, der Pfad wie folgt lauten:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Öffnen Sie die Python-Eingabeaufforderung, die mit der Instanz verknüpft ist.

> [!TIP]
> Für zukünftige Debuggen und testen, empfiehlt es sich zum Einrichten einer Python-Umgebung für die Instanz-Bibliothek.

### <a name="step-3-install-the-package-using-pip"></a>Schritt 3: Installieren Sie das Paket mithilfe von pip

+ Wenn Sie zur Verwendung von Python-Befehlszeile vertraut sind, verwenden Sie PIP.exe, um neue Pakete zu installieren. Sie finden die **Pip** Installers in der `Scripts` Unterordner. 

  SQL Server-Setup wird keine Skripts zum Systempfad hinzufügen. Wenn Sie eine Fehlermeldung, die erhalten `pip` wird nicht erkannt als interner oder externer Befehl, können Sie den Ordner "Scripts" der PATH-Variablen in Windows hinzufügen.

  Den vollständigen Pfad der **Skripts** Ordner in einer Standardinstallation lautet wie folgt:

    C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Wenn Sie Visual Studio 2017 oder Visual Studio 2015 mit den Python-Erweiterungen verwenden, können Sie ausführen `pip install` aus der **Python-Umgebungen** Fenster. Klicken Sie auf **Pakete**, und geben Sie im Textfeld den Namen oder Speicherort der zu installierenden Pakets an. Sie müssen nicht geben `pip install`; es wird für Sie automatisch ausgefüllt. 

    - Wenn der Computer über Internetzugriff verfügt, geben Sie den Namen des Pakets oder die URL der ein bestimmtes Paket und eine Version aus. 
    
    Um die Version von CNTK zu installieren, die für Windows und Python 3.5 unterstützt wird, geben Sie z. B. die Download-URL: `https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Wenn der Computer nicht über Internetzugriff verfügt, müssen Sie die WHL-Datei herunterladen, vor der Installation. Geben Sie dann den lokalen Pfad und den Namen ein. Fügen Sie beispielsweise den folgenden Pfad und die Datei zum Installieren der WHL-Datei, die von der Website heruntergeladen werden: `"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Möglicherweise werden Sie aufgefordert, Berechtigungen zum Abschließen der Installation zu erhöhen.

Im Lauf der Installation können Sie statusmeldungen im Eingabeaufforderungsfenster Befehl sehen:

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```


### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Schritt 4. Laden Sie das Paket oder die Funktionen als Teil des Skripts

Wenn die Installation abgeschlossen ist, können Sie sofort beginnen, mithilfe des Pakets, wie im nächsten Schritt beschrieben.

Beispiele für deep Learning mit CNTK finden Sie in diesen Tutorials: [Python-API für CNTK](https://cntk.ai/pythondocs/tutorials.html)

Um Funktionen aus dem Paket in Ihrem Skript verwenden, fügen Sie den Standard `import <package_name>` -Anweisung in der ersten Zeilen des Skripts:

```python
import numpy as np
import cntk as cntk
cntk._version_
```

## <a name="list-installed-packages-using-conda"></a>Liste der installierten Pakete mithilfe von conda

Es gibt verschiedene Möglichkeiten, die Sie eine Liste der installierten Pakete abrufen können. Beispielsweise sehen Sie die installierten Pakete in der **Python-Umgebungen** Windows von Visual Studio.

Wenn Sie die Python-Befehlszeile verwenden, können Sie entweder **Pip** oder **Conda** -Paket-Manager enthalten, mit der Anaconda-Python-Umgebung, die von SQL Server-Setup hinzugefügt.

1. Wechseln Sie zu C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Mit der rechten Maustaste **conda.exe** > **als Administrator ausführen**, und geben Sie `conda list` um eine Liste der in der aktuellen Umgebung installierte Pakete zurückzugeben.

1. Auf ähnliche Weise mit der rechten Maustaste **pip.exe** > **als Administrator ausführen**, und geben Sie `pip list` die gleiche Informationen zurückgegeben werden sollen. 

Weitere Informationen zu **Conda** und ihrer Verwendung können sie zum Erstellen und Verwalten mehrerer Python-Umgebungen finden Sie unter [Verwaltung von Umgebungen mit Conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).

> [!Note]
> SQL Server-Setup wird nicht hinzugefügt werden, dass Pip oder Conda zum Systempfad und auf einer Produktionsinstanz von SQL Server, halten die vermeidbare ausführbaren Dateien aus dem Pfad eine bewährte Methode ist. Allerdings können für Entwicklungs- und testumgebungen, Sie Ordner "Scripts" der PATH-Systemumgebungsvariablen Pip und Conda auf Befehl von einem beliebigen Standort ausführen hinzufügen.
