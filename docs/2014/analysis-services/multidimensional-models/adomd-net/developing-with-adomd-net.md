---
title: Entwickeln mit ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET
ms.assetid: abaf33aa-db55-43bf-8f30-15547559be1d
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1dfdd10ae488633812b61e2a0220f7c22e65e575
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061264"
---
# <a name="developing-with-adomdnet"></a>Entwickeln mit ADOMD.NET
  ADOMD.NET ist ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework-Datenanbieter, die entwickelt wurde, für die Kommunikation mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. ADOMD.NET verwendet das XML for Analysis-Protokoll für die Kommunikation mit analytischen Datenquellen, indem entweder TCP/IP- oder HTTP-Verbindungen für die Übertragung oder den Empfang von SOAP-Anforderungen oder -Antworten eingesetzt werden, die mit der XML for Analysis-Spezifikation kompatibel sind. Befehle können in Multidimensional Expressions (MDX), Data Mining Extensions (DMX), Analysis Services Scripting Language (ASSL) oder gar einer eingeschränkten SQL-Syntax gesendet werden und geben möglicherweise kein Ergebnis zurück. Analytische Daten, Key Performance Indicators (KPIs) und Miningmodelle können über das ADOMD.NET-Objektmodell abgefragt und geändert werden. Über ADOMD.NET können Sie darüber hinaus Metadaten einsehen oder mit diesen arbeiten, indem entweder OLE DB-konforme Schemarowsets abgerufen werden oder das ADOMD.NET-Objektmodell verwendet wird.  
  
 Der ADOMD.NET-Datenanbieter wird dargestellt, indem die `Microsoft.AnalysisServices.AdomdClient` Namespace.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[ADOMD.NET-Clientprogrammierung](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|Beschreibt, wie ADOMD.NET-Clientobjekte verwendet werden, um Daten und Metadaten von analytischen Datenquellen abzurufen.|  
|[ADOMD.NET-Serverprogrammierung](../../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|Beschreibt, wie ADOMD.NET-Serverobjekte verwendet werden, um gespeicherte Prozeduren und benutzerdefinierte Funktionen zu erstellen.|  
|[Neuverteilen von ADOMD.NET](redistributing-adomd-net.md)|Beschreibt den Prozess der Neuverteilung von ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|Listet die Objekte, die in enthaltenen der `Microsoft.AnalysisServices.AdomdClient` Namespace.|  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrdimensionale Ausdrücke &#40;MDX&#41; Verweis](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Datamining-Erweiterungen &#40;DMX&#41; Verweis](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Analysis Services-Schemarowsets](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Datenzugriff auf mehrdimensionale Modelle &#40;Analysis Services – mehrdimensionale Daten&#41;](../mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
