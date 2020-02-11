---
title: Mining Modell Inhalt von Zuordnungs Modellen (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a1e525d7b42d058343e41ea154f0687fb969839
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083688"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a>Miningmodellinhalt von Zuordnungsmodellen (Analysis Services – Data Mining)
  In diesem Thema wird der Miningmodellinhalt beschrieben, der Modellen eigen ist, die den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules-Algorithmus verwenden. Eine Erläuterung der allgemeinen Miningmodellinhalte, die für alle Modelltypen gelten, und Statistikterminologie finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).  
  
## <a name="understanding-the-structure-of-an-association-model"></a>Grundlegendes zur Struktur von Zuordnungsmodellen  
 Ein Zuordnungsmodell besitzt eine einfache Struktur. Jedes Modell verfügt über einen einzigen übergeordneten Knoten, der das Modell und seine Metadaten darstellt, und jeder übergeordnete Knoten enthält eine einfache Liste der Itemsets und Regeln. Die Itemsets und Regeln werden nicht in Baumstrukturen dargestellt, sie werden, wie im folgenden Diagramm gezeigt, zuerst nach Itemsets und anschließend nach Regeln geordnet.  
  
 ![Struktur des Modellinhalts für Zuordnungsmodelle](../media/modelcontentstructure-assoc.gif "Struktur des Modellinhalts für Zuordnungsmodelle")  
  
 Jedes Itemset ist in seinem eigenen Knoten (NODE_TYPE = 7) enthalten. Der *Knoten* enthält die Definition des Itemsets, die Anzahl der Fälle, die dieses Itemset enthalten, sowie weitere Informationen.  
  
 Auch jede Regel ist in ihrem eigenen Knoten (NODE_TYPE = 8) enthalten. Eine *Regel* beschreibt ein allgemeines Muster dafür, wie Elemente zugeordnet werden. Eine Regel ist wie eine IF-THEN-Anweisung. Die linke Seite der Regel enthält eine vorhandene Bedingung oder einen Satz von Bedingungen. Die rechte Seite der Regel enthält das Element des Datasets, das normalerweise den Bedingungen auf der linken Seite zugeordnet ist.  
  
 **Hinweis** Wenn Sie entweder die Regeln oder die Itemsets extrahieren möchten, können Sie eine Abfrage verwenden, um nur die gewünschten Knoten Typen zurückzugeben. Weitere Informationen finden Sie unter [Beispiele für Zuordnungsmodellabfragen](association-model-query-examples.md).  
  
## <a name="model-content-for-an-association-model"></a>Modellinhalt eines Zuordnungsmodells  
 In diesem Abschnitt werden nur diejenigen Spalten des Miningmodellinhalts detaillierter und anhand von Beispielen erläutert, die für Zuordnungsmodelle relevant sind.  
  
 Informationen zu den allgemeinen Spalten im Schemarowset, z.B. MODEL_CATALOG und MODEL_NAME, finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).  
  
 MODEL_CATALOG  
 Name der Datenbank, in der das Modell gespeichert wird.  
  
 MODEL_NAME  
 Name des Modells.  
  
 ATTRIBUTE_NAME  
 Die Namen der Attribute, die diesem Knoten entsprechen.  
  
 NODE_NAME  
 Der Name des Knotens. Bei einem Zuordnungsmodell enthält diese Spalte den gleichen Wert wie NODE_UNIQUE_NAME.  
  
 NODE_UNIQUE_NAME  
 Der eindeutige Name des Knotens.  
  
 NODE_TYPE  
 Ein Zuordnungsmodell gibt nur die folgenden Knotentypen aus:  
  
