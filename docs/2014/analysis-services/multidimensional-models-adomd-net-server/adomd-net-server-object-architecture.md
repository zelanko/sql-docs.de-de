---
title: ADOMD.NET-Server Objekt Architektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33a8f420f985c9e62c7d7f275e7de370a6988e8d
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469055"
---
# <a name="adomdnet-server-object-architecture"></a>ADOMD.NET-Serverobjektarchitektur
  Die ADOMD.NET-Server Objekte sind Hilfsobjekte, die zum Erstellen von benutzerdefinierten Funktionen (UDFs) oder gespeicherten Prozeduren in verwendet werden können [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
> [!NOTE]  
>  Um den `Microsoft.AnalysisServices.AdomdServer`-Namespace (und diese Objekte) verwenden zu können, muss eine Referenz auf msmgdsrv.dll zum Projekt der benutzerdefinierten Funktion oder der gespeicherten Prozedur hinzugefügt werden.  
  
 ![Zeigt die Objektbeziehungen im ADOMD.NET-Server](../../analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "Zeigt die Objektbeziehungen im ADOMD.NET-Server")  
ADOMD.NET-Objektmodell  
  
 Die Interaktion mit der ADOMD.NET-Objekthierarchie beginnt normalerweise mit einem oder mehreren der Objekte auf der obersten Ebene, wie in der folgenden Tabelle erläutert.  
  
|To|Verwenden Sie dieses Objekt|  
|--------|---------------------|  
|Auswerten von MDX-Ausdrücken (Multidimensional Expressions)|[Microsoft. AnalysisServices. AdomdServer. Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))<br /> Das [Microsoft. AnalysisServices. AdomdServer. Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) -Objekt bietet eine Möglichkeit, einen MDX-Ausdruck auszuführen und diesen Ausdruck unter einem angegebenen Tupel auszuwerten.|  
|Bereitstellen von Unterstützung für die Ausführung von MDX-Funktionen ohne Erstellung der vollständigen MDX-Anweisung|[Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))<br /> Das [Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) -Objekt ist praktisch zum Aufrufen von vordefinierten MDX-Funktionen, ohne das [Microsoft. AnalysisServices. AdomdServer. Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) -Objekt zu verwenden. Zusätzliche Funktionen für das [Microsoft. AnalysisServices. AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) -Objekt sollten in zukünftigen Versionen verfügbar sein.|  
|Darstellen des aktuellen Ausführungskontexts für die UDF|[Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))<br /> Das [Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) -Objekt macht Informationen verfügbar, wie z. b. den aktuellen Cube oder das Mining Modell und verschiedene Metadatenauflistungen. Ein wichtiger Verwendungszweck des [Microsoft. AnalysisServices. AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) -Objekts ist die [Microsoft. AnalysisServices. AdomdServer. Hierarchy. CurrentMember *](/previous-versions/sql/sql-server-2014/ms137044(v=sql.120)) -Eigenschaft des [Microsoft. AnalysisServices. AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120)) -Objekts. Diese Schlüsselverwendung ermöglicht dem Autor der UDF oder der gespeicherten Prozedur, Entscheidungen auf der Grundlage des Elements einer bestimmten Dimension zu treffen, auf das sich die Abfrage bezieht.|  
|Erstellen von Sätzen und Tupeln|[Microsoft. AnalysisServices. AdomdServer. SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)), [Microsoft. AnalysisServices. AdomdServer. TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))<br /> [Microsoft. AnalysisServices. AdomdServer. SetBuilder](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)) bietet eine Möglichkeit, unveränderliche Sätze zu erstellen, während [Microsoft. AnalysisServices. AdomdServer. TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120)) eine Möglichkeit bietet, unveränderliche Tupel zu erstellen.|  
|Unterstützung von impliziter Konvertierung und Umwandlung unter den sechs grundlegenden Typen der MDX-Sprache|[Microsoft. AnalysisServices. AdomdServer. MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))<br /> Das [Microsoft. AnalysisServices. AdomdServer. MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120)) -Objekt bietet implizite Konvertierung und Umwandlung zwischen den folgenden Typen:<br /><br /> -   [Microsoft. AnalysisServices. AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Level](/previous-versions/sql/sql-server-2014/ms143581(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Member](/previous-versions/sql/sql-server-2014/ms143820(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Tupel](/previous-versions/sql/sql-server-2014/ms145330(v=sql.120))<br />-   [Microsoft. AnalysisServices. AdomdServer. Set](/previous-versions/sql/sql-server-2014/ms144530(v=sql.120))<br />Skalare oder Werttypen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADOMD.NET-Serverprogrammierung](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
