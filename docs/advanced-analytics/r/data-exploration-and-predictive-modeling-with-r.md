---
title: Durchsuchen von Daten und Vorhersage Modellierung mit R
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: ecf9015fcb8f28a37343267d32f8e63aeb667e38
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345647"
---
# <a name="data-exploration-and-predictive-modeling-with-r-in-sql-server"></a>Durchsuchen von Daten und Vorhersage Modellierung mit R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel werden die Verbesserungen des Data Science Prozesses beschrieben, die durch die Integration in SQL Server möglich sind.

Betrifft: SQL Server 2016 R Services, SQL Server 2017 Machine learnign Services

## <a name="the-data-science-process"></a>Der Data Science-Prozess

Datenanalysten verwenden R häufig zum Durchsuchen von Daten und Erstellen von Vorhersagemodellen. Dies ist normalerweise ein iterativer Prozess durch Ausprobieren, bis ein geeignetes Vorhersagemodell erreicht wird. Als erfahrener Datenanalyst können Sie eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herstellen und die Daten mithilfe des RODBC-Pakets auf die lokale Arbeitsstation abrufen. Dort können Sie die Daten untersuchen und mithilfe von R-Standardpaketen ein Vorhersagemodell erstellen.

Dieser Ansatz hat jedoch viele Nachteile, die die breitere Übernahme von R im Unternehmen behindern. 

+ Daten Verschiebungen können langsam, ineffizient oder unsicher sein.
+ R selbst hat Einschränkungen hinsichtlich Leistung und Skalierung.

Diese Nachteile werden deutlicher, wenn Sie große Datenmengen verschieben und analysieren müssen, oder Datasets verwenden, die nicht in den auf Ihrem Computer verfügbaren Arbeitsspeicher passen.

Die neuen, skalierbaren Pakete und R-Funktionen [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , die in enthalten sind, helfen Ihnen, viele dieser Herausforderungen zu meistern 

## <a name="whats-different-about-revoscaler"></a>Was unterscheidet sich von revoscaler?

Das **RevoScaleR** -Paket enthält die Implementierung einiger der beliebtesten R-Funktionen, die umgestaltet wurden, um die Parallelität und Skalierung bereitzustellen. Weitere Informationen finden Sie unter [verteiltes Computing mithilfe von revoscaler](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).

Das RevoScaleR-Paket bietet auch Unterstützung zum Ändern des *Ausführungskontexts*. Dies bedeutet, dass für eine gesamte Lösung oder für eine einzelne Funktion, die Sie angeben können, die Berechnungen mithilfe der Ressourcen des Computers ausgeführt werden sollen, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hostet, und nicht auf der lokalen Arbeitsstation. Dies hat mehrere Vorteile: Sie vermeiden unnötige Datenbewegungen und Sie können auf dem Server ergiebigere Berechnungsressourcen nutzen.

## <a name="r-environment-and-packages"></a>R-Umgebung und -Pakete

Der in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] unterstützte R-Umgebung besteht aus einer Runtime-Engine, der Open Source-Sprache und einer grafischen Engine, die von mehreren Paketen unterstützt und erweitert wird. Die Sprache ermöglicht eine Vielzahl von Erweiterungen, die mithilfe der Pakete implementiert werden.  

### <a name="using-other-r-packages"></a>Verwenden anderer R-Pakete

Zusätzlich zu den proprietären r-Bibliotheken, die in Microsoft Machine Learning enthalten sind, können Sie fast alle R-Pakete in der Lösung verwenden, einschließlich:

+ Allgemeine R-Pakete aus öffentlichen Repositorys. Sie finden die beliebtesten Open Source-R-Pakete in öffentlichen Repositorys wie CRAN, wo über 6.000 Pakete gehostet werden, die von Datenanalysten verwendet werden können.
  
  Für die Windows-Plattform werden R-Pakete als ZIP-Dateien bereitgestellt, die unter der GPL-Lizenz heruntergeladen und installiert werden können.  
  
  Weitere Informationen zum Installieren der Pakete von Drittanbietern für die Verwendung mit [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]finden Sie unter [Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
  
+ Zusätzliche von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]bereitgestellte Pakete und Bibliotheken.   
  
     Das **RevoScaleR**-Paket enthält leistungsstarke Big Data-Analysen, verbesserte Versionen von Funktionen, die allgemeine Data Science-Aufgaben unterstützen, optimierte Lernmodule für Naive Bayes, lineare Regression, Zeitreihenmodelle, neuronale Netzwerke und erweiterte mathematische Bibliotheken.  
  
     Mit dem **RevoPemaR** -Paket können Sie eigene parallele, externe Speicheralgorithmen in R entwickeln.  
  
     Weitere Informationen zu diesen Paketen und deren Verwendung finden Sie unter [Was ist revoscaler](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) , und [beginnen Sie mit revopemar](https://docs.microsoft.com/machine-learning-server/r/how-to-developer-pemar). 

+ **Microsoftml** enthält eine Sammlung hochoptimierter Algorithmen für Maschinelles Lernen und Daten Transformationen des Microsoft Data Science-Teams. Viele der Algorithmen werden auch in Azure Machine Learning verwendet. Weitere Informationen finden Sie unter [microsoftml in SQL Server](ref-r-microsoftml.md).

### <a name="r-development-tools"></a>R-Entwicklungstools

Wenn Sie Ihre R-Lösung entwickeln, stellen Sie sicher, dass Sie Microsoft R Client herunterladen. Dieser kostenlose Download umfasst die Bibliotheken, die zur Unterstützung von remotecomputekontexten und skalierbaren alorithms benötigt werden:

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Eine Verteilung der r-Laufzeit und eines Satzes von Paketen, wie z. b. der Intel Math Kernel Library, die die Leistung von r-Standard Vorgängen verbessern.  
  
+ **RevoScaleR** Ein R-Paket, mit dem Sie Berechnungen per Push an eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von übersetzen können. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]. Es enthält auch einen Satz von allgemeinen R-Funktionen, die neu gestaltet wurden, um eine bessere Leistung und Skalierbarkeit zu bieten. Sie können diese verbesserten Funktionen am Präfix **rx** erkennen. Darüber hinaus sind verbesserte Datenanbieter für eine Vielzahl von Quellen enthalten; diese Funktionen haben das Präfix **Rx**.

