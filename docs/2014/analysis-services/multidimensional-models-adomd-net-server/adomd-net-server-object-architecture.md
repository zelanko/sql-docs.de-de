---
title: ADOMD.NET-serverobjektarchitektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05aee754db65811d450fb06e0e433cb4b207c372
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145625"
---
# <a name="adomdnet-server-object-architecture"></a>ADOMD.NET-Serverobjektarchitektur
  Die ADOMD.NET-Serverobjekte sind Hilfsobjekte, die verwendet werden können, zum Erstellen von benutzerdefinierten Funktionen (UDFs) oder gespeicherte Prozeduren in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Um den `Microsoft.AnalysisServices.AdomdServer`-Namespace (und diese Objekte) verwenden zu können, muss eine Referenz auf msmgdsrv.dll zum Projekt der benutzerdefinierten Funktion oder der gespeicherten Prozedur hinzugefügt werden.  
  
 ![Zeigt die objektbeziehungen im ADOMD.NET-Server](../../../2014/analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "zeigt die objektbeziehungen im ADOMD.NET-Server")  
ADOMD.NET-Objektmodell  
  
 Die Interaktion mit der ADOMD.NET-Objekthierarchie beginnt normalerweise mit einem oder mehreren der Objekte auf der obersten Ebene, wie in der folgenden Tabelle erläutert.  
  
|Aktion|Verwenden Sie dieses Objekt|  
|--------|---------------------|  
|Auswerten von MDX-Ausdrücken (Multidimensional Expressions)|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> Das <xref:Microsoft.AnalysisServices.AdomdServer.Expression>-Objekt stellt eine Möglichkeit bereit, einen MDX-Ausdruck auszuführen und diesen Ausdruck unter einem bestimmten Tupel auszuwerten.|  
|Bereitstellen von Unterstützung für die Ausführung von MDX-Funktionen ohne Erstellung der vollständigen MDX-Anweisung|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> Das <xref:Microsoft.AnalysisServices.AdomdServer.MDX>-Objekt ist zweckmäßig für den Aufruf von vordefinierten MDX-Funktionen ohne die Verwendung des <xref:Microsoft.AnalysisServices.AdomdServer.Expression>-Objekts. Weitere Funktionen für das <xref:Microsoft.AnalysisServices.AdomdServer.MDX>-Objekt werden voraussichtlich in zukünftigen Versionen verfügbar sein.|  
|Darstellen des aktuellen Ausführungskontexts für die UDF|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> Das <xref:Microsoft.AnalysisServices.AdomdServer.Context>-Objekt macht Informationen verfügbar wie den aktuellen Cube oder das Miningmodell sowie zahlreiche Metadatensammlungen. Eine Schlüsselverwendung des <xref:Microsoft.AnalysisServices.AdomdServer.Context>-Objekts ist die <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A>-Eigenschaft des <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>-Objekts. Diese Schlüsselverwendung ermöglicht dem Autor der UDF oder der gespeicherten Prozedur, Entscheidungen auf der Grundlage des Elements einer bestimmten Dimension zu treffen, auf das sich die Abfrage bezieht.|  
|Erstellen von Sätzen und Tupeln|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> bietet eine Möglichkeit, unveränderliche Sätze zu erstellen, und <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> bietet eine Möglichkeit, unveränderliche Tupel zu erstellen.|  
|Unterstützung von impliziter Konvertierung und Umwandlung unter den sechs grundlegenden Typen der MDX-Sprache|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> Das <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue>-Objekt ermöglicht implizite Konvertierung und Umwandlung unter den folgenden Typen:<br /><br /> -   <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Level><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Member><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Set><br />-Skalar, oder Werttypen|  
  
## <a name="see-also"></a>Siehe auch  
 [ADOMD.NET-Serverprogrammierung](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
