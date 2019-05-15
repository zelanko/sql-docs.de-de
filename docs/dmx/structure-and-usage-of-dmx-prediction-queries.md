---
title: Struktur und Verwendung von DMX-Vorhersageabfragen | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 37ff157cbddb0894880f12097c977b923d92f177
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981913"
---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>Struktur und Verwendung von DMX-Vorhersageabfragen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  In [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], können Sie die Vorhersageabfrage in Data Mining Extensions (DMX), unbekannte Spaltenwerte in ein neues Dataset, das auf der Grundlage der Ergebnisse eines Miningmodells vorherzusagen.  
  
 Welchen Abfragetyp Sie verwenden, hängt davon ab, welche Informationen Sie aus einem Modell erhalten möchten. Wenn Sie einfache Vorhersagen in Echtzeit erstellen möchten (beispielsweise um zu ermitteln, ob ein möglicher Kunde auf einer Website zur Rolle eines Fahrradkäufers passt), verwenden Sie eine SINGLETON-Abfrage. Wenn Sie einen Vorhersagebatch aus einer Menge von Fällen erstellen möchten, die in einer Datenquelle enthalten sind, verwenden Sie eine normale Vorhersageabfrage.  
  
## <a name="prediction-types"></a>Vorhersagetypen  
 Mit DMX können Sie folgende Typen von Vorhersagen erstellen:  
  
 PREDICTION JOIN-Abfrage  
 Wird dazu verwendet, Vorhersagen zu Eingabedaten auf Basis von Mustern zu erstellen, die im Miningmodell vorhanden sind. Diese abfrageanweisung muss folgen einem **ON** -Klausel, die die Joinbedingungen zwischen den Miningmodellspalten und den Eingabespalten bereitstellt.  
  
 Natürliche PREDICTION JOIN-Abfrage  
 Wird zum Erstellen von Vorhersagen verwendet, die auf Spaltennamen im Miningmodell basieren, die genau mit den Spaltennamen der Tabelle übereinstimmen, für die Sie die Abfrage ausführen. Diese abfrageanweisung erfordert kein **ON** -Klausel, da die Joinbedingung automatisch generiert wird, basierend auf den entsprechenden Namen zwischen den Miningmodellspalten und den Eingabespalten.  
  
 Leere PREDICTION JOIN-Abfrage  
 Wird dazu verwendet, die wahrscheinlichste Vorhersage zu ermitteln, ohne Eingabedaten bereitstellen zu müssen. Es wird eine Vorhersage zurückgegeben, die nur auf dem Inhalt des Miningmodells basiert.  
  
 SINGLETON-Abfrage  
 Wird zum Erstellen einer Vorhersage verwendet, indem die Daten in der Abfrage bereitgestellt werden. Diese Anweisung ist hilfreich, weil Sie in der Abfrage einen Einzelfall bereitstellen können, um schnell ein Ergebnis zu erzielen. Beispielsweise können Sie eine solche Abfrage dazu verwenden vorherzusagen, ob eine Person, die weiblich, 35 Jahre alt und verheiratet ist, voraussichtlich ein Fahrrad kauft. Diese Abfrage erfordert keine externe Datenquelle.  
  
## <a name="query-structure"></a>Abfragestruktur  
 Zum Erstellen einer Vorhersageabfrage in DMX kombinieren Sie die folgenden Elemente:  
  
-   **WÄHLEN SIE [VEREINFACHT]**  
  
-   **TOP**  
  
-   **VON***\<Modell >***PREDICTION JOIN-Anweisung**   
  
-   **ON**  
  
-   **WHERE**  
  
-   **ORDER BY**  
  
 Die **wählen** -Element einer Vorhersageabfrage definiert die Spalten und Ausdrücken, die im Resultset angezeigt werden, und die folgenden Daten enthalten können:  
  
-   **Vorhersagen** oder **PredictOnly** Spalten aus dem Miningmodell aus.  
  
-   Jede Spalte aus den Eingabedaten, mit denen die Vorhersagen erstellt werden.  
  
-   Funktionen, die eine Datenspalte zurückgeben.  
  
 Die **FROM**  *\<Modell >* **PREDICTION JOIN** -Element definiert die Quelldaten, die zum Erstellen der Vorhersage verwendet werden. Für eine SINGLETON-Abfrage ist dies eine Reihe von Werten, die Spalten zugewiesen sind. Für eine leere PREDICTION JOIN-Abfrage bleibt dieses Element leer.  
  
 Die **ON** -Element ordnet die Spalten, die im Miningmodell auf Spalten eines externen Datasets definiert sind. Sie müssen dieses Element nicht einfügen, wenn Sie eine leere oder natürliche PREDICTION JOIN-Abfrage erzeugen.  
  
 Sie können die **, in dem** -Klausel, um die Ergebnisse einer Vorhersageabfrage filtern. Sie können eine **oben** oder **ORDER BY** -Klausel, um die wahrscheinlichsten Vorhersagen auszuwählen. Weitere Informationen zum Verwenden dieser Klauseln finden Sie unter [wählen &#40;DMX&#41;](../dmx/select-dmx.md).  
  
 Weitere Informationen zur Syntax einer vorhersageanweisung finden Sie unter [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41; ](../dmx/select-from-model-prediction-join-dmx.md) und [SELECT FROM &#60;Modell&#62; &#40;DMX &#41;](../dmx/select-from-model-dmx.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Understanding the DMX Select Statement (Grundlegendes zur SELECT-Anweisung)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
