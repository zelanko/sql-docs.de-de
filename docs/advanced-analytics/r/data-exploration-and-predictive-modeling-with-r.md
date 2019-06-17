---
title: Datensuche und vorhersagemodellierung mit R – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: de293cd7caf481c51e4195a82ac036526c477739
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642011"
---
# <a name="data-exploration-and-predictive-modeling-with-r-in-sql-server"></a>Datensuche und vorhersagemodellierung mit R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Verbesserungen der Data Science-Prozess, die durch die Integration in SQL Server möglich sind.

Betrifft: SQL Server 2016 R Services, SQL Server 2017-Machine Learning ein Dienste

## <a name="the-data-science-process"></a>Data Science-Prozess

Datenanalysten verwenden R häufig zum Durchsuchen von Daten und Erstellen von Vorhersagemodellen. Dies ist normalerweise ein iterativer Prozess durch Ausprobieren, bis ein geeignetes Vorhersagemodell erreicht wird. Als erfahrener Datenanalyst können Sie eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herstellen und die Daten mithilfe des RODBC-Pakets auf die lokale Arbeitsstation abrufen. Dort können Sie die Daten untersuchen und mithilfe von R-Standardpaketen ein Vorhersagemodell erstellen.

Dieser Ansatz hat jedoch viele Nachteile mit sich, diese Hae beeinträchtigt die größere Akzeptanz von R im Unternehmen. 

+ Verschieben von Daten kann langsam, ineffizient oder unsicher sein.
+ R weist Einschränkungen hinsichtlich Leistung und Skalierung

Diese Nachteile werden deutlicher, wenn Sie zum Verschieben und Analysieren große Mengen von Daten oder Verwenden von Datasets, die nicht in den auf dem Computer verfügbaren Arbeitsspeicher passen, müssen.

Die neue, skalierbare-Pakete und R-Funktionen, die in enthaltenen [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] können Sie viele dieser Herausforderungen zu überwinden. 

## <a name="whats-different-about-revoscaler"></a>Was ist anders RevoScaleR?

Das **RevoScaleR** -Paket enthält die Implementierung einiger der beliebtesten R-Funktionen, die umgestaltet wurden, um die Parallelität und Skalierung bereitzustellen. Weitere Informationen finden Sie unter [Distributed-Computing mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing).

Das RevoScaleR-Paket bietet auch Unterstützung zum Ändern des *Ausführungskontexts*. Dies bedeutet, dass für eine gesamte Lösung oder für eine einzelne Funktion, die Sie angeben können, die Berechnungen mithilfe der Ressourcen des Computers ausgeführt werden sollen, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hostet, und nicht auf der lokalen Arbeitsstation. Dies hat mehrere Vorteile: Sie vermeiden unnötige Datenbewegungen und Sie können auf dem Server ergiebigere Berechnungsressourcen nutzen.

## <a name="r-environment-and-packages"></a>R-Umgebung und -Pakete

Der in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] unterstützte R-Umgebung besteht aus einer Runtime-Engine, der Open Source-Sprache und einer grafischen Engine, die von mehreren Paketen unterstützt und erweitert wird. Die Sprache ermöglicht eine Vielzahl von Erweiterungen, die mithilfe der Pakete implementiert werden.  

### <a name="using-other-r-packages"></a>Mithilfe von anderen R-Paketen

Zusätzlich zu den proprietären R-Bibliotheken mit Microsoft Machine Learning enthalten, können Sie fast alle R-Pakete in Ihrer Projektmappe, einschließlich:

+ Allgemeine R-Pakete aus öffentlichen Repositorys. Sie finden die beliebtesten Open Source-R-Pakete in öffentlichen Repositorys wie CRAN, wo über 6.000 Pakete gehostet werden, die von Datenanalysten verwendet werden können.
  
  Für die Windows-Plattform werden R-Pakete als ZIP-Dateien bereitgestellt, die unter der GPL-Lizenz heruntergeladen und installiert werden können.  
  
  Weitere Informationen zum Installieren der Pakete von Drittanbietern für die Verwendung mit [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]finden Sie unter [Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
  
+ Zusätzliche von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]bereitgestellte Pakete und Bibliotheken.   
  
     Das **RevoScaleR**-Paket enthält leistungsstarke Big Data-Analysen, verbesserte Versionen von Funktionen, die allgemeine Data Science-Aufgaben unterstützen, optimierte Lernmodule für Naive Bayes, lineare Regression, Zeitreihenmodelle, neuronale Netzwerke und erweiterte mathematische Bibliotheken.  
  
     Mit dem **RevoPemaR** -Paket können Sie eigene parallele, externe Speicheralgorithmen in R entwickeln.  
  
     Weitere Informationen zu diesen Paketen und deren Verwendung finden Sie unter [neuerungen von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler) und [erste Schritte mit RevoPemaR](https://docs.microsoft.com/machine-learning-server/r/how-to-developer-pemar). 

+ **MicrosoftML** enthält eine Auflistung von hochgradig optimierten Machine Learning-Algorithmen und Transformieren von Daten aus dem Microsoft Data Science-Team. Viele der Algorithmen werden auch in Azure Machine Learning verwendet. Weitere Informationen finden Sie unter [MicrosoftML in SQL Server](ref-r-microsoftml.md).

### <a name="r-development-tools"></a>R-Entwicklungstools

Wenn Ihre R-Lösung entwickeln möchten, achten Sie darauf, dass Sie zum Herunterladen von Microsoft R Client. Dieser kostenlose Download umfasst die Bibliotheken benötigt, um remoterechenkontexte und skalierbare Alorithms zu unterstützen:

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** Eine Verteilung von R-Laufzeitmoduls und einer Reihe von Paketen, z. B. der Intel Math Kernel-Bibliothek, die die Leistung von R-Standardfunktionen steigern.  
  
+ **RevoScaleR:** Ein R-Paket, das Sie können mithilfe von Push übertragen Berechnungen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]. installiert haben. Es enthält auch einen Satz von allgemeinen R-Funktionen, die neu gestaltet wurden, um eine bessere Leistung und Skalierbarkeit zu bieten. Sie können diese verbesserten Funktionen am Präfix **rx** erkennen. Darüber hinaus sind verbesserte Datenanbieter für eine Vielzahl von Quellen enthalten; diese Funktionen haben das Präfix **Rx**.

