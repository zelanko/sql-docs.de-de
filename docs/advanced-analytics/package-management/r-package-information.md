---
title: R-Paketinformationen erhalten
description: Erfahren Sie, wie Sie Informationen zu installierten R-Paketen auf SQL Server Machine Learning Services und SQL Server R Services erhalten.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 8c3cf3c1debc03c169c585521b8b46dd8b1365c5
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69641157"
---
# <a name="get-r-package-information"></a>R-Paketinformationen erhalten

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Informationen zu installierten R-Paketen auf SQL Server Machine Learning Services und SQL Server R Services erhalten. Beispiel-R-Skripts veranschaulichen, wie Sie Paketinformationen wie den Installationspfad und die Version auflisten.

## <a name="default-r-library-location"></a>Standard Speicherort der R-Bibliothek

Wenn Sie Machine Learning mit SQL Server installieren, wird eine einzelne paketbibliothek auf Instanzebene für jede von Ihnen installierte Sprache erstellt. Unter Windows ist die instanzbibliothek ein sicherer Ordner, der bei SQL Server registriert ist.

Alle Skripts, die in der-Datenbank auf SQL Server ausgeführt werden, müssen Funktionen aus der-instanzbibliothek laden. SQL Server kann nicht auf Pakete zugreifen, die in anderen Bibliotheken installiert sind. Dies gilt auch für Remote Clients: bei allen R-Skripts, die im Server-computekontext ausgeführt werden, können nur in der instanzbibliothek installierte Pakete verwendet werden.
Die standardinstanzbibliothek kann nur von einem Computer Administrator geändert werden, um Server Objekte zu schützen.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für R lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für R lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für R lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

Dabei wird die standardmäßige SQL-Instanz, MSSQLSERVER, vorausgesetzt. Wenn SQL Server als benutzerdefinierte benannte Instanz installiert wird, wird stattdessen der angegebene Name verwendet.

<!-- I don't think this note is necessary. If you have these other products installed, you'd already know about them.
> [!NOTE]
> If you find other folders having similar subfolder names and files, you probably have a standalone installation of  Microsoft R Server or Machine Learning Server. These server products have different installers and paths: C:\Program Files\Microsoft\R Server\R_SERVER or C:\Program Files\Microsoft\ML SERVER\R_SERVER. For more information, see [Install R Server 9.1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) or [Install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).
-->

Führen Sie die folgende Anweisung aus, um die Standard-R-paketbibliothek für die aktuelle Instanz zu überprüfen:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

In der folgenden Anweisung werden [rxsqllibpath](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) verwendet, um den Pfad der instanzbibliothek und die von SQL Server verwendete Version von revoscaler zurückzugeben:

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
> Die [rxsqllibpath](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) -Funktion kann nur auf dem lokalen Computer ausgeführt werden. Die Funktion kann keine Bibliothekspfade für Remote Verbindungen zurückgeben.

## <a name="default-r-packages"></a>Standard-R-Pakete

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

Die folgenden R-Pakete werden mit SQL Server R Services installiert.

|Pakete | Version | Beschreibung |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | Wird für remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und-Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | Wird zum Einschließen von R-Skripts in gespeicherte Prozeduren verwendet |

::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"

Die folgenden r-Pakete werden mit SQL Server Machine Learning Services installiert, wenn Sie die r-Funktion während des Setups auswählen.

|Pakete | Version | Beschreibung |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 9,2 | Wird für remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und-Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 9,2 | Wird zum Einschließen von R-Skripts in gespeicherte Prozeduren verwendet |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| 9,2 | Fügt Machine Learning-Algorithmen in R hinzu. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 9,2 | Wird zum Schreiben von MDX-Anweisungen in R verwendet. |

::: moniker-end

### <a name="component-upgrades"></a>Komponenten Upgrades

