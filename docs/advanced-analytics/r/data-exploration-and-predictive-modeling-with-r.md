---
title: Vorhersagemodellierung mit R
description: In diesem Artikel werden die Verbesserungen am Data-Science-Prozess beschrieben, die durch die Integration mit SQL Server ermöglicht werden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 561d1d32cef9102200bcc3b0730c96afed06d91a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727476"
---
# <a name="data-exploration-and-predictive-modeling-with-r-in-sql-server"></a>Datensuche und Vorhersagemodellierung mit R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Verbesserungen am Data-Science-Prozess beschrieben, die durch die Integration mit SQL Server ermöglicht werden.

Gilt für: SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

## <a name="the-data-science-process"></a>Der Data-Science-Prozess

Datenanalysten verwenden R häufig zum Durchsuchen von Daten und Erstellen von Vorhersagemodellen. Dies ist normalerweise ein iterativer Prozess durch Ausprobieren, bis ein geeignetes Vorhersagemodell erreicht wird. Als erfahrener Datenanalyst können Sie eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herstellen und die Daten mithilfe des RODBC-Pakets auf die lokale Arbeitsstation abrufen. Dort können Sie die Daten untersuchen und mithilfe von R-Standardpaketen ein Vorhersagemodell erstellen.

Dieser Ansatz birgt jedoch einige Nachteile, die die flächendeckende Einführung von R im Unternehmen erschwert haben: 

+ Die Datenverschiebung kann langsam, ineffizient oder unsicher sein.
+ R weist Leistungs- oder Skalierungseinschränkungen auf.

Diese Nachteile werden deutlicher, wenn Sie große Datenmengen verschieben und analysieren müssen oder Datasets verwenden, die nicht in den auf dem Computer verfügbaren Arbeitsspeicher passen.

Sie können viele dieser Herausforderungen mithilfe der neuen, skalierbaren Pakete und R-Funktionen meistern, die in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] enthalten sind. 

## <a name="whats-different-about-revoscaler"></a>Worin besteht der Unterschied zu RevoScaleR?

Das **RevoScaleR** -Paket enthält die Implementierung einiger der beliebtesten R-Funktionen, die umgestaltet wurden, um die Parallelität und Skalierung bereitzustellen. Weitere Informationen finden Sie unter [Verteiltes Computing mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).

Das RevoScaleR-Paket bietet auch Unterstützung zum Ändern des *Ausführungskontexts*. Dies bedeutet, dass für eine gesamte Lösung oder für eine einzelne Funktion, die Sie angeben können, die Berechnungen mithilfe der Ressourcen des Computers ausgeführt werden sollen, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hostet, und nicht auf der lokalen Arbeitsstation. Dies hat mehrere Vorteile: Sie vermeiden unnötige Datenbewegungen und Sie können auf dem Server ergiebigere Berechnungsressourcen nutzen.

## <a name="r-environment-and-packages"></a>R-Umgebung und -Pakete

Der in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] unterstützte R-Umgebung besteht aus einer Runtime-Engine, der Open Source-Sprache und einer grafischen Engine, die von mehreren Paketen unterstützt und erweitert wird. Die Sprache ermöglicht eine Vielzahl von Erweiterungen, die mithilfe der Pakete implementiert werden.  

### <a name="using-other-r-packages"></a>Verwenden anderer R-Pakete

Zusätzlich zu den proprietären R-Bibliotheken in Microsoft Azure Machine Learning können Sie nahezu alle R-Pakete in Ihrer Lösung verwenden, einschließlich der folgenden:

+ Allgemeine R-Pakete aus öffentlichen Repositorys. Sie finden die beliebtesten Open Source-R-Pakete in öffentlichen Repositorys wie CRAN, wo über 6.000 Pakete gehostet werden, die von Datenanalysten verwendet werden können.
  
  Für die Windows-Plattform werden R-Pakete als ZIP-Dateien bereitgestellt, die unter der GPL-Lizenz heruntergeladen und installiert werden können.  
  
  Weitere Informationen zum Installieren der Pakete von Drittanbietern für die Verwendung mit [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]finden Sie unter [Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
  
+ Zusätzliche von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]bereitgestellte Pakete und Bibliotheken.   
  
     Das **RevoScaleR**-Paket enthält leistungsstarke Big Data-Analysen, verbesserte Versionen von Funktionen, die allgemeine Data Science-Aufgaben unterstützen, optimierte Lernmodule für Naive Bayes, lineare Regression, Zeitreihenmodelle, neuronale Netzwerke und erweiterte mathematische Bibliotheken.  
  
     Mit dem **RevoPemaR** -Paket können Sie eigene parallele, externe Speicheralgorithmen in R entwickeln.  
  
     Weitere Informationen zu diesen Paketen und deren Verwendung finden Sie unter [Was ist RevoScaleR?](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) und [Erste Schritte mit RevoPemaR](https://docs.microsoft.com/machine-learning-server/r/how-to-developer-pemar). 

+ **MicrosoftML** enthält einige hochoptimierte Machine-Learning-Algorithmen und Datentransformationen, die vom Microsoft-Data-Science-Team ausgearbeitet wurden. Viele dieser Algorithmen werden auch in Azure Machine Learning verwendet. Weitere Informationen finden Sie unter [MicrosoftML in SQL Server](ref-r-microsoftml.md).

### <a name="r-development-tools"></a>R-Entwicklungstools

Laden Sie Microsoft R Client herunter, wenn Sie R-Lösungen entwickeln. Dieser kostenlose Download enthält die Bibliotheken, die Sie für die Unterstützung von Remotecomputekontexten und skalierbarer Algorithmen benötigen:

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Eine Verteilung der R-Runtime und einige Pakete, z. B. die mathematische Kernelbibliothek von Intel, die die Leistung von R-Standardvorgängen steigern.  
  
+ **RevoScaleR:** Ein R-Paket, mit dem Sie Berechnungen auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verlagern können. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]. Es enthält auch einen Satz von allgemeinen R-Funktionen, die neu gestaltet wurden, um eine bessere Leistung und Skalierbarkeit zu bieten. Sie können diese verbesserten Funktionen am Präfix **rx** erkennen. Darüber hinaus sind verbesserte Datenanbieter für eine Vielzahl von Quellen enthalten; diese Funktionen haben das Präfix **Rx**.