|Knotentyp-ID|type|  
|------------------|----------|  
|1 (Model)|Stammknoten oder übergeordneter Knoten|  
|7 (Itemset)|Ein Itemset oder Auflistung von Attribut/Wert-Paaren. Beispiele:<br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> oder<br /><br /> `Gender = Male`.|  
|8 (Regel)|Eine Regel, die definiert, in welcher Beziehung Elemente zueinander stehen.<br /><br /> Beispiel:<br /><br /> `Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.|  
  
 NODE_CAPTION  
 Eine Bezeichnung oder Beschriftung, die dem Knoten zugeordnet ist.  
  
 **Itemsetknoten** Eine durch Trennzeichen getrennte Liste von Elementen.  
  
 **Regel Knoten** Enthält die linke und die Rechte Seite der Regel.  
  
 CHILDREN_CARDINALITY  
 Gibt die Anzahl von untergeordneten Elementen des aktuellen Knotens an.  
  
 Über **geordneter Knoten** Gibt die Gesamtanzahl von Itemsets plus Regeln an.  
  
> [!NOTE]  
>  Eine Aufschlüsselung der Anzahl von Itemsets und Regeln finden Sie unter NODE_DESCRIPTION für den Stammknoten des Modells.  
  
 **Itemset-oder Regel Knoten** Immer 0.  
  
 PARENT_UNIQUE_NAME  
 Der eindeutige Name des dem Knoten übergeordneten Elements.  
  
 Über **geordneter Knoten** Immer NULL.  
  
 **Itemset-oder Regel Knoten** Immer 0.  
  
 NODE_DESCRIPTION  
 Eine benutzerfreundliche Beschreibung des Knoteninhalts.  
  
 Über **geordneter Knoten** Enthält eine durch Trennzeichen getrennte Liste der folgenden Informationen über das Modell:  
  
|Element|BESCHREIBUNG|  
|----------|-----------------|  
|ITEMSET_COUNT|Anzahl aller Itemsets im Modell.|  
|RULE_COUNT|Anzahl aller Regeln im Modell.|  
|MIN_SUPPORT|Die minimale Unterstützung für jedes einzelnes Itemset.<br /><br /> **Hinweis** Dieser Wert kann sich von dem Wert unterscheiden, den Sie für den *minimalen _Support* Parameter festgelegt haben.|  
|MAX_SUPPORT|Die maximale Unterstützung für jedes einzelne Itemset.<br /><br /> **Hinweis** Dieser Wert kann sich von dem Wert unterscheiden, den Sie für den *MAXIMUM_SUPPORT* -Parameter festgelegt haben.|  
|MIN_ITEMSET_SIZE|Die Größe des kleinsten Itemsets, die als Anzahl von Elementen dargestellt wird.<br /><br /> Ein Wert von 0 gibt an, dass der `Missing`-Status als unabhängiges Element behandelt wurde.<br /><br /> **Hinweis** Der Standardwert des *MINIMUM_ITEMSET_SIZE* -Parameters ist 1.|  
|MAX_ITEMSET_SIZE|Gibt die Größe des größten Itemsets an, das gefunden wurde.<br /><br /> **Hinweis** Dieser Wert wird durch den Wert beschränkt, den Sie bei der Erstellung des Modells für den *MAX_ITEMSET_SIZE* -Parameter festgelegt haben. Der erste Wert kann den anderen Wert nie übersteigen, aber er kann kleiner sein. Der Standardwert ist 3.|  
|MIN_PROBABILITY|Die minimale Wahrscheinlichkeit, die für jedes einzelne Itemset oder eine Regel im Modell erkannt wurde.<br /><br /> Beispiel: 0,400390625<br /><br /> **Hinweis** Bei Itemsets ist dieser Wert immer größer als der Wert, den Sie bei der Erstellung des Modells für den *MINIMUM_PROBABILITY* -Parameter festgelegt haben.|  
|MAX_PROBABILITY|Die maximale Wahrscheinlichkeit, die für jedes einzelnes Itemset oder eine Regel im Modell erkannt wurde.<br /><br /> Beispiel: 1<br /><br /> **Hinweis** Es gibt keinen Parameter, um die maximale Wahrscheinlichkeit von Itemsets einzuschränken. Wenn Sie Elemente ausschließen möchten, die zu häufig vorkommen, verwenden Sie stattdessen den *MAXIMUM_SUPPORT* -Parameter.|  
|MIN_LIFT|Die Mindestmenge an Lift, die vom Modell für ein beliebiges Itemset bereitgestellt wird.<br /><br /> Beispiel: 0,4309369632511<br /><br /> Hinweis: Wenn Sie den minimalen Lift kennen, können Sie leichter bestimmen, ob der Lift für irgendein einzelnes Itemset signifikant ist.|  
|MAX_LIFT|Die Höchstmenge an Lift, die vom Modell für ein beliebiges Itemset bereitgestellt wird.<br /><br /> Beispiel: 1,95758227647523 **Hinweis** Wenn Sie den maximalen Lift kennen, können Sie leichter bestimmen, ob der Lift für irgendein einzelnes Itemset signifikant ist.|  
  
 **Itemsetknoten** Itemsetknoten enthalten eine Liste der Elemente, die als durch Trennzeichen getrennte Text Zeichenfolge angezeigt werden.  
  
 Beispiel:  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 Dies bedeutet, Trekkingreifen und Wasserflasche wurden zusammen gekauft.  
  
 **Regel Knoten** Regel Knoten enthalten eine linke und Rechte Seite der Regel, getrennt durch einen Pfeil.  
  
 Beispiel: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`  
  
 Das bedeutet, dass jemand, der die Artikel Trekkingreifen und Wasserflasche kauft, wahrscheinlich auch den Artikel Fahrradkappe kauft.  
  
 NODE_RULE  
 Ein XML-Fragment, das die Regel oder das Itemset beschreibt, die bzw. das im Knoten eingebettet ist.  
  
 Über **geordneter Knoten** Blitz.  
  
 **Itemsetknoten** Blitz.  
  
 **Regel Knoten** Das XML-Fragment enthält zusätzliche nützliche Informationen über die Regel, z. b. die Unterstützung, das Vertrauen und die Anzahl der Elemente und die ID des Knotens, der die linke Seite der Regel darstellt.  
  
 MARGINAL_RULE  
 Leer.  
  
 NODE_PROBABILITY  
 Ein Wahrscheinlichkeits- oder ein Vertrauenswert, der dem Itemset oder der Regel zugeordnet ist.  
  
 Über **geordneter Knoten** Immer 0.  
  
 **Itemsetknoten** Wahrscheinlichkeit des Itemsets.  
  
 **Regel Knoten** Der Vertrauens Wert für die Regel.  
  
 MARGINAL_PROBABILITY  
 Identisch mit NODE_PROBABILITY.  
  
 NODE_DISTRIBUTION  
 Die Tabelle enthält sehr unterschiedliche Informationen, je nachdem, ob der Knoten ein Itemset oder eine Regel ist.  
  
 Über **geordneter Knoten** Blitz.  
  
 **Itemsetknoten** Listet jedes Element im Itemset sowie einen Wahrscheinlichkeits-und Unterstützungs Wert auf. Wenn das Itemset beispielsweise zwei Itemset enthält, wird der Name jedes Produkts zusammen mit der Anzahl der Fälle aufgeführt, die jedes Produkt enthalten.  
  
 **Regel Knoten** Enthält zwei Zeilen. Die erste Zeile enthält das Attribut von der rechten Seite der Regel, d. das vorhergesagte Element zusammen mit einem Vertrauenswert.  
  
 Die zweite Zeile ist Zuordnungsmodellen eigen. Sie enthält einen Zeiger auf das Itemset auf der rechten Seite der Regel. Der Zeiger wird in der ATTRIBUTE_VALUE-Spalte als ID des Itemset dargestellt, das nur das Element von der rechten Seite enthält.  
  
 Wenn die Regel beispielsweise `If {A,B} Then {C}`lautet, enthält die Tabelle den Namen des Elements `{C}`und die ID des Knotens, der das Itemset für Element C enthält.  
  
 Dieser Zeiger ist nützlich, weil Sie anhand des Itemsetknotens bestimmen können, wie viele Fälle insgesamt das Produkt von der rechten Seite beinhalten. Die Fälle, für welche die Regel `If {A,B} Then {C}` gilt, stellen eine Teilmenge der Fälle dar, die im Itemset für `{C}`aufgeführt sind.  
  
 NODE_SUPPORT  
 Die Anzahl der Fälle, die diesen Knoten unterstützen.  
  
 Über **geordneter Knoten** Anzahl der Fälle im Modell.  
  
 **Itemsetknoten** Anzahl der Fälle, die alle Elemente im Itemset enthalten.  
  
 **Regel Knoten** Die Anzahl der Fälle, die alle in der Regel enthaltenen Elemente enthalten.  
  
 MSOLAP_MODEL_COLUMN  
 Enthält unterschiedliche Informationen, je nachdem, ob der Knoten ein Itemset oder eine Regel ist.  
  
 Über **geordneter Knoten** Blitz.  
  
 **Itemsetknoten** Blitz.  
  
 **Regel Knoten** Die ID des Itemsets, das die Elemente auf der linken Seite der Regel enthält. Wenn die Regel beispielsweise `If {A,B} Then {C}`lautet, enthält diese Spalte die ID des Itemsets, das nur `{A,B}`enthält.  
  
 MSOLAP_NODE_SCORE  
 Über **geordneter Knoten** Blitz.  
  
 **Itemsetknoten** Wichtigkeits Bewertung für das Itemset.  
  
 **Regel Knoten** Wichtigkeits Bewertung für die Regel.  
  
> [!NOTE]  
>  Die Wichtigkeit wird für Itemsets und Regeln auf unterschiedliche Weise berechnet. Weitere Informationen finden Sie unter [Technische Referenz für den Microsoft Association-Algorithmus](microsoft-association-algorithm-technical-reference.md).  
  
 MSOLAP_NODE_SHORT_CAPTION  
 Leer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Inhalt &#40;Analysis Services Data Mining-&#41;](mining-model-content-analysis-services-data-mining.md)   
 [Microsoft Association-Algorithmus](microsoft-association-algorithm.md)   
 [Beispiele für Zuordnungsmodellabfragen](association-model-query-examples.md)  
  
  