Können Sie einem beliebigen Windows-basierten Code-Editor, die R, z. B. unterstützt [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] oder RStudio. Der Download von [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] umfasst zudem allgemeine Befehlszeilentools für R, z.B. „RGui.exe.“

## <a name="use-new-data-sources-and-compute-contexts"></a>Mit neuen Daten Datenquellen und Computekontexten

Wenn das RevoScaleR-Paket zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], suchen Sie nach dieser Funktionen in Ihrem R-Code verwenden:

+ **RxSqlServerData** ist eine im „RevoScaleR“-Paket bereitgestellte Funktion zur Unterstützung der verbesserten Datenkonnektivität mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neuen skalierbaren Pakete und R-Funktionen verwenden.
  
     Sie können diese Funktion im R-Code verwenden, um die *Datenquelle*zu definieren. Das Datenquellenobjekt gibt den Server und die Tabellen an, auf dem bzw. in denen sich die Daten befinden. Zudem verwaltet es das Lesen der Daten aus sowie das Schreiben der Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Das **RxInSqlServer** -Funktion kann der *Computekontext*neuen skalierbaren Pakete und R-Funktionen verwenden.  Sie können mit anderen Worten angeben, wo der R-Code ausgeführt werden soll: auf der lokalen Arbeitsstation oder auf dem Computer, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz hostet.  Weitere Informationen finden Sie unter [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler).
  
     Wenn Sie Computekontext festlegen, wirkt sich das nur auf Berechnungen aus, die einen Remoteausführungskontext unterstützen, d.h. vom RevoScaleR-Paket bereitgestellte R-Vorgänge und verwandte Funktionen. Üblicherweise können R-Lösungen, die auf standardmäßigen CRAN-Paketen basieren, nicht im Remotecomputekontext ausgeführt werden. Sie können allerdings auf dem [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]-Computer ausgeführt werden, wenn sie mit T-SQL gestartet werden. Sie können aber mithilfe der `rxExec`-Funktion einzelne R-Funktionen aufrufen, und sie remote in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausführen.

Beispiele zum Erstellen und Arbeiten mit Datenquellen und Ausführungskontexten finden Sie in diesen Tutorials:

+ [Tieferer Einblick in Data Science](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [-Datenanalyse mithilfe von Microsoft R](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)

## <a name="deploy-r-code-to-production"></a>Bereitstellen Sie R-Code für die Produktion.

Ein wichtiger Teil der Data Science ist die Bereitstellung Ihrer Analysen für andere Benutzer oder die Verwendung von Vorhersagemodellen zur Optimierung von Geschäftsergebnissen oder -prozessen. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]gestaltet sich der Wechsel zur Produktion einfach, wenn Ihr R-Skript oder das Modell fertig ist.

Weitere Informationen zum Verschieben Ihres Codes zur Ausführung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter [Operationalizing Your R Code](../../advanced-analytics/r/operationalizing-your-r-code.md)neuen skalierbaren Pakete und R-Funktionen verwenden.

Normalerweise beginnt der Bereitstellungsprozess mit dem Bereinigen Ihres Skripts, um den für die Produktion nicht erforderlichen Code zu entfernen. Wenn Sie Berechnungen näher auf die Daten verschieben, möglicherweise Methoden zum effizienteren verschieben, zusammenfassen oder präsentieren von Daten als alles in r  Es wird empfohlen, dass die Datenanalysten mit einem Datenbankentwickler über Möglichkeiten zur Verbesserung der Leistung, insbesondere dann, wenn die Lösung kann die DatenBereinigung oder Featureentwicklung enthält, in SQL effektiver sein. Möglicherweise sind Änderungen an ETL-Prozessen erforderlich, um sicherzustellen, dass Workflows zum Erstellen oder Bewerten eines Modells erfolgreich ausgeführt werden und eingegebene Daten im richtigen Format vorliegen.

## <a name="see-also"></a>Siehe auch

[Vergleich von R-Base "und" RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)

[RevoScaleR-Bibliothek in SQL Server](ref-r-revoscaler.md)
