---
title: SELECT FROM &lt;Model&gt; Vorhersage Join (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b592aef0ba3831c5513e039ee4552d826468e819
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928325"
---
# <a name="select-from-ltmodelgt-prediction-join-dmx"></a>SELECT FROM &lt;Model&gt; Vorhersage Join (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Verwendet ein Miningmodell dazu, die Status von Spalten vorherzusagen, die zu einer externen Datenquelle gehören. Die **Vorhersage Join** -Anweisung gleicht jeden Fall von der Quell Abfrage zum Modell ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <select expression list>   
FROM <model> | <sub select> [NATURAL] PREDICTION JOIN   
<source data query> [ON <join mapping list>]   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Ausdrucks Liste auswählen*  
 Eine durch Trennzeichen getrennte Liste mit Spaltenbezeichnern und Ausdrücken, die aus dem Miningmodell abgeleitet sind.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Unterauswahl*  
 Eine eingebettete SELECT-Anweisung.  
  
 *Quelldaten Abfrage*  
 Die Quellabfrage.  
  
 *joinmapping-Liste*  
 Optional. Ein logischer Ausdruck, in dem Spalten aus dem Modell mit Spalten aus der Quellabfrage verglichen werden.  
  
 *Bedingungs Ausdruck*  
 Optional. Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *Begriff*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die ON-Klausel definiert die Zuordnung zwischen den Spalten aus der Quellabfrage und den Spalten aus dem Miningmodell. Diese Zuordnung wird zum Weiterleiten von Spalten aus der Quell Abfrage an Spalten im Mining Modell verwendet, sodass die Spalten als Eingaben verwendet werden können, um die Vorhersagen zu erstellen. Spalten in der \< *Liste der joinzuordnung*> werden mit einem Gleichheitszeichen (=) verknüpft, wie im folgenden Beispiel gezeigt:  
  
```  
[MiningModel].ColumnA = [source data query].Column1 AND   
[MiningModel].ColumnB = [source data query].Column2 AND  
...  
```  
  
 Wenn Sie in der ON-Klausel eine geschachtelte Tabelle binden, müssen Sie die Schlüsselspalte mit Nichtschlüsselspalten verknüpfen, damit der Algorithmus ermitteln kann, zu welchem Fall der Datensatz der geschachtelten Spalte gehört.  
  
 Die Quellabfrage für den PREDICTION JOIN kann eine Tabellen- oder eine SINGLETON-Abfrage sein.  
  
 Sie können Vorhersagefunktionen angeben, die keinen Tabellen Ausdruck in der \< *SELECT-Ausdrucks Liste* zurückgeben> \<und den Bedingungs *Ausdruck*>.  
  
 Der **natürliche Vorhersage Join** ordnet automatisch Spaltennamen aus der Quell Abfrage zu, die den Spaltennamen im Modell entsprechen. Wenn Sie die **natürliche Vorhersage**verwenden, können Sie die ON-Klausel weglassen.  
  
 Die WHERE-Bedingung kann nur auf vorhersagbare Spalten oder verknüpfte Spalten angewendet werden.  
  
 Die ORDER BY-Klausel lässt nur eine einzelne Spalte als Argument zu, d. h. Sie können nicht nach mehreren Spalten sortieren.  
  
## <a name="example-1-singleton-query"></a>Beispiel 1: SINGLETON-Abfrage  
 Im folgenden Beispiel wird erläutert, wie eine Abfrage erstellt wird, die in Echtzeit vorhersagt, ob eine bestimmte Person ein Fahrrad kauft. In dieser Abfrage werden die Daten nicht in einer Tabelle oder einer anderen Datenquelle gespeichert, sondern direkt in die Abfrage eingegeben. Die Person in der Abfrage hat folgende Merkmale:  
  
-   35 Jahre alt  
  
-   Besitzt ein Haus  
  
-   Besitzt zwei Autos  
  
-   Hat zwei Kinder, die zu Hause leben  
  
 Wenn Sie das TM Decision Tree-Mining Modell und die bekannten Merkmale des Subjekts verwenden, gibt die Abfrage einen booleschen Wert zurück, der beschreibt, ob die Person das Fahrrad gekauft hat, und einen Satz von tabellarischen Werten, die von der [präthistogram &#40;DMX-&#41;](../dmx/predicthistogram-dmx.md) -Funktion zurückgegeben werden, die die Art der Vorhersage beschreiben.  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  PredictHistogram([Bike Buyer])  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 35 AS [Age],  
  '5-10 Miles' AS [Commute Distance],  
  '1' AS [House Owner Flag],  
  2 AS [Number Cars Owned],  
  2 AS [Total Children]) AS t  
```  
  
## <a name="example-2-using-openquery"></a>Beispiel 2: Verwenden von OPENQUERY  
 Das folgende Beispiel zeigt, wie Sie eine Batch Vorhersage Abfrage erstellen, indem Sie eine Liste potenzieller Kunden verwenden, die in einem externen Dataset gespeichert sind. Da die Tabelle Teil einer Datenquellen Sicht ist, die für eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]definiert wurde, kann die Abfrage [OPENQUERY](../dmx/source-data-query-openquery.md) zum Abrufen der Daten verwenden. Da sich die Namen der Spalten in der Tabelle von denen im Mining Modell unterscheiden, muss die **on** -Klausel verwendet werden, um die Spalten in der Tabelle den Spalten im Modell zuzuordnen.  
  
 Die Abfrage gibt Folgendes zurück: den Vor- und Nachnamen jeder Person in der Tabelle sowie eine boolesche Spalte, die angibt, ob die Personen voraussichtlich ein Fahrrad kauften, dabei bedeutet 0 „wird vermutlich kein Fahrrad kaufen“ und 1 „wird vermutlich ein Fahrrad kaufen“. Die letzte Spalte enthält die Wahrscheinlichkeit für das vorhergesagte Ergebnis.  
  
```  
SELECT  
  t.[LastName],  
  t.[FirstName],  
  [TM Decision Tree].[Bike Buyer],  
  PredictProbability([Bike Buyer])  
From  
  [TM Decision Tree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [LastName],  
      [FirstName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [Education],  
      [Occupation],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
  [TM Decision Tree].[Gender] = t.[Gender] AND  
  [TM Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM Decision Tree].[Total Children] = t.[TotalChildren] AND  
  [TM Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM Decision Tree].[Education] = t.[Education] AND  
  [TM Decision Tree].[Occupation] = t.[Occupation] AND  
  [TM Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
```  
  
 Um das Dataset auf die Kunden zu beschränken, die voraussichtlich ein Fahrrad kaufen werden, und um die Liste anschließend nach Kundennamen zu sortieren, können Sie dem vorstehenden Beispiel eine WHERE-Klausel und eine ORDER BY-Klausel hinzufügen.  
  
```  
WHERE [BIKE Buyer]  
ORDER BY [LastName] ASC  
```  
  
## <a name="example-3-predicting-associations"></a>Beispiel 3: Vorhersagen von Zuordnungen  
 Das folgende Beispiel zeigt, wie eine Vorhersage durch Verwenden eines Modells erstellt wird, das über den [!INCLUDE[msCoName](../includes/msconame-md.md)] Association-Algorithmus erstellt wurde. Vorhersagen über ein Zuordnungsmodell können verwendet werden, um zugehörige Produkte zu empfehlen. Die folgende Abfrage gibt beispielsweise die drei Produkte zurück, die höchstwahrscheinlich zusammen gekauft werden:  
  
-   Mountain Bottle Cage  
  
-   Mountain Tire Tube  
  
-   Mountain-200  
  
 Die [Vorhersage &#40;DMX-&#41;](../dmx/predict-dmx.md) -Funktion ist polymorph und kann mit allen Modelltypen verwendet werden. Sie verwenden den Wert3 als Argument für die Funktion, um die Anzahl der Elemente zu begrenzen, die von der Abfrage zurückgegeben werden. Die **Select** -Liste, die der Natural Vorhersage Join-Klausel folgt, liefert die Werte, die als Eingabe für die Vorhersage verwendet werden.  
  
```  
SELECT FLATTENED  
  PREDICT([Association].[v Assoc Seq Line Items], 3)  
FROM  
  [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
  UNION SELECT 'Mountain Tire Tube' AS [Model]  
  UNION SELECT 'Mountain-200' AS [Model]) AS [v Assoc Seq Line Items ]) AS t  
```  
  
 Beispielergebnisse:  
  
|Expression.Model|  
|----------------------|  
|HL Mountain Tire|  
|Water Bottle|  
|Fender Set – Mountain|  
  
 Da die Spalte, die das vorhersagbare Attribut `[v Assoc Seq Line Items]` enthält, eine Tabellenspalte ist, gibt die Abfrage eine einzelne Spalte zurück, die eine geschachtelte Tabelle enthält. Die Spalte der geschachtelten Tabelle erhält standardmäßig den Namen `Expression`. Wenn Ihr Anbieter keine hierarchischen Rowsets unterstützt, können Sie das **vereinfachte Schlüsselwort** verwenden, wie in diesem Beispiel gezeigt, um das Anzeigen der Ergebnisse zu vereinfachen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wählen Sie &#40;DMX-&#41;](../dmx/select-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