Sie können alle Windows-basierten Code-Editoren verwenden, die R unterstützen, z. B. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] oder RStudio. Der Download von [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] umfasst zudem allgemeine Befehlszeilentools für R, z.B. „RGui.exe.“

## <a name="use-new-data-sources-and-compute-contexts"></a>Verwenden neuer Datenquellen und Computekontexte

Wenn Sie die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des RevoScaleR-Pakets herstellen, können Sie diese Funktionen in Ihrem R-Code verwenden:

+ **RxSqlServerData** ist eine im „RevoScaleR“-Paket bereitgestellte Funktion zur Unterstützung der verbesserten Datenkonnektivität mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neuen skalierbaren Pakete und R-Funktionen verwenden.
  
     Sie können diese Funktion im R-Code verwenden, um die *Datenquelle*zu definieren. Das Datenquellenobjekt gibt den Server und die Tabellen an, auf dem bzw. in denen sich die Daten befinden. Zudem verwaltet es das Lesen der Daten aus sowie das Schreiben der Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Das **RxInSqlServer** -Funktion kann der *Computekontext*neuen skalierbaren Pakete und R-Funktionen verwenden.  Sie können mit anderen Worten angeben, wo der R-Code ausgeführt werden soll: auf der lokalen Arbeitsstation oder auf dem Computer, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hostet.  Weitere Informationen finden Sie unter [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler).
  
     Wenn Sie Computekontext festlegen, wirkt sich das nur auf Berechnungen aus, die einen Remoteausführungskontext unterstützen, d.h. vom RevoScaleR-Paket bereitgestellte R-Vorgänge und verwandte Funktionen. Üblicherweise können R-Lösungen, die auf standardmäßigen CRAN-Paketen basieren, nicht im Remotecomputekontext ausgeführt werden. Sie können allerdings auf dem [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Computer ausgeführt werden, wenn sie mit T-SQL gestartet werden. Sie können aber mithilfe der `rxExec`-Funktion einzelne R-Funktionen aufrufen, und sie remote in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausführen.

Beispiele für das Erstellen und Arbeiten mit Datenquellen und Ausführungskontexten finden Sie in diesen Tutorials:

+ [Tieferer Einblick in Data Science](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [Datenanalyse mithilfe von Microsoft R](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)

## <a name="deploy-r-code-to-production"></a>Bereitstellen von R-Code für die Produktion

Ein wichtiger Teil der Data Science ist die Bereitstellung Ihrer Analysen für andere Benutzer oder die Verwendung von Vorhersagemodellen zur Optimierung von Geschäftsergebnissen oder -prozessen. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]gestaltet sich der Wechsel zur Produktion einfach, wenn Ihr R-Skript oder das Modell fertig ist.

Weitere Informationen zum Verschieben Ihres Codes zur Ausführung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter [Operationalizing Your R Code](../../advanced-analytics/r/operationalizing-your-r-code.md)neuen skalierbaren Pakete und R-Funktionen verwenden.

Normalerweise beginnt der Bereitstellungsprozess mit dem Bereinigen Ihres Skripts, um den für die Produktion nicht erforderlichen Code zu entfernen. Wenn die Berechnungen näher an die Daten rücken, finden Sie möglicherweise bessere Wege als R, Daten noch effizienter zu verschieben, zusammenzufassen oder zu präsentieren. Wir empfehlen Data Scientists, sich mit einem Datenbankentwickler darüber auszutauschen, wie die Leistung verbessert werden kann. Das gilt insbesondere, wenn die Lösung für die Datenbereinigung oder Featureentwicklung eingesetzt werden soll, die in SQL effektiver durchgeführt werden können. Möglicherweise sind Änderungen an ETL-Prozessen erforderlich, um sicherzustellen, dass Workflows zum Erstellen oder Bewerten eines Modells erfolgreich ausgeführt werden und eingegebene Daten im richtigen Format vorliegen.

## <a name="see-also"></a>Weitere Informationen

[Grundlegende R-Funktionen und RevoScaleR-Funktionen im Vergleich](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)

[RevoScaleR-Bibliothek in SQL Server](ref-r-revoscaler.md)
