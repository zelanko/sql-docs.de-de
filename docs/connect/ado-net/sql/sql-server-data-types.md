---
title: SQL Server-Datentypen und ADO.NET
description: Beschreibt das Arbeiten mit SQL Server-Datentypen und deren Interaktion mit .NET-Datentypen.
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 12ad13d6788ae2b8995289100883b06c5ab6d7c6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452035"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server-Datentypen und ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server und .NET basieren auf unterschiedlichen Typsystemen, was zu einem möglichen Datenverlust führen kann. Um die Datenintegrität beizubehalten, stellt die Microsoft SqlClient-Datenanbieter für SQL Server (<xref:Microsoft.Data.SqlClient>) typisierte Accessormethoden zum Arbeiten mit SQL Server Daten bereit. Sie können die-Enumerationen in den <xref:System.Data.SqlDbType>-Klassen verwenden, um <xref:Microsoft.Data.SqlClient.SqlParameter> Datentypen anzugeben.  
  
In SQL Server 2008 werden neue Datentypen eingeführt, die für geschäftliche Anforderungen zum Arbeiten mit Datums-und uhrzeitanforderungen, strukturierten, semistrukturierten und unstrukturierten Daten entworfen wurden. Diese sind in der SQL Server 2008-Onlinedokumentation dokumentiert.  
  
Die SQL Server Datentypen, die für die Verwendung in Ihrer Anwendung verfügbar sind, hängt von der verwendeten Version von SQL Server ab. Weitere Informationen finden Sie unter [Datentypen (Datenbank-Engine)](https://go.microsoft.com/fwlink/?LinkID=107468) aus SQL Server-Onlinedokumentation.
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[SqlTypes und das DataSet](sqltypes-dataset.md)  
Beschreibt die neue Typunterstützung für `SqlTypes` im `DataSet`.  
  
[Behandlung von NULL-Werten](handle-null-values.md)  
Veranschaulicht die Arbeit mit NULL-Werten und dreiwertigen Logik.  
  
[Vergleichen von GUID- und uniqueidentifier-Werten](compare-guid-uniqueidentifier-values.md)  
Veranschaulicht das Arbeiten mit GUID-und uniqueidentifier-Werten in SQL Server und .net.  
  
[Datums- und Zeitdaten](date-time-data.md)  
Beschreibt, wie die neuen Datums-und Uhrzeit Datentypen verwendet werden, die in SQL Server 2008 eingeführt wurden.  
  
[Große UDTs](large-udts.md)  
Veranschaulicht das Abrufen von Daten aus großen Wert-UDTs, die in SQL Server 2008 eingeführt wurden.  
  
[XML-Daten in SQL Server](xml-data-sql-server.md)  
Beschreibt das Arbeiten mit XML-Daten, die aus SQL Server abgerufen werden.  
  
## <a name="reference"></a>Verweis  
<xref:System.Data.DataSet>  
Beschreibt die `DataSet` Klasse und alle Member.  
  
<xref:System.Data.SqlTypes>  
Beschreibt die `SqlTypes`-Namespace und alle zugehörigen Member.  
  
<xref:System.Data.SqlDbType>  
Beschreibt die `SqlDbType` Enumeration und alle zugehörigen Member.  
  
<xref:System.Data.DbType>  
Beschreibt die `DbType` Enumeration und alle zugehörigen Member.  
  
## <a name="next-steps"></a>Nächste Schritte
- [Tabellenwertparameter](table-valued-parameters.md)
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