Sie können einen beliebigen Windows-basierten Code-Editor verwenden, der R unter [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] stützt, z. b. oder rstudio. Der Download von [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] umfasst zudem allgemeine Befehlszeilentools für R, z.B. „RGui.exe.“

## <a name="use-new-data-sources-and-compute-contexts"></a>Verwenden von neuen Datenquellen und computekontexten

Wenn Sie das revoscaler-Paket verwenden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]um eine Verbindung mit herzustellen, suchen Sie nach diesen Funktionen, die im R-Code verwendet werden:

+ **RxSqlServerData** ist eine im „RevoScaleR“-Paket bereitgestellte Funktion zur Unterstützung der verbesserten Datenkonnektivität mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neuen skalierbaren Pakete und R-Funktionen verwenden.
  
     Sie können diese Funktion im R-Code verwenden, um die *Datenquelle*zu definieren. Das Datenquellenobjekt gibt den Server und die Tabellen an, auf dem bzw. in denen sich die Daten befinden. Zudem verwaltet es das Lesen der Daten aus sowie das Schreiben der Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Das **RxInSqlServer** -Funktion kann der *Computekontext*neuen skalierbaren Pakete und R-Funktionen verwenden.  Sie können mit anderen Worten angeben, wo der R-Code ausgeführt werden soll: auf der lokalen Arbeitsstation oder auf dem Computer, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hostet.  Weitere Informationen finden Sie unter [revoscaler Functions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler).
  
     Wenn Sie Computekontext festlegen, wirkt sich das nur auf Berechnungen aus, die einen Remoteausführungskontext unterstützen, d.h. vom RevoScaleR-Paket bereitgestellte R-Vorgänge und verwandte Funktionen. Üblicherweise können R-Lösungen, die auf standardmäßigen CRAN-Paketen basieren, nicht im Remotecomputekontext ausgeführt werden. Sie können allerdings auf dem [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Computer ausgeführt werden, wenn sie mit T-SQL gestartet werden. Sie können aber mithilfe der `rxExec`-Funktion einzelne R-Funktionen aufrufen, und sie remote in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausführen.

Beispiele zum Erstellen und arbeiten mit Datenquellen und Ausführungs Kontexten finden Sie in diesen Tutorials:

+ [Tieferer Einblick in Data Science](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [Datenanalyse mit Microsoft R](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)

## <a name="deploy-r-code-to-production"></a>R-Code für die Produktion bereitstellen

Ein wichtiger Teil der Data Science ist die Bereitstellung Ihrer Analysen für andere Benutzer oder die Verwendung von Vorhersagemodellen zur Optimierung von Geschäftsergebnissen oder -prozessen. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]gestaltet sich der Wechsel zur Produktion einfach, wenn Ihr R-Skript oder das Modell fertig ist.

Weitere Informationen zum Verschieben Ihres Codes zur Ausführung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter [Operationalizing Your R Code](../../advanced-analytics/r/operationalizing-your-r-code.md)neuen skalierbaren Pakete und R-Funktionen verwenden.

Normalerweise beginnt der Bereitstellungsprozess mit dem Bereinigen Ihres Skripts, um den für die Produktion nicht erforderlichen Code zu entfernen. Wenn Sie Berechnungen näher an die Daten verschieben, finden Sie möglicherweise Möglichkeiten, Daten effizienter zu verschieben, zusammenzufassen oder darzustellen, als alles in R auszuführen.  Es wird empfohlen, dass Data Scientists einen Datenbankentwickler über Möglichkeiten zum Verbessern der Leistung informieren. Dies gilt insbesondere, wenn die Lösung eine Datenbereinigung oder Featureentwicklung durchführt, die in SQL effektiver sein könnte. Möglicherweise sind Änderungen an ETL-Prozessen erforderlich, um sicherzustellen, dass Workflows zum Erstellen oder Bewerten eines Modells erfolgreich ausgeführt werden und eingegebene Daten im richtigen Format vorliegen.

## <a name="see-also"></a>Siehe auch

[Vergleich der Basis-R-und revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)

[Revoscaler-Bibliothek in SQL Server](ref-r-revoscaler.md)
