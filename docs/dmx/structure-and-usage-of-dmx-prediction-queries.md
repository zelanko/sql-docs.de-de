---
title: Struktur und Verwendung von DMX-Vorhersage Abfragen | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 99d8ef98ad4e86bce0e1beff819a8d140662aaf7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938060"
---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>Struktur und Verwendung von DMX-Vorhersageabfragen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]können Sie die Vorhersage Abfrage in Data Mining-Erweiterungen (DMX) verwenden, um unbekannte Spaltenwerte in einem neuen Dataset basierend auf den Ergebnissen eines Mining Modells vorherzusagen.  
  
 Welchen Abfragetyp Sie verwenden, hängt davon ab, welche Informationen Sie aus einem Modell erhalten möchten. Wenn Sie einfache Vorhersagen in Echtzeit erstellen möchten (beispielsweise um zu ermitteln, ob ein möglicher Kunde auf einer Website zur Rolle eines Fahrradkäufers passt), verwenden Sie eine SINGLETON-Abfrage. Wenn Sie einen Vorhersagebatch aus einer Menge von Fällen erstellen möchten, die in einer Datenquelle enthalten sind, verwenden Sie eine normale Vorhersageabfrage.  
  
## <a name="prediction-types"></a>Vorhersagetypen  
 Mit DMX können Sie folgende Typen von Vorhersagen erstellen:  
  
 PREDICTION JOIN-Abfrage  
 Wird dazu verwendet, Vorhersagen zu Eingabedaten auf Basis von Mustern zu erstellen, die im Miningmodell vorhanden sind. Auf diese Abfrage Anweisung muss eine **on** -Klausel folgen, die die Joinbedingungen zwischen den Mining Modell Spalten und den Eingabe Spalten bereitstellt.  
  
 Natürliche PREDICTION JOIN-Abfrage  
 Wird zum Erstellen von Vorhersagen verwendet, die auf Spaltennamen im Miningmodell basieren, die genau mit den Spaltennamen der Tabelle übereinstimmen, für die Sie die Abfrage ausführen. Diese Abfrage Anweisung erfordert keine **on** -Klausel, da die Joinbedingung automatisch basierend auf den übereinstimmenden Namen zwischen den Mining Modell Spalten und den Eingabe Spalten generiert wird.  
  
 Leere PREDICTION JOIN-Abfrage  
 Wird dazu verwendet, die wahrscheinlichste Vorhersage zu ermitteln, ohne Eingabedaten bereitstellen zu müssen. Es wird eine Vorhersage zurückgegeben, die nur auf dem Inhalt des Miningmodells basiert.  
  
 SINGLETON-Abfrage  
 Wird zum Erstellen einer Vorhersage verwendet, indem die Daten in der Abfrage bereitgestellt werden. Diese Anweisung ist hilfreich, weil Sie in der Abfrage einen Einzelfall bereitstellen können, um schnell ein Ergebnis zu erzielen. Beispielsweise können Sie eine solche Abfrage dazu verwenden vorherzusagen, ob eine Person, die weiblich, 35 Jahre alt und verheiratet ist, voraussichtlich ein Fahrrad kauft. Diese Abfrage erfordert keine externe Datenquelle.  
  
## <a name="query-structure"></a>Abfragestruktur  
 Zum Erstellen einer Vorhersageabfrage in DMX kombinieren Sie die folgenden Elemente:  
  
-   **[vereinfacht] auswählen**  
  
-   **TOP**  
  
-   *****Aus\<Modell>* **Vorhersage Join**      
  
-   **EIN**  
  
-   **WHERE**  
  
-   **ORDER BY**  
  
 Das **Select** -Element einer Vorhersage Abfrage definiert die Spalten und Ausdrücke, die im Resultset angezeigt werden, und kann die folgenden Daten enthalten:  
  
-   **Vorhersagen** oder **vorhersag** Bare Spalten aus dem Mining Modell.  
  
-   Jede Spalte aus den Eingabedaten, mit denen die Vorhersagen erstellt werden.  
  
-   Funktionen, die eine Datenspalte zurückgeben.  
  
 Das **from** * \<-Modell>* **Vorhersage Join** -Element definiert die Quelldaten, die zum Erstellen der Vorhersage verwendet werden sollen. Für eine SINGLETON-Abfrage ist dies eine Reihe von Werten, die Spalten zugewiesen sind. Für eine leere PREDICTION JOIN-Abfrage bleibt dieses Element leer.  
  
 Das **on** -Element ordnet die Spalten, die im Mining Modell definiert sind, den Spalten in einem externen DataSet zu. Sie müssen dieses Element nicht einfügen, wenn Sie eine leere oder natürliche PREDICTION JOIN-Abfrage erzeugen.  
  
 Sie können die **Where** -Klausel verwenden, um die Ergebnisse einer Vorhersage Abfrage zu filtern. Sie können eine **Top** -Klausel oder eine **Order by** -Klausel verwenden, um die wahrscheinlichsten Vorhersagen auszuwählen. Weitere Informationen zur Verwendung dieser Klauseln finden Sie unter [Select &#40;DMX&#41;](../dmx/select-dmx.md).  
  
 Weitere Informationen zur Syntax einer Vorhersage Anweisung finden [Sie unter Select from &#60;Model&#62; Vorhersage Join &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md) und [Select from &#60;Model&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Grundlegendes zur SELECT-Anweisung (DMX)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
