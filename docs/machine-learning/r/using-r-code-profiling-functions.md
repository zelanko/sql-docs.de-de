---
title: Verbessern der Leistung durch Verwenden von R-Code-Profilerstellungsfunktionen
description: Sammeln Sie hilfreiche Informationen zum Verbessern der Leistung und zum Erzielen schnellerer Ergebnisse für R-Berechnungen unter SQL Server mithilfe von R-Profilerstellungsfunktionen. Die *rprof*-Funktion sammelt Informationen zu internen Funktionsaufrufen und gibt diese zurück.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 12/12/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 16a1ed8df29de58450f87118068e43646c46fd90
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86484638"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Verwenden von R-Code-Profilerstellungsfunktionen
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Neben SQL Server-Ressourcen und Tools zum Überwachen von R-Skriptausführung können Sie auch Leistungstools von anderen R-Paketen verwenden, um weitere Informationen zu internen Funktionsaufrufen zu erhalten. 

> [!TIP]
> Dieser Artikel enthält grundlegende Ressourcen, die Ihnen den Einstieg erleichtern. Als Anleitung wird der Abschnitt *Performance* in [„Advanced R“ von Hadley Wickham](http://adv-r.had.co.nz) empfohlen.

## <a name="using-rprof"></a>Verwenden von RPROF

Die [*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof)-Funktion ist im Basispaket [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1) enthalten, das standardmäßig geladen wird. 

Im Allgemeinen schreibt die *rprof*-Funktion die Aufrufliste in bestimmten Intervallen in eine Datei. Anschließend können Sie die [*summaryRprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof)-Funktion verwenden, um die Ausgabedatei zu verarbeiten. Ein Vorteil von *rprof* ist, dass die Funktion Sampling durchführt und dadurch die Leistungsauslastung der Überwachung verringert wird.

Zur Verwendung der R-Profilerstellung in Ihrem Code rufen Sie diese Funktion auf und geben ihre Parameter an, darunter auch den Namen des Speicherorts der Protokolldatei, die geschrieben wird. Die Profilerstellung kann im Code aktiviert oder deaktiviert werden. Die folgende Syntax veranschaulicht die grundlegende Verwendung: 

```R
# Specify profiling output file.
varOutputFile <- "C:/TEMP/run001.log")
Rprof(varOutputFile)

# Turn off profiling
Rprof(NULL)
    
# Restart profiling
Rprof(append=TRUE)
```

> [!NOTE]
> Für die Verwendung dieser Funktion ist es erforderlich, dass Windows Perl auf dem Computer installiert ist, auf dem der Code ausgeführt wird. Deshalb wird empfohlen, dass Sie Code während der Entwicklung in einer R-Umgebung erstellen und dann den gedebuggten Code an SQL Server bereitstellen.  


## <a name="r-system-functions"></a>R-Systemfunktionen

Die R-Sprache umfasst viele Basispaketfunktionen für die Rückgabe des Inhalts von Systemvariablen. Als Teil des R-Codes können Sie zum Beispiel `Sys.timezone` zum Abrufen der aktuellen Zeitzone oder `Sys.Time` zum Abrufen der Systemzeit von R verwenden. 

Informationen zu einzelnen R-Systemfunktionen können Sie erhalten, indem Sie den Namen der Funktion als Argument für die R-`help()`-Funktion von einer R-Eingabeaufforderung aus eingeben.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Debuggen und Profilerstellung in R

Die Dokumentation für Microsoft R Open, die standardmäßig installiert ist, enthält ein Handbuch zum Entwickeln von Erweiterungen für die R-Sprache, in dem [Profilerstellung und Debuggen](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) im Detail erläutert werden. Sie finden dieselbe Dokumentation auf Ihrem Computer im Verzeichnis C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>Weitere Informationen

+ [utils R-Paket](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [„Advanced R“ von Hadley Wickham](http://adv-r.had.co.nz)
