---
title: Arbeiten mit Schemarowsets in ADOMD.NET | Microsoft Docs
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
- metadata [ADOMD.NET]
- retrieving metadata
- schema rowsets [ADOMD.NET]
ms.assetid: 7bf75bf8-f1e1-44f6-ac42-c38a681654cf
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9c6acc3ffe3a0f0b7ae5523833cbb85f0c152cc5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148717"
---
# <a name="working-with-schema-rowsets-in-adomdnet"></a>Arbeiten mit Schemarowsets in ADOMD.NET
  Wenn Sie mehr als die im ADOMD.NET-Objektmodell vorhandenen Metadaten benötigen, bietet ADOMD.NET die Möglichkeit, den vollständigen Bereich für XMLA-(XML for Analysis-), OLE DB-, OLE DB für OLAP- und OLE DB für Data Mining-Schemarowsets abzurufen:  
  
 **XML for Analysis-Metadaten**  
 Die XML for Analysis-Schemarowsets stellen eine Methode zum Abrufen von Informationen über den Server auf niedriger Ebene bereit. Zu den verfügbaren Informationen gehören die auf dem Server vorhandenen Datenquellen, die durch den Anbieter reservierten Schlüsselwörter, die vom Anbieter unterstützten Literale und vieles mehr. Sie können ein XML for Analysis-Schemarowset verwenden, um alle Schemarowsets zu ermitteln, die vom Anbieter unterstützt werden.  
  
 Weitere Informationen: [XML for Analysis-Schemarowsets](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 **OLE DB-Metadaten**  
 Die OLE DB-Schemarowsets stellen eine Methode nach Industriestandard für das Abrufen von Informationen von diversen Anbietern bereit.  
  
 Weitere Informationen: [OLE DB-Schemarowsets](../schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
 **OLAP-Metadaten**  
 Zu den Schemainformationen, die für eine analytische Datenquelle bereitgestellt werden, gehören die über die analytische Datenquelle verfügbaren Datenbanken und Kataloge, Cubes und Miningmodelle in einer Datenbank, für Cubes in der Datenbank bestehende Rollen und vieles mehr.  
  
 Weitere Informationen: [OLE DB für OLAP-Schemarowsets](../schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
 **Datamining-Metadaten**  
 Zusätzlich zu OLAP-Metadaten können Data Mining-Metadaten mittels Schemarowsets abgerufen werden. Die verfügbaren Rowsets machen Informationen über die verfügbaren Data Mining-Modelle in der Datenbank, die verfügbaren Mining-Algorithmen, die für den Algorithmus erforderlichen Parameter, Miningstrukturen und vieles mehr verfügbar.  
  
 Weitere Informationen: [Data Mining-Schemarowsets](../schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
 Für jeden dieser verschiedenen Schemarowsets rufen Sie Metadaten vom Rowset durch die Übergabe eines GUID oder XMLA-Namens mit der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>-Methode des <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>-Objekts ab.  
  
## <a name="retrieving-metadata-by-passing-guids"></a>Abrufen von Metadaten durch Übergabe von GUIDS  
 Die <xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid> Klasse enthält eine Liste von Feldern, die die Schemarowsets, die am häufigsten von Anbietern und analytischen Datenquellen unterstützt darstellen. Um sowohl allgemeine als auch anbieterspezifische Metadaten von einem Anbieter oder einer analytischen Datenquelle abzurufen, verwenden Sie die GUIDs, die als Bestandteil der <xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid> Objekt mit einer der folgenden Methoden:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
> [!NOTE]  
>  Der ADOMD.NET-Datenanbieter macht Schemainformationen über eine Funktionalität verfügbar, die Ihr spezifischer Anbieter und die analytische Datenquelle bereitstellen. Jeder Anbieter und jede Datenquelle stellen möglicherweise andere Metadaten bereit.  
  
## <a name="retrieving-metadata-by-passing-xmla-names"></a>Abrufen von Metadaten durch Übergabe von XMLA-Namen  
 Die folgenden Methoden nutzen als Argumente den XMLA-Schemanamen, der identifiziert, welche Schemainformationen zurückzugeben sind, und einen Array von Einschränkungen in diesen zurückgegebenen Spalten:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
 Jede dieser Methoden gibt eine Instanz von einem `DataSet` -Objekt, das mit den Schemainformationen aufgefüllt wird. Das `DataSet`-Objekt stammt aus dem `System.Data`-Namespace der Microsoft .NET Framework-Klassenbibliothek.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Funktion GetActions nimmt eine Verbindung, den Cubenamen, eine Koordinate und einen Koordinatentyp, ruft eine [MDSCHEMA_ACTIONS-Rowsets](../schema-rowsets/ole-db-olap/mdschema-actions-rowset.md), und gibt die verfügbaren Aktionen auf der ausgewählten Koordinate.  
  
 [!code-csharp[Adomd.NetClient#GetActions](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#getactions)]  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen von Metadaten aus einer analytischen Datenquelle](retrieving-metadata-from-an-analytical-data-source.md)  
  
  