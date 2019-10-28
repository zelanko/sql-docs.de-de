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
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d8dc9d5100f71fed39c1e4166882230451dd139e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451932"
---
# <a name="sql-xml-column-values"></a>SQL-XML-Spaltenwerte

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server unterstützt den `xml`-Datentyp. Daher können Entwickler Resultsets, die diesen Typ einschließen, mithilfe des Standardverhaltens der <xref:Microsoft.Data.SqlClient.SqlCommand>-Klasse abrufen. Eine `xml` Spalte kann genauso wie jede beliebige Spalte abgerufen werden (z. b. in eine <xref:Microsoft.Data.SqlClient.SqlDataReader>). Wenn Sie jedoch mit dem Inhalt der Spalte als XML arbeiten möchten, müssen Sie einen <xref:System.Xml.XmlReader> verwenden.  
  
## <a name="example"></a>Beispiel  
Die folgende Konsolenanwendung ruft zwei Zeilen mit jeweils einer `xml`-Spalte aus der **Sales.Store**-Tabelle in der **AdventureWorks**-Datenbank ab und übermittelt sie an eine <xref:Microsoft.Data.SqlClient.SqlDataReader>-Instanz. Für jede Zeile wird der Wert der Spalte `xml` mithilfe der <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A>-Methode von <xref:Microsoft.Data.SqlClient.SqlDataReader> gelesen. Der Wert wird in einem <xref:System.Xml.XmlReader> gespeichert. Beachten Sie, dass Sie anstelle der <xref:System.Data.IDataRecord.GetValue%2A>-Methode <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> verwenden müssen, wenn Sie den Inhalt auf eine <xref:System.Data.SqlTypes.SqlXml> Variable festlegen möchten.  <xref:System.Data.IDataRecord.GetValue%2A> gibt den Wert der `xml` Spalte als Zeichenfolge zurück.  
  
> [!NOTE]
>  Beim Installieren von SQL Server wird die Beispieldatenbank **AdventureWorks** in der Standardeinstellung nicht installiert. Sie können Sie installieren, indem Sie SQL Server-Setup ausführen.  
  
[!code-csharp[DataWorks SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Nächste Schritte
- <xref:System.Data.SqlTypes.SqlXml>
- [XML-Daten in SQL Server](xml-data-sql-server.md)
