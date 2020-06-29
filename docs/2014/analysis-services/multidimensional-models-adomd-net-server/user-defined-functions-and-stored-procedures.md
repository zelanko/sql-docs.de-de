---
title: Benutzerdefinierte Funktionen und gespeicherte Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
author: minewiskan
ms.author: owend
ms.openlocfilehash: a49aa41d158bf2c9fd1ebb1a711d6ff35c0df98b
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469015"
---
# <a name="user-defined-functions-and-stored-procedures"></a>Benutzerdefinierte Funktionen und gespeicherte Prozeduren
  Mit ADOMD.NET-Server Objekten können Sie benutzerdefinierte Funktionen (User Defined Function, UDF) oder gespeicherte Prozeduren für erstellen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , die mit Metadaten und Daten vom Server interagieren. Diese prozessinternen Methoden werden durch Multidimensional Expressions (MDX)- oder Data Mining Extensions (DMX)-Anweisungen aufgerufen, um zusätzliche Funktionen bereitzustellen, die nicht den Wartezeiten eines Netzwerks unterworfen sind.  
  
## <a name="udf-examples"></a>UDF-Beispiele  
 Eine benutzerdefinierte Funktion (UDF) ist eine Methode, die im Zusammenhang mit einer MDX- oder DMX-Anweisung aufgerufen wird, eine beliebige Anzahl an Parametern unterstützt und jede Art von Daten zurückgeben kann.  
  
 Eine mit MDX erstellte benutzerdefinierte Funktion ist mit einer für DMX erstellten vergleichbar. Der Hauptunterschied besteht darin, dass bestimmte Eigenschaften von [Microsoft. das AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) -Objekt, z. b. die Eigenschaften [Microsoft. AnalysisServices. AdomdServer. Context. CURRENTCUBE *](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) und [Microsoft. AnalysisServices. AdomdServer. Context. CurrentMiningModel *](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) , ist nur für eine Skriptsprache oder die andere verfügbar.  
  
 Die folgenden Beispiele zeigen, wie man mit einer benutzerdefinierten Funktion eine Knotenbeschreibung zurückgibt, Tupeln filtert und einen Filter auf ein Tupel anwendet.  
  
### <a name="returning-a-node-description"></a>Zurückgeben einer Knotenbeschreibung  
 Im folgenden Beispiel wird eine benutzerdefinierte Funktion erstellt, mit der die Knotenbeschreibung für einen bestimmten Knoten zurückgegeben wird. Die benutzerdefinierte Funktion verwendet den derzeitigen Kontext, in dem sie ausgeführt wird, und ruft den Knoten mithilfe einer DMX FROM-Klausel aus dem aktuellen Miningmodell ab.  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 Nach der Bereitstellung kann das vorherige UDF-Beispiel durch folgenden DMX-Ausdruck, der den wahrscheinlichsten Vorhersageknoten abruft, aufgerufen werden. Die Beschreibung enthält Informationen, in denen die Bedingungen beschrieben werden, die den Vorhersageknoten bilden.  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a>Zurückgeben von Tupeln  
 Im folgenden Beispiel werden mit einem Satz und einer Rückgabezahl Tupeln nach dem Zufallsprinzip aus dem Satz abgerufen, wodurch schließlich eine Teilmenge zurückgegeben wird:  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 Das vorherige Beispiel wird in folgendem MDX-Beispiel aufgerufen. In diesem MDX-Beispiel werden fünf Zufalls Zustände oder Provinzen aus der **Adventure Works** -Datenbank abgerufen.  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a>Anwenden eines Filters auf ein Tupel  
 In folgendem Beispiel wird eine benutzerdefinierte Funktion definiert, mit der in einem Satz unter Verwendung des Expression-Objekts ein Filter auf jedes Tupel in dem Satz angewendet wird. Alle Tupel, die dem Filter entsprechen, werden einem zurückgegebenen Satz hinzugefügt.  
  
 [!code-csharp[Adomd.NetServer#FilterSet](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#filterset)]  
  
 Das vorangegangene Beispiel wird in folgendem MDX-Beispiel aufgerufen, bei dem der Satz auf mit 'A' beginnende Städte gefiltert wird.  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a>Beispiel für gespeicherte Prozeduren  
 In folgendem Beispiel verwendet eine MDX-basierte, gespeicherte Prozedur AMO, um bei Bedarf Partitionen für Internet Sales zu erstellen.  
  
 [!code-csharp[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#createinternetsalesmeasuregrouppartitions)]  
  
  
