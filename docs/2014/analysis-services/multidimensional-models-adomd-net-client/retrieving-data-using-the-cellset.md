---
title: Abrufen von Daten mittels CellSet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- CellSet object
- retrieving data
- data retrieval [ADOMD.NET], CellSet object
ms.assetid: 77e4ee58-882d-4012-91a3-0565f18a4882
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9bce95fa12e7f5437d6d1f3872470a57114b76d3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180341"
---
# <a name="retrieving-data-using-the-cellset"></a>Abrufen von Daten mittels Cellset
  Beim Abruf analytischer Daten bietet das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt die meiste Interaktivität und Flexibilität. Das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt ist ein im Arbeitsspeicher befindlicher Cache für hierarchische Daten und Metadaten, der die ursprüngliche Dimensionalität der Daten beibehält. Das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt kann darüber hinaus in einen Online- oder Offlinezustand traversiert werden. Aufgrund dieser Offline-Fähigkeit kann das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt verwendet werden, um Daten und Metadaten in beliebiger Reihenfolge einzusehen, und es stellt das umfangreichste Objektmodell für die Datenabfrage bereit. Diese Offline-Fähigkeit führt dazu, dass das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt den größten Verwaltungsaufwand erfordert und von allen ADOMD.NET-Objektmodellen zur Datenabfrage das langsamste ist.  
  
## <a name="retrieving-data-in-a-connected-state"></a>Abrufen von Daten im Onlinezustand  
 Um das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt für das Abrufen von Daten zu verwenden, führen Sie die folgenden Schritte durch:  
  
1.  **Erstellen Sie eine neue Instanz des Objekts.**  
  
     Um eine neue Instanz des <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekts zu generieren, rufen Sie die Methode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> oder die Methode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekts auf.  
  
2.  **Identifizieren Sie die Metadaten.**  
  
     Neben dem Abruf von Daten ruft ADOMD.NET auch Metadaten für das Cellset ab. Sobald der Befehl die Abfrage ausgeführt und einen <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> zurückgegeben hat, können Sie die Metadaten über diverse Objekte abrufen. Diese Metadaten werden benötigt, damit Clientanwendungen Cellsetdaten anzeigen und mit diesen interagieren können. Beispielsweise bieten viele Clientanwendungen Funktionen für ein Drilldown oder eine hierarchische Anzeige der untergeordneten Positionen einer angegebenen Position im Cellset.  
  
     In ADOMD.NET stellen die Eigenschaften <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Axes%2A> und <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.FilterAxis%2A> des <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekts die Metadaten der Abfrage und der Slicerachsen im zurückgegebenen Cellset dar. Beide Eigenschaften geben Verweise auf <xref:Microsoft.AnalysisServices.AdomdClient.Axis>-Objekte zurück, die wiederum die Positionen enthalten, die auf jeder Achse dargestellt sind.  
  
     Jedes <xref:Microsoft.AnalysisServices.AdomdClient.Axis>-Objekt enthält eine Auflistung von <xref:Microsoft.AnalysisServices.AdomdClient.Position>-Objekten, die die Menge der Tupel darstellen, die für diese Achse verfügbar sind. Jedes <xref:Microsoft.AnalysisServices.AdomdClient.Position>-Objekt stellt ein einzelnes Tupel dar, das ein oder mehr Elemente enthält, die durch eine Auflistung von <xref:Microsoft.AnalysisServices.AdomdClient.Member>-Objekten dargestellt werden.  
  
3.  **Abrufen von Daten aus der cellsetauflistung ab.**  
  
     Neben dem Abruf von Metadaten ruft ADOMD.NET auch Daten für das Cellset ab. Sobald der Befehl die Abfrage ausgeführt und einen <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> zurückgegeben hat, können Sie die Daten über die <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A>-Auflistung von <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> abrufen. Diese Auflistung enthält die Werte, die für die Schnittmenge aller Achsen in der Abfrage berechnet werden. Deshalb gibt es mehrere Indexer für den Zugriff auf jede Schnittmenge oder Zelle. Eine Liste der Indexer finden Sie unter <xref:Microsoft.AnalysisServices.AdomdClient.CellCollection.Item%2A>.  
  
### <a name="example-of-retrieving-data-in-a-connected-state"></a>Beispiel für das Abrufen von Daten im Onlinezustand  
 Das folgende Beispiel stellt eine Verbindung zum lokalen Server her und führt dann einen Befehl auf der Verbindung aus. Das Beispiel analysiert die Ergebnisse mithilfe des `CellSet`-Objektmodells: Die Beschriftungen (Metadaten) für die Spalten werden von der ersten Achse abgerufen, und die Beschriftungen (Metadaten) für jede Zeile werden von der zweiten Achse abgerufen, und die Schnittmenge wird mithilfe der <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.Cells%2A>-Auflistung abgerufen.  
  
 [!code-csharp[Adomd.NetClient#ReturnCommandUsingCellSet](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#returncommandusingcellset)]  
  
## <a name="retrieving-data-in-a-disconnected-state"></a>Abrufen von Daten im Offlinezustand  
 Durch das Laden von XML, das in einer vorherigen Abfrage zurückgegeben wurde, können Sie das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt verwenden, um eine umfangreiche Methode für das Durchsuchen analytischer Daten bereitzustellen, ohne dass eine aktive Verbindung erforderlich ist.  
  
> [!NOTE]  
>  Nicht alle Eigenschaften der Objekte, die über das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt verfügbar sind, sind auch im Offlinezustand verfügbar. Weitere Informationen finden Sie unter <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>.  
  
### <a name="example-of-retrieving-data-in-a-disconnected-state"></a>Beispiel für das Abrufen von Daten im Offlinezustand  
 Das folgende Beispiel ähnelt dem zuvor in diesem Thema behandelten Metadaten- und Datenbeispiel. Allerdings wird der Befehl im folgenden Beispiel mit einem Aufruf von <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A> ausgeführt, und das Ergebnis wird als `System.Xml.XmlReader` zurückgegeben. In diesem Beispiel wird das <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt dann mithilfe dieses `System.Xml.XmlReader` über die <xref:Microsoft.AnalysisServices.AdomdClient.CellSet.LoadXml%2A>-Methode aufgefüllt. Obwohl in diesem Beispiel der `System.Xml.XmlReader` umgehend geladen wird, können Sie das XML, das im Leser vorhanden ist, auf der Festplatte zwischenspeichern oder diese Daten auf beliebige Weise an eine andere Anwendung übergeben, bevor Sie die Daten in ein Cellset laden.  
  
 [!code-csharp[Adomd.NetClient#DemonstrateDisconnectedCellset](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#demonstratedisconnectedcellset)]  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Daten aus einer analytischen Datenquelle](retrieving-data-from-an-analytical-data-source.md)   
 [Abrufen von Daten mittels AdomdDataReader](retrieving-data-using-the-adomddatareader.md)   
 [Abrufen von Daten mittels XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  
