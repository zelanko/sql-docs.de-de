---
title: SQL-XML-Spaltenwerte
description: Demonstriert das Abrufen von XLM-Daten aus SQL Server und das Arbeiten mit diesen Daten.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2704ceae26c58edc85b0cbc1f0fbe6cc98f64311
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902001"
---
# <a name="sql-xml-column-values"></a>SQL-XML-Spaltenwerte

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server unterstützt den `xml`-Datentyp. Daher können Entwickler Resultsets, die diesen Typ einschließen, mithilfe des Standardverhaltens der <xref:Microsoft.Data.SqlClient.SqlCommand>-Klasse abrufen. Eine `xml`-Spalte kann wie jede andere Spalte abgerufen werden (beispielsweise in eine <xref:Microsoft.Data.SqlClient.SqlDataReader>-Instanz), wenn Sie den Inhalt der Spalte jedoch als XML verwenden möchten, müssen Sie <xref:System.Xml.XmlReader> verwenden.  
  
## <a name="example"></a>Beispiel  
Die folgende Konsolenanwendung ruft zwei Zeilen mit jeweils einer `xml`-Spalte aus der **Sales.Store**-Tabelle in der **AdventureWorks**-Datenbank ab und übermittelt sie an eine <xref:Microsoft.Data.SqlClient.SqlDataReader>-Instanz. Für jede Zeile wird der Wert der `xml`-Spalte mithilfe der <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A>-Methode von <xref:Microsoft.Data.SqlClient.SqlDataReader> gelesen. Der Wert wird in einer <xref:System.Xml.XmlReader>-Instanz gespeichert. Beachten Sie, dass Sie <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> anstelle der <xref:System.Data.IDataRecord.GetValue%2A>-Methode verwenden müssen, wenn Sie eine <xref:System.Data.SqlTypes.SqlXml>-Variable als Inhalt festlegen möchten. <xref:System.Data.IDataRecord.GetValue%2A> gibt den Wert der `xml`-Spalte als Zeichenfolge zurück.  
  
> [!NOTE]
>  Beim Installieren von SQL Server wird die Beispieldatenbank **AdventureWorks** in der Standardeinstellung nicht installiert. Sie kann jedoch mithilfe von SQL Server-Setup installiert werden.  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Nächste Schritte
- <xref:System.Data.SqlTypes.SqlXml>
- [XML-Daten in SQL Server](xml-data-sql-server.md)
