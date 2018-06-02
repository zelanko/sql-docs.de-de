---
title: Abrufen von Informationen von R und Python-Paket für SQL Server-Machine Learning | Microsoft Docs
description: R und Python-Paketversion ermitteln, überprüfen Sie die Installation und eine Liste der installierten Pakete auf SQL Server R Services "oder" Machine Learning Services abzurufen.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 85ea4658ca8b60fc24d7e4f7849de1655eab6082
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707888"
---
#  <a name="get-r-and-python-package-information"></a>Abrufen von Informationen für R und Python-Paket
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Auch müssen wenn Sie mit mehreren Umgebungen oder Installationen von R oder Python arbeiten, Sie sicherstellen, dass der Code, den Sie ausführen, die erwartete Umgebung für Python oder den Arbeitsbereich "richtige" für r verwendet wird Upgrade von Machine learning-Komponenten über beispielsweise [Bindung](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md), möglicherweise der Pfad zum R-Bibliothek in einem anderen Ordner als den Standardwert. Wenn Sie R-Client oder eine Instanz des eigenständigen Servers installieren, müssen Sie außerdem möglicherweise mehrere R-Bibliotheken auf Ihrem Computer.

R und Python-Skript-Beispiele in diesem Artikel veranschaulichen das Abrufen der Pfad und die Version von Paketen, die von SQL Server verwendet.

## <a name="get-the-r-library-location"></a>Abrufen des Standorts der R-Bibliothek

