---
title: Ausführen von Befehlen für eine analytische Datenquelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6f37e3fe4cccfbfc8824971881c7d5fb68240252
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117349"
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Ausführen von Befehlen für eine analytische Datenquelle
  Wenn eine Verbindung zu einer analytischen Datenquelle hergestellt wurde, können Sie ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekt verwenden, um Befehle für diese Datenquelle auszuführen und Ergebnisse von der Datenquelle zurückzugeben. Diese Befehle können mithilfe von multidimensionalen Ausdrücken (Multidimensional Expressions, MDX), Data Mining-Erweiterungen (DMX) oder einer begrenzten SQL-Syntax Daten abrufen. Darüber hinaus können Sie ASSL-Befehle (Analysis Services Scripting Language) verwenden, um die zugrunde liegende Datenbank zu bearbeiten.  
  
## <a name="creating-a-command"></a>Erstellen eines Befehls  
 Vor dem Ausführen eines Befehls müssen Sie diesen erstellen. Sie können einen Befehl auf zwei verschiedene Arten erstellen:  
  
-   Die erste Methode verwendet den <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Konstruktor, der das Ausführen eines Befehls für die Datenquelle ermöglicht sowie ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt angibt, auf dem der Befehl ausgeführt wird.  
  
-   Die zweite Methode verwendet die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts.  
  
 Der Text des auszuführenden Befehls kann abgefragt und mit der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>-Eigenschaft bearbeitet werden. Die Befehle, die Sie erstellen, müssen keine Daten zurückgeben, nachdem sie ausgeführt wurden.  
  
## <a name="running-a-command"></a>Ausführen eines Befehls  
 Wenn Sie ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekt erstellt haben, stehen mehrere <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A>-Methoden zur Verfügung, die Ihr Befehl zum Ausführen verschiedener Aktionen verwenden kann. In der folgenden Tabelle werden einige dieser Aktionen aufgeführt.  
  
|Aktion|Verwenden Sie diese Methode|  
|--------|---------------------|  
|Zurückgeben von Ergebnissen als Datenstrom|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A>, um ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekt zurückzugeben|  
|Zurückgeben eines <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekts|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Ausführen von Befehlen, die keine Zeilen zurückgeben|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Zurückgeben eines `XMLReader`-Objekts, das Daten in einem XMLA-kompatiblen Format (XML for Analysis) enthält|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Beispiel für das Ausführen eines Befehls  
 In diesem Beispiel wird der Befehl <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> verwendet, um einen XMLA-Befehl auszuführen, der den `Adventure Works DW`-Cube auf dem lokalen Server verarbeitet, ohne Daten zurückzugeben.  
  
 [!code-csharp[Adomd.NetClient#ExecuteXMLAProcessCommand](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#executexmlaprocesscommand)]  
  
  
