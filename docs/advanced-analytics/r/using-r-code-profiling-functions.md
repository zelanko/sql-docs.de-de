---
title: Verwenden von R-Code-Profilerstellungsfunktionen – SQL Server Machine Learning Services
description: Verbessern Sie der Leistung und erhalten Sie schnellere Ergebnisse auf R-Berechnungen in SQL Server mithilfe von R, die profilerstellung für Funktionen zum Zurückgeben von Informationen zu internen Funktionsaufrufen zu.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7bd54130ecb17241f0a5cddf4d80e186d7a8a427
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645024"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Verwenden von R-Code-Profilerstellungsfunktionen zur Verbesserung der Leistung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Neben SQL Server-Ressourcen und Tools zum Überwachen von R-Skriptausführung können Sie auch Leistungstools von anderen R-Paketen verwenden, um weitere Informationen zu internen Funktionsaufrufen zu erhalten. 

> [!TIP]
> Dieser Artikel enthält grundlegende Ressourcen, um Ihnen den Einstieg erleichtern. Für Anleitungen von Experten, empfehlen wir die *Leistung* im Abschnitt ["Advanced R" von Hadley Wickham](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Verwenden von RPROF

[*Rprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) ist eine Funktion, die im Basispaket enthalten [ **"utils"**](https://www.rdocumentation.org/packages/utils/versions/3.5.1), das standardmäßig geladen wird. 

Im Allgemeinen schreibt die *rprof*-Funktion die Aufrufliste in bestimmten Intervallen in eine Datei. Anschließend können Sie die [ *SummaryRprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) Funktion, um die Ausgabedatei zu verarbeiten. Ein Vorteil von *rprof* ist, dass die Funktion Sampling durchführt und dadurch die Leistungsauslastung der Überwachung verringert wird.

Zur Verwendung der R-Profilerstellung in Ihrem Code rufen Sie diese Funktion auf und geben ihre Parameter an, darunter auch den Namen des Speicherorts der Protokolldatei, die geschrieben wird. Die Profilerstellung kann im Code aktiviert oder deaktiviert werden. Die folgende Syntax zeigt die grundlegende Verwendung: 

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

Die Dokumentation für Microsoft R Open, die standardmäßig installiert ist, enthält ein Handbuch zum Entwickeln von Erweiterungen für die R-Sprache, die erläutert, [profilerstellung und Debuggen](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) im Detail. Die gleiche Dokumentation finden Sie auf Ihrem Computer C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>Siehe auch

+ ["utils"-R-Paket](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ ["Advanced R" von Hadley Wickham](http://adv-r.had.co.nz)
