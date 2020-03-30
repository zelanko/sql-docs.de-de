---
title: SQL Server-Datentypen und ADO.NET
description: Beschreibt das Arbeiten mit SQL Server-Datentypen und deren Interaktion mit .NET-Datentypen.
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 50a6e158f5678b30028337b70e1da6914038e64a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896542"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server-Datentypen und ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server und .NET basieren auf unterschiedlichen Typsystemen. Dies kann zu Datenverlust führen. Um Datenintegrität sicherzustellen, bietet der Microsoft SqlClient-Datenanbieter für SQL Server (<xref:Microsoft.Data.SqlClient>) typisierte Accessormethoden für die Arbeit mit SQL Server-Daten. Sie können die Enumerationen in den <xref:System.Data.SqlDbType>-Klassen verwenden, um <xref:Microsoft.Data.SqlClient.SqlParameter>-Datentypen anzugeben.  
  
In SQL Server 2008 werden neue Datentypen eingeführt, um geschäftliche Anforderungen zu erfüllen. Diese Datentypen ermöglichen die Arbeit mit Datums- und Uhrzeitangaben sowie mit strukturierten, teilweise strukturierten und unstrukturierten Daten. Diese sind in der SQL Server 2008-Onlinedokumentation dokumentiert.  
  
Welche SQL Server-Datentypen in Ihrer Anwendung verwendet werden können, hängt von Ihrer SQL Server-Version ab. Weitere Informationen finden Sie unter [Datentypen (Datenbankmodul)](https://go.microsoft.com/fwlink/?LinkID=107468) in der SQL Server-Onlinedokumentation.
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[SqlTypes und das DataSet](sqltypes-dataset.md)  
Beschreibt die neue Typunterstützung für `SqlTypes` im `DataSet`.  
  
[Behandlung von NULL-Werten](handle-null-values.md)  
Veranschaulicht, wie Sie mit NULL-Werten und dreiwertiger Logik arbeiten.  
  
[Vergleichen von GUID- und uniqueidentifier-Werten](compare-guid-uniqueidentifier-values.md)  
Veranschaulicht, wie Sie mit GUID- und uniqueidentifier-Werten in SQL Server und .NET arbeiten.  
  
[Datums- und Zeitdaten](date-time-data.md)  
Beschreibt die Verwendung der neuen Datums- und Uhrzeitdatentypen ab SQL Server 2008.  
  
[Große UDTs](large-udts.md)  
Veranschaulicht, wie Sie Daten aus UDTs mit großen Werten abrufen, die mit SQL Server 2008 eingeführt wurden.  
  
[XML-Daten in SQL Server](xml-data-sql-server.md)  
Beschreibt, wie Sie mit XML-Daten arbeiten, die aus SQL Server abgerufen wurden.  
  
## <a name="reference"></a>Verweis  
<xref:System.Data.DataSet>  
Beschreibt die `DataSet`-Klasse und alle ihre Member.  
  
<xref:System.Data.SqlTypes>  
Beschreibt den `SqlTypes`-Namespace und alle seine Member.  
  
<xref:System.Data.SqlDbType>  
Beschreibt die `SqlDbType`-Enumeration und alle ihre Member.  
  
<xref:System.Data.DbType>  
Beschreibt die `DbType`-Enumeration und alle ihre Member.  
  
## <a name="next-steps"></a>Nächste Schritte
- [Tabellenwertparameter](table-valued-parameters.md)
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
