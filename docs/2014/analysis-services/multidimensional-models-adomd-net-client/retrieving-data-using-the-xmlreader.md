---
title: Abrufen von Daten mittels XmlReader | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- retrieving data
- XmlReader object
- data retrieval [ADOMD.NET], XmlReader object
ms.assetid: 420ec40e-be2d-413a-b4b2-6d2b1756e270
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 257777c40c829921680b8fce333bd6e44f6f57fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056816"
---
# <a name="retrieving-data-using-the-xmlreader"></a>Abrufen von Daten mittels XmlReader
  Die `XmlReader`-Klasse, die Bestandteil des `System.Xml`-Namespace für die Microsoft .NET Framework-Klassenbibliothek ist, ähnelt der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Klasse insofern, als die `XmlReader`-Klasse ebenfalls einen schnellen Vorwärtszugriff auf die Daten ohne Zwischenspeicherung ermöglicht. Wenn keine analytische Ansicht der Daten im Arbeitsspeicher mithilfe des <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekts erforderlich ist, eignet sich das `XmlReader`-Objekt perfekt für das Abrufen von XML-Daten, insbesondere wenn es sich um große Datenmengen handelt. Da `XmlReader` Daten streamt, ist es nicht erforderlich, dass `XmlReader` alle Daten abruft und zwischenspeichert, bevor sie für den Aufrufer verfügbar gemacht werden. Dies wäre der Fall, wenn ein <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>-Objekt zum Konvertieren der XML for Analysis-Antwort in eine analytische Objektmodelldarstellung verwendet würde.  
  
 Die `XmlReader`-Klasse bietet direkten Zugriff auf die von ADOMD.NET empfangene XML for Analysis-Antwort, wenn die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekts aufgerufen wird. Da es sich bei den abgerufenen Daten um nicht formatierte XML-Rohdaten handelt, müssen Sie die Daten und Metadaten manuell analysieren. Sobald die Daten abgerufen wurden, sollte das `XmlReader`-Objekt geschlossen werden.  
  
## <a name="retrieving-data-and-metadata"></a>Abrufen von Daten und Metadaten  
 Um die `XmlReader`-Klasse für das Abrufen von Daten zu verwenden, führen Sie die folgenden Schritte aus:  
  
1.  **Erstellen Sie eine neue Instanz des Objekts.**  
  
     Um eine neue Instanz der `XmlReader`-Klasse zu erstellen, rufen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A>- oder <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekts auf.  
  
2.  **Abrufen von Daten.**  
  
     Nachdem der Befehl die Abfrage ausgeführt hat und ein `XmlReader`-Objekt zurückgibt, müssen Sie die Daten und die Metadaten analysieren. Die XML-Daten und -Metadaten werden im systemeigenen Format angegeben, das vom XML for Analysis-Anbieter verwendet wird. Für die meisten XML for Analysis-Anbieter ist das systemeigene Format das `MDDataSet`-Format. Das `MDDataSet`-Format stellt sowohl Daten als auch Metadaten für Cellsets in einem gut strukturierten Format bereit. Weitere Informationen zum `MDDataSet`-Format finden Sie in der Spezifikation für XML for Analysis.  
  
3.  **Schließen des Readers an.**  
  
     Sie sollten immer die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A>-Methode aufrufen, wenn Sie die Verwendung des `XmlReader`-Objekts abgeschlossen haben. Solange ein `XmlReader`-Objekt geöffnet ist, ist dieses `XmlReader`-Objekt zur ausschließlichen Verwendung des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts berechtigt, das zum Ausführen des Befehls verwendet wurde. Sie sind in diesem Fall nicht in der Lage, Befehle mithilfe dieses <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> auszuführen, einschließlich der Erstellung eines weiteren `XmlReader` oder <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, bis Sie das ursprüngliche `XmlReader`-Objekt schließen.  
  
### <a name="example-of-retrieving-data-from-the-xmlreader"></a>Beispiel für das Abrufen von Daten aus XmlReader  
 Im folgenden Beispiel wird ein Befehl ausgeführt, und die Daten werden als `XmlReader`-Objekt abgerufen, wobei die Dateiinhalte an die Konsole ausgegeben werden.  
  
 [!code-csharp[Adomd.NetClient#OutputDataWithXML](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#outputdatawithxml)]  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Daten aus einer analytischen Datenquelle](retrieving-data-from-an-analytical-data-source.md)   
 [Abrufen von Daten mittels CellSet](retrieving-data-using-the-cellset.md)   
 [Abrufen von Daten mittels AdomdDataReader](retrieving-data-using-the-adomddatareader.md)  
  
  