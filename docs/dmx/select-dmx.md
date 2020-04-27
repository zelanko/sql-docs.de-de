---
title: Select (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8bf766c6f0a7fd757b280b0f950a43cfdc025929
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928427"
---
# <a name="select-dmx"></a>SELECT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die **Select** -Anweisung in Data Mining Extensions (DMX) wird für die folgenden Aufgaben in Data Mining verwendet:  
  
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
  
 Um die Abfrageergebnisse zu vereinfachen, verwenden **Sie die SELECT** -Syntax mit der **vereinfachten Option,** wie im folgenden Beispiel gezeigt:  
  
```  
SELECT FLATTENED <select list> FROM ...  
```  
  
## <a name="top-n-and-order-by"></a>Top \<n> und Order by  
 Sie können die Ergebnisse einer Abfrage mithilfe eines Ausdrucks sortieren und dann eine Teilmenge der Ergebnisse zurückgeben, indem Sie eine Kombination aus der **Order by** -Klausel und der **Top** -Klausel verwenden. Dies ist hilfreich für Szenarien wie gezieltes Mailing, in dem Sie Ergebnisse nur an die Personen senden möchten, die am wahrscheinlichsten antworten. Sie können die Ergebnisse einer Vorhersage Abfrage für das Ziel mit der Vorhersage Wahrscheinlichkeit sortieren und dann nur die ersten \<n> Ergebnisse zurückgeben.  
  
## <a name="select-list"></a>Liste auswählen  
 Die * \<Auswahlliste>* kann skalare Spalten Verweise, Vorhersagefunktionen und Ausdrücke enthalten. Welche Optionen verfügbar sind, hängt vom Algorithmus und den folgenden Kontexten ab:  
  
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
 Sie können die Fälle begrenzen, die von der Abfrage zurückgegeben werden, indem Sie eine **Where** -Klausel verwenden. Die **Where** -Klausel gibt an, dass Spalten Verweise im **Where** -Ausdruck die gleiche Semantik wie Spalten Verweise in der * \<SELECT-Liste>* der **Select** -Anweisung aufweisen müssen und nur einen booleschen Ausdruck zurückgeben können. Die Syntax für die **Where** -Klausel lautet wie folgt:  
  
```  
WHERE < condition expression >  
```  
  
 Die SELECT-Liste und die **Where** -Klausel einer **Select** -Anweisung müssen die folgenden Regeln einhalten:  
  
-   Die Auswahlliste muss einen Ausdruck enthalten, der kein boolesches Ergebnis zurückgibt. Sie können den Ausdruck ändern, aber der Ausdruck muss nicht boolesche Ergebnisse zurückgeben.  
  
-   Die **Where** -Klausel muss einen Ausdruck enthalten, der ein boolesches Ergebnis zurückgibt. Sie können die Klausel ändern, aber sie muss ein boolesches Ergebnis zurückgeben.  
  
## <a name="predictions"></a>Vorhersagen (Predictions)  
 Für das Erstellen von Vorhersagen gibt es zwei Syntaxformen:  
  
-   [Wählen Sie aus &#60;Modell&#62; Vorhersage Join &#40;DMX aus&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
-   [Wählen Sie aus &#60;Modell&#62; &#40;DMX aus&#41;](../dmx/select-from-model-dmx.md)  
  
 Mit der ersten Form für Vorhersagen können Sie komplexe Vorhersagen in Echtzeit oder als Batch erstellen.  
  
 Die zweite Vorhersageform erstellt einen leeren PREDICTION JOIN für eine vorhersagbare Spalte in einem Miningmodell und gibt den wahrscheinlichsten Status der Spalte zurück. Die Ergebnisse einer solchen Abfrage basieren vollständig auf dem Inhalt des Miningmodells.  
  
 Mithilfe der folgenden Syntax können Sie eine SELECT-Anweisung in die Quell Abfrage einer SELECT from Vorhersage JOIN-Anweisung einfügen.  
  
```  
SELECT FROM PREDICTION JOIN (<SELECT statement>) AS t, WHERE <SELECT statement>  
```  
  
 Weitere Informationen zum Erstellen von Vorhersage Abfragen finden Sie unter [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md).  
  
## <a name="clause-syntax"></a>Klauselsyntax  
 Aufgrund der Komplexität des Browsens mit der **Select** -Anweisung werden ausführliche Syntax Elemente und Argumente in der-Klausel beschrieben. Weitere Informationen zu den einzelnen Klauseln erhalten Sie, wenn Sie auf ein Thema in der folgenden Liste klicken:  
  
 [Wählen Sie unterschiedliche &#60;Modell &#62; &#40;DMX aus&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
 [Wählen Sie aus &#60;Modell&#62; aus. Inhalt &#40;DMX-&#41;](../dmx/select-from-model-content-dmx.md)  
  
 [Wählen Sie aus &#60;Modell&#62; aus. Fälle &#40;DMX-&#41;](../dmx/select-from-model-cases-dmx.md)  
  
 [Wählen Sie aus &#60;Modell&#62; aus. SAMPLE_CASES &#40;DMX-&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
 [Wählen Sie aus &#60;Modell&#62; aus. DIMENSION_CONTENT &#40;DMX-&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
 [Wählen Sie aus &#60;Modell&#62; Vorhersage Join &#40;DMX aus&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
 [Wählen Sie aus &#60;Modell&#62; &#40;DMX aus&#41;](../dmx/select-from-model-dmx.md)  
  
 [Wählen Sie aus &#60;Struktur&#62; aus. Denen](../dmx/select-from-structure-cases.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)  
  
  
