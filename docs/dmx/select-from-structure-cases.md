---
title: SELECT FROM &lt;Struktur&gt;. FÄLLEN | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 041d6ade2363b4a33528bd44438a2fcb440d61ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928294"
---
# <a name="select-from-ltstructuregtcases"></a>SELECT FROM &lt;Struktur&gt;. FÄLLEN
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Fälle zurück, die zum Erstellen der Miningstruktur verwendet wurden.  
  
 Wenn Drillthrough nicht für die Struktur aktiviert ist, erzeugt die Anweisung einen Fehler. Die Anweisung schlägt auch fehl, wenn der Benutzer keine Drillthroughberechtigungen für die Miningstruktur hat.  
  
 In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], Drillthrough für neue Miningstrukturen ist standardmäßig aktiviert. Um zu überprüfen, ob Drillthrough für eine bestimmte Struktur aktiviert ist, überprüfen Sie, ob der Wert des der **CacheMode** -Eigenschaftensatz auf **KeepTrainingCases**.  
  
 Wenn der Wert des **CacheMode** geändert wird, um **ClearAfterProcessing**, die strukturfälle im Cache gelöscht werden, und Sie können Drillthrough nicht verwenden.  
  
> [!NOTE]  
>  Sie können Drillthrough in der Miningstruktur nicht mit Data Mining-Erweiterungen (DMX) aktivieren oder deaktivieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Liste mit Ausdrücken*  
 Eine Liste von Ausdrücken, die durch Trennzeichen voneinander getrennt sind.  
  
 Ein Ausdruck kann Spaltenbezeichner, benutzerdefinierte Funktionen und VBA-Funktionen einschließen.  
  
 *Struktur*  
 Der Name der Struktur.  
  
 *Bedingungsausdruck*  
 Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Drillthrough sowohl für das Modell als auch für die Struktur aktivieren, kann jedes Mitglied einer Rolle mit Drillthroughberechtigungen für die Miningstruktur und das Modell mit der folgenden Syntax Strukturspalten zurückgeben, die nicht Teil des Modells sind:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Aus diesem Grund zum Schutz sensibler oder persönlicher Informationen sollten, erstellen Sie die Datenquellensicht so einrichten, persönliche Informationen verborgen sind, und **AllowDrillthrough** -Berechtigung für eine Miningstruktur oder ein Miningmodell nur, wenn erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele basieren auf der Miningstruktur, Targeted Mailing, die basierend auf den [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] -Datenbank und den zugeordneten Miningmodellen. Weitere Informationen finden Sie unter [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drill-through-to-structure-cases"></a>Beispiel 1: Drillthrough zu Strukturfällen  
 Im folgenden Beispiel wird eine Liste der 500 ältesten Kunden in der Miningstruktur Targeted Mailing zurückgegeben. Die Abfrage gibt alle Spalten im Miningmodell zurück, beschränkt die Zeilen jedoch auf die Kunden, die ein Fahrrad gekauft haben, und sortiert diese nach Alter. Sie können die Ausdrucksliste auch so bearbeiten, dass nur die benötigten Spalten zurückgegeben werden.  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>Beispiel 2: Drillthrough zu Test- oder Trainingsfällen nur  
 Im folgenden Beispiel wird eine Liste der zum Testen reservierten Strukturfälle für Targeted Mailing zurückgegeben. Wenn die Miningstruktur keinen Zurückhaltungstestsatz enthält, werden alle Fälle standardmäßig als Trainingsfälle behandelt, und bei dieser Abfrage würden 0 Fälle zurückgegeben werden.  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 Um die Trainingsfälle zurückzugeben, ersetzen Sie die Funktion `IsTrainingCase()`.  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
