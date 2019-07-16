---
title: SELECT (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8bf766c6f0a7fd757b280b0f950a43cfdc025929
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928427"
---
# <a name="select-dmx"></a>SELECT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **wählen** Anweisung in der Data Mining Extensions (DMX) für die folgenden Aufgaben im Datamining verwendet wird:  
  
-   Durchsuchen des Inhalts eines vorhandenen Miningmodells  
  
-   Erstellen von Vorhersagen aus einem vorhandenen Miningmodell  
  
-   Erstellen einer Kopie eines vorhandenen Miningmodells  
  
-   Durchsuchen der Miningstruktur  
  
 Obwohl die vollständige Syntax dieser Anweisung komplex ist, können die Hauptklauseln, die für das Durchsuchen eines Modells und der ihm zugrunde liegenden Struktur verwendet werden, wie folgt zusammengefasst werden:  
  
```  
SELECT [FLATTENED] [TOP <n>] <select list>  
FROM <model/structure>[.aspect]  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
## <a name="flattened"></a>FLATTENED  
 Einige Data Mining-Clients unterstützen keine Resultsets in hierarchischem Format von einem Data Mining-Anbieter. Der Client kann möglicherweise keine Hierarchie verwalten oder muss die Ergebnisse in einer einzelnen denormalisierten Tabelle speichern. Sollen die Daten aus geschachtelten Tabellen in vereinfachte Tabellen konvertiert werden, müssen Sie für die Anforderungsergebnisse fordern, dass sie vereinfacht werden.  
  
 Verwenden, um die Ergebnisse der Abfrage zu vereinfachen, die **wählen** Syntax mit dem **FLATTENED** -Option wie im folgenden Beispiel gezeigt:  
  
```  
SELECT FLATTENED <select list> FROM ...  
```  
  
## <a name="top-n-and-order-by"></a>TOP \<n > und ORDER BY  
 Sie können die Ergebnisse einer Abfrage mithilfe eines Ausdrucks sortieren, und klicken Sie dann eine Teilmenge der Ergebnisse zurückgeben können, indem Sie eine Kombination aus den **ORDER BY** und **oben** Klauseln. Dies ist hilfreich für Szenarien wie gezieltes Mailing, in dem Sie Ergebnisse nur an die Personen senden möchten, die am wahrscheinlichsten antworten. Sie Sortieren der Ergebnisse eines Ziels für e-Mail-Abfrage nach der vorhersagewahrscheinlichkeit könnten, und klicken Sie dann nur die oberste zurückgeben \<n > Ergebnisse.  
  
## <a name="select-list"></a>Wählen Sie aus  
 Die  *\<select-Liste >* kann Verweise auf skalare Spalten, Vorhersagefunktionen und Ausdrücke enthalten. Welche Optionen verfügbar sind, hängt vom Algorithmus und den folgenden Kontexten ab:  
  
-   Wird eine Miningstruktur oder ein Miningmodell abgefragt?  
  
-   Werden Inhalte oder Fälle abgefragt?  
  
-   Handelt es sich bei den Quelldaten um eine relationale Tabelle oder um einen Cube?  
  
-   Werden Vorhersagen getroffen?  
  
 In vielen Fällen können Sie Aliasse verwenden, oder Sie erstellen einfache Ausdrücke basierend auf den Elementen in der Auswahlliste. Das folgende Beispiel zeigt einen einfachen Ausdruck in Modellspalten:  
  
```  
SELECT [CustomerID], [Last Name] + ', ' + [FirstName] AS FullName  
FROM <model>.CASES  
```  
  
 Im folgenden Beispiel wird ein Alias für eine Spalte erstellt, die die Ergebnisse einer Vorhersagefunktion enthält:  
  
```  
SELECT Predict([Column1], 'Value') as Column1Prediction  
FROM MyModel  
JOIN <source data query>  
```  
  
## <a name="where"></a>WHERE  
 Sie können einschränken, die Fälle, die von der Abfrage, mithilfe zurückgegeben werden einer **, in denen** Klausel. Die **, in denen** -Klausel gibt an, dass Spaltenverweise im der **, in denen** Ausdruck müssen die gleiche Semantik wie Spaltenverweise in der  *\<select-Liste >* von der **wählen** -Anweisung und kann nur einen booleschen Ausdruck zurückgeben. Die Syntax für die **, in denen** -Klausel ist wie folgt  
  
```  
WHERE < condition expression >  
```  
  
 Der select-Liste und **, in denen** -Klausel eine **wählen** Anweisung muss die folgenden Regeln entsprechen:  
  
-   Die Auswahlliste muss einen Ausdruck enthalten, der kein boolesches Ergebnis zurückgibt. Sie können den Ausdruck ändern, aber der Ausdruck muss nicht boolesche Ergebnisse zurückgeben.  
  
-   Die **, in denen** -Klausel muss einen Ausdruck, der ein boolesches Ergebnis zurückgibt enthalten. Sie können die Klausel ändern, aber sie muss ein boolesches Ergebnis zurückgeben.  
  
## <a name="predictions"></a>Vorhersagen (Predictions)  
 Für das Erstellen von Vorhersagen gibt es zwei Syntaxformen:  
  
-   [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
-   [SELECT FROM &#60;Modell&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 Mit der ersten Form für Vorhersagen können Sie komplexe Vorhersagen in Echtzeit oder als Batch erstellen.  
  
 Die zweite Vorhersageform erstellt einen leeren PREDICTION JOIN für eine vorhersagbare Spalte in einem Miningmodell und gibt den wahrscheinlichsten Status der Spalte zurück. Die Ergebnisse einer solchen Abfrage basieren vollständig auf dem Inhalt des Miningmodells.  
  
 Sie können eine select-Anweisung in die Quellabfrage einer SELECT FROM PREDICTION JOIN-Anweisung einfügen, indem Sie die folgende Syntax verwenden.  
  
```  
SELECT FROM PREDICTION JOIN (<SELECT statement>) AS t, WHERE <SELECT statement>  
```  
  
 Weitere Informationen zum Erstellen von Vorhersageabfragen finden Sie unter [Struktur und Verwendung von DMX-Vorhersageabfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md).  
  
## <a name="clause-syntax"></a>Klauselsyntax  
 Aufgrund der Komplexität der Browsen mit der **wählen** -Anweisung, ausführliche Syntaxelemente und Argumente Klauseln beschrieben. Weitere Informationen zu den einzelnen Klauseln erhalten Sie, wenn Sie auf ein Thema in der folgenden Liste klicken:  
  
 [SELECT DISTINCT FROM &#60;Modell &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
 [SELECT FROM &#60;Modell&#62;. Inhalt &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
 [SELECT FROM &#60;Modell&#62;. Fällen &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
 [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
 [SELECT FROM &#60;model&#62;.DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
 [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
 [SELECT FROM &#60;Modell&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 [SELECT FROM &#60;Struktur&#62;. FÄLLEN](../dmx/select-from-structure-cases.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)  
  
  
