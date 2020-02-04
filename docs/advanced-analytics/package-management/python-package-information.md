---
title: Abrufen von Paketinformationen für Python
description: Erfahren Sie, wie Sie Informationen zu installierten Python-Paketen, einschließlich Versionsnummern und Installationsspeicherorten, in SQL Server Machine Learning Services erhalten.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1aa12da4a138ea8f292fa8b64db00456d3c35fe3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "70000446"
---
# <a name="get-python-package-information"></a>Abrufen von Paketinformationen für Python

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel erfahren Sie, wie Sie Informationen zu installierten Python-Paketen, einschließlich Versionsnummern und Installationsspeicherorten, in SQL Server Machine Learning Services erhalten. Dabei wird anhand von Python-Beispielskripts veranschaulicht, wie Sie Paketinformationen, z. B. Installationspfad und Version, auflisten können.

## <a name="default-python-library-location"></a>Standardspeicherort der Python-Bibliothek

Wenn Sie Machine Learning-Funktionen mit SQL Server installieren, wird eine einzelne Paketbibliothek auf Instanzebene für jede von Ihnen installierte Sprache erstellt. Unter Windows ist die Instanzbibliothek ein gesicherter Ordner, der bei SQL Server registriert ist.

Alle Skripts oder Codes, die datenbankintern in SQL Server ausgeführt werden, müssen Funktionen aus der Instanzbibliothek laden. SQL Server kann nicht auf Pakete zugreifen, die in anderen Bibliotheken installiert sind. Dies gilt auch für Remoteclients: Jeder Python-Code, der im Servercomputekontext ausgeführt wird, kann nur Pakete verwenden, die in der Instanzbibliothek installiert sind.
Zum Schutz der Serverressourcen kann die Standardinstanzbibliothek nur von einem Computeradministrator geändert werden.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für Python lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für Python lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

Dabei wird von der standardmäßigen SQL-Instanz, MSSQLSERVER, ausgegangen. Wenn SQL Server als benutzerdefinierte benannte Instanz installiert wird, wird stattdessen der angegebene Name verwendet.

Führen Sie die folgende Anweisung aus, um die Standardbibliothek für die aktuelle Instanz zu überprüfen. In diesem Beispiel wird die Liste der in der Python-Variablen `sys.path` enthaltenen Ordner zurückgegeben. Die Liste enthält das aktuelle Verzeichnis und den Pfad der Standardbibliothek.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

Weitere Informationen zur Variablen `sys.path`, und wie sie zum Festlegen des Suchpfads für Module des Interpreters verwendet wird, finden Sie im Abschnitt zum [Suchpfad für das Modul](https://docs.python.org/2/tutorial/modules.html#the-module-search-path).

## <a name="default-python-packages"></a>Python-Standardpakete

Wenn Sie bei der Installation die Python-Funktion auswählen, werden die folgenden Python-Pakete mit SQL Server Machine Learning Services installiert.

| Pakete | Version |  BESCHREIBUNG |
| ---------|---------|--------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Wird für Remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Fügt Machine Learning-Algorithmen in Python hinzu. |

### <a name="component-upgrades"></a>Komponentenupgrades

Python-Pakete werden standardmäßig durch Service Packs und kumulative Updates aktualisiert. Zusätzliche Pakete und vollständige Versionsupgrades von Python-Kernkomponenten sind nur durch Produktupgrades oder durch Binden des Python-Supports an Microsoft Machine Learning Server möglich.

Weitere Informationen finden Sie unter [Upgrade R and Python components in SQL Server (Upgrade von R- und Python-Komponenten in SQL Server)](../install/upgrade-r-and-python.md).

## <a name="default-open-source-python-packages"></a>Open-Source-Standardpakete für Python

Wenn Sie während der Installation als Programmiersprache „Python“ auswählen, wird die Anaconda 4.2-Distribution (über Python 3.5) installiert. Zusätzlich zu den Python-Codebibliotheken umfasst die Standardinstallation Beispieldaten, Komponententests und Beispielskripts.

> [!IMPORTANT]
> Überschreiben Sie die vom SQL Server-Setup installierte Version von Python niemals manuell mit neueren, online verfügbaren Versionen. Python-Pakete von Microsoft basieren auf bestimmten Versionen von Anaconda. Die Änderung Ihrer Installation könnte diese instabil machen.

## <a name="list-all-installed-python-packages"></a>Auflisten aller installierten Python-Pakete

Das folgende Beispielskript zeigt eine Liste der installierten Pakete und deren Versionsnummern an.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
import pkg_resources
import pandas as pd
installed_packages = pkg_resources.working_set
installed_packages_list = sorted(["%s==%s" % (i.key, i.version) for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
  '
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

## <a name="find-a-single-python-package"></a>Suchen eines einzelnen Python-Pakets

Wenn Sie ein Python-Paket installiert haben und sicherstellen möchten, dass es für eine bestimmte SQL Server-Instanz verfügbar ist, können Sie eine gespeicherte Prozedur ausführen, um das Paket zu laden und Meldungen zurückzugeben.

Beispielsweise kann mit dem folgenden Code nach dem `scikit-learn`-Paket gesucht werden.
Wenn das Paket gefunden wurde, gibt der Code die Meldung „Package scikit-learn is installed“ (Das Paket scikit-learn ist installiert) zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import pkg_resources
pckg_name = "scikit-learn"
pckgs = pandas.DataFrame([(i.key) for i in pkg_resources.working_set], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
  '
```

<a name="get-package-vers"></a>

Im folgenden Beispiel werden die Versionsnummern des revoscalepy-Pakets und von Python zurückgegeben.

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import revoscalepy
import sys
print(revoscalepy.__version__)
print(sys.version)
  '
```

## <a name="next-steps"></a>Nächste Schritte

+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Abrufen von R-Paketinformationen](r-package-information.md)
+ [Neue R-Pakete installieren](../r/install-additional-r-packages-on-sql-server.md)
+ [R- und Python-Tutorials](../tutorials/machine-learning-services-tutorials.md)
