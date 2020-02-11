---
title: 'Lektion 4: Ausführen von Market Basket-Vorhersagen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63312110"
---
# <a name="lesson-4-executing-market-basket-predictions"></a>Lektion 4: Ausführen von Warenkorbvorhersagen
  In dieser Lektion verwenden Sie die DMX `SELECT` -Anweisung, um Vorhersagen basierend auf den Zuordnungs Modellen zu erstellen, die Sie in [Lektion 2: Hinzufügen von Mining Modellen zur Market Basket-Mining Struktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)erstellt haben. Eine Vorhersageabfrage wird unter Verwendung der DMX `SELECT`-Anweisung unter Hinzufügung einer `PREDICTION JOIN`-Klausel erstellt. Weitere Informationen zur Syntax eines Vorhersage Joins finden [Sie unter Select from &#60;Model&#62; Vorhersage Join &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).  
  
 Das **Select from \<Model> Vorhersage Join** -Formular der `SELECT` Anweisung enthält drei Teile:  
  
-   Einer Liste der Miningmodellspalten und Vorhersagefunktionen, die im Resultset zurückgegeben werden. Diese Liste kann auch Eingabespalten aus den Quelldaten enthalten.  
  
-   Eine Quellabfrage, die die zum Erstellen einer Vorhersage verwendeten Daten definiert. Wenn Sie beispielsweise zahlreiche Vorhersagen in einem Batch erstellen, kann die Quellabfrage eine Liste von Kunden abrufen.  
  
-   Einer Zuordnung von Miningmodellspalten und Quelldaten. Wenn die Namen der Spalten übereinstimmen, können Sie die `NATURAL PREDICTION JOIN`-Syntax verwenden und auf die Spaltenzuordnungen verzichten.  
  
 Mithilfe von Vorhersagefunktionen lässt sich die Abfrage optimieren. Vorhersagefunktionen stellen zusätzliche Informationen bereit, z. B. die Wahrscheinlichkeit des Eintreffens einer Vorhersage oder die Unterstützung für die Vorhersage im Trainingsdataset. Weitere Informationen zu Vorhersagefunktionen finden Sie unter [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
 Vorhersageabfragen können auch mit dem Generator für Vorhersageabfragen in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erstellt werden.  
  
## <a name="singleton-prediction-join-statement"></a>PREDICTION JOIN-Anweisung in einer SINGLETON-Vorhersageabfrage  
 Der erste Schritt besteht darin, eine SINGLETON-Abfrage zu erstellen, indem **Sie \<das Select from Model>-Vorhersage Join** -Syntax verwenden und einen einzelnen Satz von Werten als Eingabe bereitstellen. Es folgt ein allgemeines Beispiel für die SINGLETON-Anweisung:  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 In der ersten Codezeile werden die Spalten des Miningmodells definiert, das die Abfrage zurückgibt und der Name des Miningmodells angegeben, mit dem die Vorhersage generiert wurde:  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 In der nächsten Zeile des Codes wird der auszuführende Vorgang angegeben. Da Sie Werte für jede der Spalten angeben und die Namen genauso eingeben, dass sie mit dem Modell übereinstimmen, können Sie die `NATURAL PREDICTION JOIN`-Syntax verwenden. Wenn die Spaltennamen jedoch anders lauten, müssen Sie Zuordnungen zwischen den Spalten im Modell und den Spalten in den neuen Daten angeben, indem Sie eine `ON`-Klausel hinzufügen.  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 Die nächsten Codezeilen definieren die Produkte im Einkaufswagen, die zum Vorhersagen zusätzlicher Produkte, die ein Kunde erwerben wird, verwendet werden:  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen Sie eine Abfrage, mit der vorhergesagt wird, welche anderen Elemente ein Kunde wahrscheinlich kaufen wird. Dies geschieht auf der Grundlage vorhandener Elemente in Ihrem Warenkorb. Sie erstellen diese Abfrage, indem Sie das Mining Modell mit dem Standard *MINIMUM_PROBABILITY*verwenden.  
  
-   Erstellen einer Abfrage, die anhand von Artikeln, die sich bereits im Einkaufswagen eines Kunden befinden, vorhersagt, welche anderen Artikel ein Kunde wahrscheinlich kaufen wird. Diese Abfrage basiert auf einem anderen Modell, in dem *MINIMUM_PROBABILITY* auf 0,01 festgelegt wurde. Da der Standardwert für *MINIMUM_PROBABILITY* in Zuordnungs Modellen 0,3 ist, sollte die Abfrage für dieses Modell mehr mögliche Elemente als die Abfrage für das Standardmodell zurückgeben.  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a>Erstellen einer Vorhersage durch Verwenden eines Modells mit dem MINIMUM_PROBABILITY-Standardwert  
  
#### <a name="to-create-an-association-query"></a>So erstellen Sie eine Zuordnungsabfrage  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** , um den Abfrage-Editor zu öffnen.  
  
2.  Kopieren Sie das Standardbeispiel der `PREDICTION JOIN`-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     Sie können einfach den Spaltennamen [Products] einschließen, aber mithilfe der [Vorhersage &#40;DMX-&#41;](/sql/dmx/predict-dmx) Funktion können Sie die Anzahl der vom Algorithmus zurückgegebenen Produkte auf drei begrenzen. Sie können auch `INCLUDE_STATISTICS` verwenden. Damit werden der Unterstützungswert, die Wahrscheinlichkeit und die angepasste Wahrscheinlichkeit für jedes Produkt zurückgegeben. Mithilfe dieser statistischen Informationen können Sie die Genauigkeit der Vorhersage bewerten.  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Default Association]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     durch:  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     Diese Anweisung verwendet die `UNION`-Anweisung, um drei Produkte anzugeben, die zusammen mit den vorhergesagten Produkten im Einkaufskorb enthalten sein müssen. Die Modell-Spalte in der `SELECT`-Anweisung entspricht der Modell-Spalte, die in der geschachtelten Products-Tabelle enthalten ist.  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Association Prediction.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
     Die Abfrage gibt eine Tabelle zurück, die drei Produkte enthält: HL Mountain Tire, Fender Set - Mountain und ML Mountain Tire. In der Tabelle werden diese zurückgegebenen Produkte in der Reihenfolge ihrer Wahrscheinlichkeit aufgeführt. Das zurückgegebene Produkt, dessen Wahrscheinlichkeit, zusammen mit den in der Abfrage angegebenen drei Produkten in den gleichen Warenkorb eingefügt zu werden, am höchsten ist, wird an der Spitze der Tabelle angezeigt. Die folgenden zwei Produkte besitzen die nächsthöhere Wahrscheinlichkeit, in den Warenkorb eingefügt zu werden. Die Tabelle enthält zudem statistische Informationen, die die Genauigkeit der Vorhersage beschreiben.  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a>Erstellen einer Vorhersage durch Verwenden eines Modells mit dem MINIMUM_PROBABILITY-Wert 0,01  
  
#### <a name="to-create-an-association-query"></a>So erstellen Sie eine Zuordnungsabfrage  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** , um den Abfrage-Editor zu öffnen.  
  
2.  Kopieren Sie das Standardbeispiel der `PREDICTION JOIN`-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Modified Association]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     durch:  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     Diese Anweisung verwendet die `UNION`-Anweisung, um drei Produkte anzugeben, die zusammen mit den vorhergesagten Produkten im Einkaufskorb enthalten sein müssen. Die `[Model]`-Spalte in der `SELECT`-Anweisung entspricht der Spalte, die in der geschachtelten Products-Tabelle enthalten ist.  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Modified Association Prediction.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
     Die Abfrage gibt eine Tabelle zurück, die drei Produkte enthält: HL Mountain Tire, Water Bottle und Fender Set - Mountain. In der Tabelle werden diese Produkte in der Reihenfolge ihrer Wahrscheinlichkeit aufgeführt. Das Produkt, das an der Spitze der Tabelle angezeigt wird, besitzt die höchste Wahrscheinlichkeit, zusammen mit den in der Abfrage angegebenen drei Produkten in den gleichen Warenkorb eingefügt zu werden. Die restlichen Produkte besitzen die nächsthöhere Wahrscheinlichkeit, in den Warenkorb eingefügt zu werden. Die Tabelle enthält auch Statistiken, die die Genauigkeit der Vorhersage beschreiben.  
  
     Sie können in den Ergebnissen dieser Abfrage erkennen, dass der Wert des *MINIMUM_PROBABILITY* -Parameters die von der Abfrage zurückgegebenen Ergebnisse beeinflusst.  
  
 Dies ist der letzte Schritt im Market Basket-Lernprogramm. Sie verfügen jetzt über einen Satz von Modellen, mit dem sich vorhersagen lässt, welche Produkte von Kunden möglicherweise gleichzeitig gekauft werden.  
  
 Informationen zur Verwendung von DMX in einem anderen Vorhersage Szenario finden Sie unter [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiele für Zuordnungs Modell Abfragen](../../2014/analysis-services/data-mining/association-model-query-examples.md)   
 [Schnittstellen für Data Mining-Abfragen](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
