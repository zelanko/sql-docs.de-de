---
title: Arbeiten mit dem ADOMD.NET-Objektmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 46a34a3885d0db0f80fd683e2cec74b68d26797c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156540"
---
# <a name="working-with-the-adomdnet-object-model"></a>Arbeiten mit dem ADOMD.NET-Objektmodell
  ADOMD.NET bietet ein Objektmodell zum Anzeigen der Cubes und untergeordneten Objekte, die in einer analytischen Datenquelle enthalten sind. Jedoch sind nicht alle Metadaten für eine bestimmte analytische Datenquelle über das Objektmodell verfügbar. Das Objektmodell bietet nur Zugriff auf die Informationen, die von einer Clientanwendung am sinnvollsten angezeigt werden können, damit ein Benutzer interaktiv Befehle erstellen kann. Aufgrund der geringeren Komplexität der darzustellenden Metadaten ist das ADOMD.NET-Objektmodell einfacher zu verwenden.  
  
 Beim ADOMD.NET-Objektmodell bietet das <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt Zugriff auf Informationen in den Cubes und Miningmodellen der analytischen Onlineverarbeitung (OLAP), die in einer analytischen Datenquelle definiert sind, sowie zugehörige Objekte wie Dimensionen, benannte Mengen und Mining-Algorithmen.  
  
## <a name="retrieving-olap-metadata"></a>Abrufen von OLAP-Metadaten  
 Jedes <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt enthält eine Auflistung von <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>-Objekten, die dem Benutzer oder der Anwendung verfügbare Cubes darstellen. Das <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>-Objekt macht Informationen über den Cube sowie verschiedene, dem Cube zugehörige Objekte verfügbar, wie zum Beispiel Dimensionen, Key Performance Indicators, Measures, benannte Mengen usw.  
  
 Sie sollten nach Möglichkeit das <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>-Objekt verwenden, um Metadaten in Clientanwendungen darzustellen, die mehrere OLAP-Server unterstützen sollen; dies gilt ebenfalls für allgemeine Zwecke des Anzeigens und Abrufens von Metadaten.  
  
> [!NOTE]  
>  Bei anbieterspezifischen Metadaten oder für die Anzeige oder den Abruf detaillierter Metadaten sollten Sie Metadaten mithilfe von Schemarowsets abrufen. Weitere Informationen finden Sie unter [arbeiten mit Schemarowsets in ADOMD.NET](retrieving-metadata-working-with-schema-rowsets.md)).  
  
 Im folgenden Beispiel wird das <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef>-Objekt verwendet, um die sichtbaren Cubes und die zugehörigen Dimensionen vom lokalen Server abzurufen.  
  
 [!code-csharp[Adomd.NetClient#RetrieveCubesAndDimensions](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#retrievecubesanddimensions)]  
  
## <a name="retrieving-data-mining-metadata"></a>Abrufen von Data Mining-Metadaten  
 Jedes <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekt besitzt mehrere Auflistungen, die Informationen über die Data Mining-Fähigkeiten der Datenquelle bereitstellen:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> enthält eine Liste aller Miningmodelle in der Datenquelle.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> stellt Informationen über die verfügbaren Mining-Algorithmen bereit.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> macht Informationen über die Mining-Strukturen auf dem Server verfügbar.  
  
 Um zu bestimmen, wie Sie eine Abfrage für ein Miningmodell auf dem Server durchführen, gehen Sie die <xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A>-Auflistung durch. Jedes <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn>-Objekt macht folgende Merkmale verfügbar:  
  
-   Ob das Objekt eine Eingabespalte ist (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>).  
  
-   Ob das Objekt eine Vorhersagespalte ist (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>).  
  
-   Die einer diskreten Spalte (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>) zugeordneten Werte  
  
-   Die Art der Daten in der Spalte (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>).  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Metadaten aus einer analytischen Datenquelle](retrieving-metadata-from-an-analytical-data-source.md)  
  
  
