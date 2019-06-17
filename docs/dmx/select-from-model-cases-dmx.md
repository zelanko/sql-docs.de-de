---
title: SELECT FROM &lt;Modell&gt;. FÄLLEN (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f65aa4dc64e795235286eccd9f3283216ba6f4f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62658767"
---
# <a name="select-from-ltmodelgtcases-dmx"></a>SELECT FROM &lt;Modell&gt;. FÄLLEN (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Unterstützt Drillthrough und gibt die Fälle zurück, mit denen das Modell trainiert wurde. Sie können auch Strukturspalten zurückgeben, die nicht im Modell enthalten sind, wenn Drillthrough sowohl für die Miningstruktur als auch für das Miningmodell aktiviert wurde und wenn Sie über die entsprechenden Berechtigungen verfügen.  
  
 Wenn Drillthrough nicht für das Miningmodell aktiviert ist, erzeugt diese Anweisung einen Fehler.  
  
> [!NOTE]  
>  In Data Mining-Erweiterungen (DMX) können Sie Drillthrough nur beim Erstellen des Modells aktivieren. Mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie Drillthrough zu einem vorhandenen Modell hinzufügen. Das Modell muss jedoch erneut verarbeitet werden, bevor Sie die Fälle anzeigen oder abfragen können.  
  
 Weitere Informationen zur drillthroughaktivierung finden Sie unter [CREATE MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md), und [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *expression list*  
 Eine Liste von Ausdrücken, die durch Trennzeichen voneinander getrennt sind. Ein Ausdruck kann u. a. Spaltenbezeichner, benutzerdefinierte Funktionen und VBA-Funktionen einschließen.  
  
 Um eine Strukturspalte einzuschließen, die nicht im Miningmodell enthalten ist, verwenden Sie die Funktion `StructureColumn('<structure column name>')`.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *condition expression*  
 Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Drillthrough sowohl für das Miningmodell als auch für die Miningstruktur aktivieren, können Benutzer, die Mitglied einer Rolle mit Drillthroughberechtigungen für das Miningmodell und die Miningstruktur sind, auf Spalten in der Miningstruktur zugreifen, die nicht Teil des Miningmodells sind. Aus diesem Grund zum Schutz sensibler oder persönlicher Informationen sollten, erstellen Sie die Datenquellensicht so einrichten, persönliche Informationen verborgen sind, und **AllowDrillthrough** -Berechtigung für eine Miningstruktur nur bei Bedarf.  
  
 Die [Lag &#40;DMX&#41; ](../dmx/lag-dmx.md) Funktion kann mit zeitreihenmodellen verwendet werden, um oder filtern Sie nach die zeitverzögerung zwischen jedem Fall und der Anfangszeit zurückzugeben.  
  
 Mithilfe der [IsInNode &#40;DMX&#41; ](../dmx/isinnode-dmx.md) Funktion in der **, in denen** Klausel nur Fälle zurückgegeben, die dem Knoten zugeordnet sind, die durch die NODE_UNIQUE_NAME-Spalte des Schemarowsets angegeben ist.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele basieren auf der Miningstruktur Targeted Mailing, die basierend auf den [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Datenbank und den zugeordneten Miningmodellen. Weitere Informationen finden Sie unter [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
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
>  Nicht alle Miningmodelltypen unterstützen Drillthrough. Weitere Informationen zu den Modellen, die Drillthrough unterstützen, finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