R-Pakete werden standardmäßig durch Service Packs und kumulative Updates aktualisiert. Zusätzliche Pakete und vollständige Versions Upgrades von Kern-R-Komponenten sind nur durch Produkt Upgrades oder durch die Bindung von R-Unterstützung an Microsoft Machine Learning Server möglich.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Außerdem können Sie microsoftml-und olapr-Pakete über ein Komponenten Upgrade zu einer SQL Server-Instanz hinzufügen.
::: moniker-end

Weitere Informationen finden Sie unter [Aktualisieren von R-und python-Komponenten in SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-r-packages"></a>Standard-Open-Source-R-Pakete

Die R-Unterstützung umfasst Open Source-Funktionen, sodass Sie grundlegende R-Funktionen aufzurufen und zusätzliche Open Source-und Drittanbieter Pakete installieren können. Die Unterstützung von R-Sprachen umfasst Kernfunktionen wie **Base**, **Stats**, **utils**und andere. Eine Basisinstallation von r umfasst auch zahlreiche Beispiel Datasets und r-Standard Tools, wie z. **b. rgui** (ein interaktiver interaktiver Editor) und **RTERM** (eine R-Eingabeaufforderung).

Die Verteilung von Open Source-R in Ihrer Installation ist [Microsoft R Open (MRO)](https://mran.microsoft.com/open). MRO fügt der Basis-R einen Wert hinzu, indem weitere Open Source-Pakete wie die [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library)eingeschlossen werden.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Die Version von R, die von MRO mithilfe SQL Server R Services Setup bereitgestellt wird, ist 3.2.2.
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Die Version von R, die von MRO mithilfe von SQL Server Machine Learning Services-Setup bereitgestellt wird, ist 3.3.3.
::: moniker-end

> [!IMPORTANT]
> Sie sollten die installierte Version von R nie manuell überschreiben, indem Sie SQL Server-Setup mit neueren Versionen im Web. Microsoft r-Pakete basieren auf bestimmten Versionen von R. durch eine Änderung Ihrer Installation kann die Anwendung destabilisiert werden.

## <a name="list-all-installed-r-packages"></a>Auflisten aller installierten R-Pakete

Im folgenden Beispiel wird die r- `installed.packages()` Funktion in [!INCLUDE[tsql](../../includes/tsql-md.md)] einer gespeicherten Prozedur verwendet, um eine Liste der r-Pakete anzuzeigen, die in der R_SERVICES-Bibliothek für die aktuelle SQL-Instanz installiert wurden. Dieses Skript gibt die Felder Paketname und Version in der Beschreibungsdatei zurück.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);',
@input_data_1 = N'
  '
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Weitere Informationen zu den optionalen Feldern und den Standard Feldern für das Feld "R Package Description [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)" finden Sie unter.

## <a name="find-a-single-r-package"></a>Suchen eines einzelnen R-Pakets

Wenn Sie ein R-Paket installiert haben und sicherstellen möchten, dass es für eine bestimmte SQL Server Instanz verfügbar ist, können Sie eine gespeicherte Prozedur ausführen, um das Paket zu laden und Nachrichten zurückzugeben.

Beispielsweise wird mit der folgenden Anweisung das [glue](https://cran.r-project.org/web/packages/glue/)-Paket gesucht und geladen, sofern es verfügbar ist.
Wenn das Paket nicht gefunden oder geladen werden kann, erhalten Sie eine Fehlermeldung mit dem Text "Es ist kein Paket mit dem Namen" Klebstoff "vorhanden.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("glue")'
GO
```

Weitere Informationen zum Paket `packageDescription`finden Sie unter.
Die folgende Anweisung gibt Informationen für das **glue**-Installationspaket zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("glue"))
  '
```

## <a name="next-steps"></a>Nächste Schritte

+ [Neue R-Pakete installieren](../r/install-additional-r-packages-on-sql-server.md)
+ [Informationen zum Python-Paket erhalten](python-package-information.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials zu R und python](../tutorials/machine-learning-services-tutorials.md)
