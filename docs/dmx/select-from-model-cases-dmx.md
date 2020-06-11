---
title: Wählen Sie aus dem &lt; Modell aus &gt; . Fälle (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6753f90b76f70de9f7368a5656ba93b16a3740d1
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669608"
---
# <a name="select-from-ltmodelgtcases-dmx"></a>Wählen Sie aus dem &lt; Modell aus &gt; . Fälle (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Unterstützt Drillthrough und gibt die Fälle zurück, mit denen das Modell trainiert wurde. Sie können auch Strukturspalten zurückgeben, die nicht im Modell enthalten sind, wenn Drillthrough sowohl für die Miningstruktur als auch für das Miningmodell aktiviert wurde und wenn Sie über die entsprechenden Berechtigungen verfügen.  
  
 Wenn Drillthrough nicht für das Miningmodell aktiviert ist, erzeugt diese Anweisung einen Fehler.  
  
> [!NOTE]  
>  In Data Mining-Erweiterungen (DMX) können Sie Drillthrough nur beim Erstellen des Modells aktivieren. Mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie Drillthrough zu einem vorhandenen Modell hinzufügen. Das Modell muss jedoch erneut verarbeitet werden, bevor Sie die Fälle anzeigen oder abfragen können.  
  
 Weitere Informationen zum Aktivieren von Drillthrough finden Sie unter [Create Mining Model &#40;DMX&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)und [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Ausdrucks Liste*  
 Eine Liste von Ausdrücken, die durch Trennzeichen voneinander getrennt sind. Ein Ausdruck kann u. a. Spaltenbezeichner, benutzerdefinierte Funktionen und VBA-Funktionen einschließen.  
  
 Um eine Strukturspalte einzuschließen, die nicht im Miningmodell enthalten ist, verwenden Sie die Funktion `StructureColumn('<structure column name>')`.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Bedingungs Ausdruck*  
 Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie Drillthrough sowohl für das Miningmodell als auch für die Miningstruktur aktivieren, können Benutzer, die Mitglied einer Rolle mit Drillthroughberechtigungen für das Miningmodell und die Miningstruktur sind, auf Spalten in der Miningstruktur zugreifen, die nicht Teil des Miningmodells sind. Daher sollten Sie zum Schutz sensibler Daten oder persönlicher Informationen die Datenquellen Sicht so erstellen, dass persönliche Informationen maskiert werden, und die **AllowDrillThrough** -Berechtigung für eine Mining Struktur nur bei Bedarf erteilen.  
  
 Die [Verzögerung &#40;DMX-&#41;](../dmx/lag-dmx.md) -Funktion kann mit Zeitreihen Modellen verwendet werden, um die Zeitspanne zwischen den einzelnen Fällen und der Anfangszeit zurückzugeben oder zu filtern.  
  
 Mithilfe der [IsInNode-&#40;DMX-&#41;](../dmx/isinnode-dmx.md) -Funktion in der **Where** -Klausel werden nur Fälle zurückgegeben, die dem Knoten zugeordnet sind, der durch die NODE_UNIQUE_NAME-Spalte des Schemarowsets angegeben wird.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele basieren auf der Mining Struktur Ziel-Mailing, die auf der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank und den zugehörigen Mining Modellen basiert. Weitere Informationen finden Sie unter [Tutorial zu Data Mining-Grundlagen](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drillthrough-to-model-cases-and-structure-columns"></a>Beispiel 1: Drillthrough zu Modellfällen und Strukturspalten  
 Im folgenden Beispiel werden die Spalten für alle Fälle zurückgegeben, die zum Testen des Target Mailing-Modells verwendet wurden. Wenn die Miningstruktur, auf der das Modell aufbaut, kein Zurückhaltungstestdataset enthält, werden bei dieser Abfrage 0 Fälle zurückgegeben. Sie können die Ausdrucksliste dazu verwenden, nur die benötigten Spalten zurückzugeben.  
  
```  
SELECT * FROM [TM Decision Tree].Cases  
WHERE IsTestCase();  
```  
  
### <a name="example-2-drillthrough-to-training-cases-in-a-specific-node"></a>Beispiel 2: Drillthrough zu Trainingsfällen in einem bestimmten Knoten  
 Im folgenden Beispiel werden nur jene Fälle zurückgegeben, die verwendet wurden, um Cluster 2 zu trainieren. Der Knoten für Cluster 2 verfügt über den Wert "002" für die Spalte NODE_UNIQUE_NAME. Das Beispiel gibt außerdem eine Strukturspalte zurück, [Customer Key], die nicht Teil des Miningmodells war, und stellt den Alias `CustomerID` für die Spalte zur Verfügung. Beachten Sie, dass der Name der Strukturspalte als Zeichenfolgenwert übergeben wird und daher in Anführungszeichen und nicht in Klammern gesetzt werden muss.  
  
```  
SELECT StructureColumn('Customer Key') AS CustomerID, *   
FROM [TM_Clustering].Cases  
WHERE IsTrainingCase()  
AND IsInNode('002')  
```  
  
 Um eine Strukturspalte zurückzugeben, müssen Drillthroughberechtigungen sowohl im Miningmodell als auch in der Miningstruktur aktiviert sein.  
  
> [!NOTE]  
>  Nicht alle Miningmodelltypen unterstützen Drillthrough. Informationen zu den Modellen, die Drillthrough unterstützen, finden Sie unter [Drillthrough-Abfragen &#40;Data Mining-&#41;](https://docs.microsoft.com/analysis-services/data-mining/drillthrough-queries-data-mining).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wählen Sie &#40;DMX-&#41;](../dmx/select-dmx.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