Für alle Versionen von SQL Server, führen Sie die folgende Anweisung zum Überprüfen der [Standardbibliothek R-Paket](installing-and-managing-r-packages.md) für die aktuelle Instanz:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Optional können Sie [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) in neueren Versionen von "revoscaler" in SQL Server 2017 Machine Learning Services oder [R Services aktualisierten R auf mindestens "revoscaler" 9.0.1](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Diese gespeicherte Prozedur gibt den Pfad der Instanz-Bibliothek und die Version von "revoscaler" von SQL Server verwendet:

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Die [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) Funktion kann nur auf dem lokalen Computer ausgeführt werden. Die Funktion kann nicht für Remoteverbindungen Bibliothekspfade zurück.

**Ergebnisse**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Abrufen des Standorts der Python-Bibliothek

Für **Python** in SQL Server-2017, führen Sie die folgende Anweisung aus, um zu überprüfen, ob die Standardbibliothek für die aktuelle Instanz. In diesem Beispiel gibt die Liste der Ordner für die Python `sys.path` Variable. Die Liste enthält das aktuelle Verzeichnis und den Pfad der Standardbibliothek.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Ergebnisse**

```text
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Weitere Informationen zu den Variablen `sys.path` und wie sie zum Festlegen der Interpreter Suchpfad für Module verwendet wird, finden Sie unter der [Python-Dokumentation](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>Liste aller Pakete

Es gibt mehrere Möglichkeiten, die Sie eine vollständige Liste der installierten Pakete abrufen können. Ein Vorteil der ausgeführten Paket List-Befehle aus Sp_execute_external_script ist, dass Sie sichergestellt, dass werden Pakete, die in der Bibliothek für die Instanz installiert.

### <a name="r"></a>R

Im folgenden Beispiel wird die R-Funktion `installed.packages()` in einem [!INCLUDE [tsql](..\..\includes\tsql-md.md)] gespeicherte Prozedur, eine Matrix aus Paketen abzurufen, die in der Bibliothek R_SERVICES für die aktuelle Instanz installiert wurden. Dieses Skript paketfelder aus Name und Version in der DESCRIPTION-Datei zurückgibt, wird nur der Name zurückgegeben.

```SQL
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Weitere Informationen zu den optionalen und Standardfelder für das Beschreibungsfeld der R-Paket finden Sie unter [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

Die `pip` Modul wird standardmäßig installiert, und unterstützt viele Vorgänge zum Auflisten installiert Pakete, zusätzlich zu den vom standard Python unterstützt. Sie können ausführen `pip` aus einem Python Eingabeaufforderung natürlich, aber Sie können auch einige Pip-Funktionen aufrufen von `sp_execute_external_script`.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
  import pip
  import pandas as pd
  installed_packages = pip.get_installed_distributions()
  installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
  df = pd.DataFrame(installed_packages_list)
  OutputDataSet = df'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

Beim Ausführen `pip` über die Befehlszeile stehen viele weitere Funktionen: `pip list` Ruft alle Pakete, die installiert werden, wohingegen `pip freeze` Listet die Pakete installiert, indem Sie `pip`, und nicht auflisten von Paketen, die selbst pip hängt ab. Sie können auch `pip freeze` um eine Abhängigkeitsdatei zu generieren.

## <a name="find-a-single-package"></a>Suchen eines einzelnen Pakets

Wenn Sie ein Paket installiert haben und möchten sicherstellen, dass er für eine bestimmte SQL Server-Instanz verfügbar ist, können Sie durch Ausführen der folgenden Aufruf der gespeicherten Prozedur, laden Sie das Paket und nur Nachrichten zurück.

### <a name="r"></a>R

In diesem Beispiel sucht und lädt die Bibliothek "revoscaler" aus, falls verfügbar.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Wenn das Paket gefunden wird, wird eine Meldung zurückgegeben: "Befehle wurde erfolgreich abgeschlossen."

+ Wenn das Paket gespeichert oder geladen werden kann, erhalten Sie eine Fehlermeldung, die mit dem Text: "ist kein Paket namens"MissingPackageName""

### <a name="python"></a>Python

Das entsprechende Kontrollkästchen für Python ausgeführt werden kann, aus der Python-shell, mit `conda` oder `pip` Befehle. Führen Sie stattdessen diese Anweisung in einer gespeicherten Prozedur an:

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
  import pip
  import pkg_resources
  pckg_name = "revoscalepy"
  pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
  installed_pckg = pckgs.query(''key == @pckg_name'')
  print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

## <a name="get-package-information-in-r-and-python-tools"></a>Abrufen von Paketinformationen in R und Python-tools

Allen vorherigen Anweisungen wird davon ausgegangen, dass Sie eine SQL Server-Tool wie Management Studio (SSMS) verwenden. Wenn Sie mithilfe von R und Python-Tools lieber, erläutert in den folgenden Anweisungen und Informationen über eine Befehlszeile R oder Python zu erhalten.

### <a name="r-commands"></a>R-Befehle

Die Instanz-Bibliothek für R ist \Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library.

Starten Sie den standard-R-Tools von diesen Speicherorten aus, um sicherzustellen, dass Pakete aus der Bibliothek Instanz verwendet werden:

+ \MSSQL14. MSSQLSERVER\R_SERVICES\bin\R.exe für eine R-Eingabeaufforderung
+ \MSSQL14. MSSQLSERVER\R_SERVICES\bin\x64\Rgui.exe für ein R-Konsolen-app

Sie können R-Standardbefehle oder "revoscaler"-Befehle verwenden, Paketinformationen abgerufen. Die RevoScaleR-Paket wird automatisch geladen. 

Rückgabeinformationen Sie RevoScaleR-Paket:

    > print(Revo.version)

Eine Liste aller installierten Pakete zurück:

    > installed.packages()

Die Version von r zurückgegeben

    > packageDescription("base")

### <a name="python-commands"></a>Python-Befehle

Unterstützung der Python ist nur in SQL Server-2017. Die Instanz-Bibliothek für Python ist \Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\.

Öffnen Sie die Python-Befehlsfenster, von diesem Speicherort aus, um sicherzustellen, dass Pakete aus der Bibliothek Instanz verwendet werden:

+ \MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Python.exe

Öffnen Sie die interaktive Hilfe:

    > help()

Geben Sie einen Modulnamen ein Hilfe zum Abrufen der Paketinhalt, Version und Dateispeicherort:

    help> revoscalepy

<a name="pip-conda"></a>

### <a name="python-package-managers-pip-and-conda"></a>Python Paket-Manager (Pip und Conda)

Anaconda enthält Python-Tools zum Verwalten von Paketen. In einer standardmäßigen werden Instanz, Pip Conda und anderen Tools im Ordner \Programme\Microsoft SQL Server\MSSQL14 gefunden. MSSQLSERVER\PYTHON_SERVICES\Scripts.

SQL Server-Setup ist nicht hinzugefügt werden, dass Pip oder Conda zum Systempfad und auf einer Produktionsinstanz von SQL Server beibehalten unbedeutende ausführbaren Dateien aus dem Pfad eine bewährte Methode ist. Allerdings können für Entwicklungs- und testumgebungen, Sie den Ordner "Skripts" System PATH-Umgebungsvariable Pip und Conda auf Befehl von jedem Standort ausgeführt hinzufügen.

1. Wechseln Sie zu C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Mit der rechten Maustaste **conda.exe** > **als Administrator ausführen**, und geben Sie `conda list` zurückzugebenden eine Liste der Pakete, die in der aktuellen Umgebung installiert.

1. Auf ähnliche Weise mit der rechten Maustaste **pip.exe** > **als Administrator ausführen**, und geben Sie `pip list` auf die gleichen Informationen zurückzugeben. 


## <a name="next-steps"></a>Nächste Schritte

+ [Neue R-Pakete installieren](install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)