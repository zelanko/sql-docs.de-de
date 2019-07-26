---
title: Verwenden von R-Code-Profilerstellungsfunktionen
description: Verbessern Sie die Leistung, und erzielen Sie schnellere Ergebnisse für r-Berechnungen auf SQL Server, indem Sie mithilfe von r-Profil Erstellungs Funktionen Informationen zu internen Funktionsaufrufen zurück
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: a586a4f7656dd0319e3139e05ba1bea6c8d96abe
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469846"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Verwenden von R-Code-Profil Erstellungs Funktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Neben SQL Server-Ressourcen und Tools zum Überwachen von R-Skriptausführung können Sie auch Leistungstools von anderen R-Paketen verwenden, um weitere Informationen zu internen Funktionsaufrufen zu erhalten. 

> [!TIP]
> Dieser Artikel enthält grundlegende Ressourcen, die Ihnen den Einstieg erleichtern. Eine Anleitung für Experten finden Sie im Abschnitt zur *Leistung* in ["Advanced R" von Hadley Wickham](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Verwenden von RPROF

[*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) ist eine Funktion, die im Basispaket " [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1)" enthalten ist, das standardmäßig geladen wird. 

Im Allgemeinen schreibt die *rprof*-Funktion die Aufrufliste in bestimmten Intervallen in eine Datei. Sie können dann die [*summaryrprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) -Funktion verwenden, um die Ausgabedatei zu verarbeiten. Ein Vorteil von *rprof* ist, dass die Funktion Sampling durchführt und dadurch die Leistungsauslastung der Überwachung verringert wird.

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

Die Dokumentation für Microsoft R Open, die standardmäßig installiert wird, umfasst ein manuelles entwickeln von Erweiterungen für die Programmiersprache r, in der die [Profilerstellung und das Debuggen](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) ausführlich erläutert werden. Sie finden dieselbe Dokumentation auf Ihrem Computer unter "c:\Programme\Microsoft SQL server\mssql13.". MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>Siehe auch

+ [utils R-Paket](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ ["Advanced R" von Hadley Wickham](http://adv-r.had.co.nz)
