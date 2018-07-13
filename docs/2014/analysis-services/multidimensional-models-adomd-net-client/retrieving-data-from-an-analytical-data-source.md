---
title: Abrufen von Daten aus einer analytischen Datenquelle | Microsoft-Dokumentation
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
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4e5595bd4e001b006cb1dfe62cba40cee3bbb30c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196420"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Abrufen von Daten von einer analytischen Datenquelle
  Sobald Sie eine Verbindung herstellen und die Abfrage erstellen, können Sie alle Daten abrufen. In ADOMD.NET können Sie Daten über drei Objekte abfragen (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> und <xref:System.Xml.XmlReader>), indem Sie eine der `Execute`-Methoden des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>-Objekts aufrufen.  
  
 Jedes dieser drei Objekte stellt ein Gleichgewicht zwischen Interaktivität und Aufwand her:  
  
-   *Interaktivität* bezieht sich auf die einfache bedienbarkeit und die Menge an Informationen über das Objektmodell zur Verfügung.  
  
-   *Aufwand* bezieht sich auf die Menge des Datenverkehrs, der ein Objektmodell generiert wird, über die Netzwerkverbindung mit dem Server, die Menge des benötigten Arbeitsspeichers für das Objektmodell und die Geschwindigkeit, mit dem das Objektmodell Daten abruft.  
  
 Um Sie bei der Auswahl des Datenabrufobjekts, das am geeignetsten für die Anforderungen Ihrer Anwendung ist, zu unterstützen, stellt die folgende Tabelle die Unterschiede zwischen Interaktivität und Aufwand für jedes Objekt heraus.  
  
|Objekt|Interaktivität|Aufwand|Behält Dimensionalität bei|Informationen zur Verwendung|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Am höchsten|Mittelhoch, führt zum langsamsten Datenabruf|ja|[Abrufen von Daten mit dem Cellset](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Moderieren|Moderieren|nein|[Auffüllen eines Datasets mit einen "DataAdapter"](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Moderieren|Moderieren|nein|[Abrufen von Daten mittels AdomdDataReader](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Am niedrigsten|Am niedrigsten, was zum schnellsten Datenabruf führt|ja|[Abrufen von Daten mittels XmlReader](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ADOMD.NET-Clientprogrammierung](adomd-net-client-programming.md)  
  
  
