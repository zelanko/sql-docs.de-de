---
title: Aufbauen von Verbindungen in ADOMD.NET | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a338d1902440fe6489b7c4c91176899999aa25fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172020"
---
# <a name="establishing-connections-in-adomdnet"></a>Aufbauen von Verbindungen in ADOMD.NET
  In ADOMD.NET verwenden Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> Objekt, das Öffnen von Verbindungen mit analytischen Datenquellen, wie z. B. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbanken. Wenn die Verbindung nicht mehr benötigt wird, sollten Sie die Verbindung explizit schließen.  
  
## <a name="opening-a-connection"></a>Öffnen einer Verbindung  
 Um eine Verbindung in ADOMD.NET zu öffnen, müssen Sie zunächst eine Verbindungszeichenfolge zu einer gültigen analytischen Datenquelle und Datenbank angeben. Dann müssen Sie die Verbindung explizit für diese Datenquelle öffnen.  
  
### <a name="specifying-a-multidimensional-data-source"></a>Angeben einer mehrdimensionalen Datenquelle  
 Um eine analytische Datenquelle und eine Datenbank anzugeben, legen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>-Eigenschaft des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts fest. Die für die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>-Eigenschaft angegebene Verbindungszeichenfolge ist eine OLE DB-kompatible Zeichenfolge. ADOMD.NET verwendet die angegebene Verbindungszeichenfolge, um zu bestimmen, wie eine Verbindung mit dem Server hergestellt wird.  
  
 Die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>-Eigenschaft kann entweder für ein bestehendes <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt oder während der Erstellung einer Instanz eines <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts gesetzt werden. Der folgende Code veranschaulicht, wie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>-Eigenschaft beim Erstellen einer ADOMD-Verbindung festgelegt wird:  
  
```vb  
Dim advwrksConnection As New AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS")  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString)  
```  
  
```csharp  
AdomdConnection advwrksConnection = new AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS");  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString);  
```  
  
### <a name="opening-a-connection-to-the-data-source"></a>Öffnen einer Verbindung zur Datenquelle  
 Nachdem Sie die Verbindungszeichenfolge angegeben haben, müssen Sie die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A>-Methode verwenden, um die Verbindung zu öffnen. Wenn Sie ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt öffnen, können Sie verschiedene Sicherheitsstufen für die Verbindung festlegen. Die Sicherheitsstufe, die für die Verbindung verwendet wird, hängt vom Wert der Einstellung der `ProtectionLevel`-Verbindungszeichenfolge ab. Weitere Informationen über das Öffnen von sicherer Verbindungen in ADOMD.NET finden Sie unter [Establishing Secure Connections in ADOMD.NET](connections-in-adomd-net-establishing-secure-connections.md).  
  
## <a name="working-with-a-connection"></a>Arbeiten mit einer Verbindung  
 Jede geöffnete Verbindung besteht in einer Sitzung, die zustandsbehaftete Vorgänge unterstützt. Eine Sitzung kann für mehr als eine geöffnete Verbindung freigegeben werden. Durch die Freigabe einer Sitzung können mehrere Clients den gleichen Kontext nutzen. Weitere Informationen finden Sie unter [arbeiten mit Verbindungen und Sitzungen in ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
 Sie können eine geöffnete Verbindung verwenden, um Metadaten, Daten und Ausführungsbefehle abzurufen. Weitere Informationen finden Sie unter [Abrufen von Metadaten aus einer analytischen Datenquelle](retrieving-metadata-from-an-analytical-data-source.md), [Abrufen von Daten aus einer analytischen Datenquelle](retrieving-data-from-an-analytical-data-source.md), und [Ausführen von Befehlen für eine analytische Daten Quelle](executing-commands-against-an-analytical-data-source.md).  
  
 Bei geöffneter Verbindung können Sie Daten und Metadaten abrufen und Befehle aus einer Transaktion ausführen, bei der ein Commit vor dem Lesevorgang ausgeführt werden muss, wobei während des Lesens der Daten eine Sperre aufrechterhalten wird, um Dirty Reads zu verhindern. Die Daten können auch vor dem Ende der Transaktion noch geändert werden, was zu nicht wiederholbaren Lesevorgängen oder Phantomdaten führt. Weitere Informationen finden Sie unter [Durchführen von Transaktionen in ADOMD.NET](../../relational-databases/native-client-ole-db-transactions/transactions.md).  
  
## <a name="closing-a-connection"></a>Trennen einer Verbindung  
 Wir empfehlen, dass Sie ein <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt explizit schließen, sobald Sie die Verbindung nicht mehr benötigen. Um die Verbindung explizit zu schließen, können Sie die Methoden `Close` und `Dispose` des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts nutzen.  
  
 Eine Verbindung, die nicht explizit geschlossen wird, sondern bei der zugelassen wird, dass sie den Bereich verlässt, gibt möglicherweise Serverressourcen nicht schnell genug frei, damit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Clientanwendungen mit hoher Parallelität neue Verbindungen effizient öffnen können. Je nachdem, wie Sie die Verbindung erstellt haben, kann die Sitzung, die vom <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt verwendet wird, aktiv bleiben, wenn die Verbindung nicht explizit geschlossen wird.  
  
 Weitere Informationen zu Sitzungen finden Sie unter [arbeiten mit Verbindungen und Sitzungen in ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
> [!IMPORTANT]  
>  Rufen Sie in der `Finalize`-Methode einer jeglichen implementierten Klasse nicht die Methoden `Close` oder `Dispose` eines <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>-Objekts oder eines jeglichen anderen verwalteten Objekts auf. Geben Sie in einem Finalizer nur die nicht verwalteten Ressourcen frei, die direkt der implementierten Klasse angehören. Wenn die implementierte Klasse keine nicht verwalteten Ressourcen besitzt, nehmen Sie keine `Finalize`-Methode in die Klassendefinition auf.  
  
## <a name="see-also"></a>Siehe auch  
 [ADOMD.NET-Clientprogrammierung](adomd-net-client-programming.md)  
  
  
