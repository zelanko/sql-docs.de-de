---
title: Massenkopiervorgänge in SQL Server
description: Beschreibt die Massenkopierfunktionen für den .NET-Datenanbieter für SQL Server.
ms.date: 09/30/2019
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 6ab832627f04825b5cdddc2939108fb427801bc7
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928911"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Massenkopiervorgänge in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server enthält ein beliebtes Befehlszeilen-Hilfsprogramm mit dem Namen **bcp** zum schnellen Massenkopieren großer Dateiumfänge in Tabellen oder Ansichten in SQL Server-Datenbanken. Die <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse ermöglicht Ihnen das Schreiben von verwalteten Codelösungen, die eine ähnliche Funktionalität bereitstellen. Es gibt eine Reihe weiterer Verfahren, Daten in eine SQL-Server-Tabelle zu laden (beispielsweise INSERT-Anweisungen), doch bietet <xref:Microsoft.Data.SqlClient.SqlBulkCopy> ihnen gegenüber einen erheblichen Leistungsvorteil.  
  
Die <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse bietet folgende Möglichkeiten:  
  
- Einen einzelnen Massenkopiervorgang  
  
- Mehrere Massenkopiervorgänge  
  
- Einen Massenkopiervorgang innerhalb einer Transaktion  
  
> [!NOTE]
>  Wenn Sie .NET Framework, Version 1.1 oder früher, verwenden (bei diesen Versionen wird die <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse nicht unterstützt), können Sie die **BULK INSERT**-Anweisung von Transact-SQL für SQL Server mit dem <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt ausführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Einrichten des Massenkopierbeispiels](bulk-copy-example-setup.md)  
In diesem Artikel werden die Tabellen beschrieben, die in den Beispielen für Massenkopiervorgänge verwendet werden, und SQL-Skripts zum Erstellen der Tabellen in der AdventureWorks-Datenbank werden bereitgestellt.  
  
[Einzelne Massenkopiervorgänge](single-bulk-copy-operations.md)  
In diesem Artikel wird das Durchführen einzelner Massenkopiervorgänge für Daten in eine SQL Server-Instanz mithilfe der <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse beschrieben und wie der Massenkopiervorgang mithilfe von Transact-SQL-Anweisungen und der <xref:Microsoft.Data.SqlClient.SqlCommand>-Klasse durchgeführt werden kann.  
  
[Mehrere Massenkopiervorgänge](multiple-bulk-copy-operations.md)  
Beschreibt das Ausführen mehrerer Massenkopiervorgänge von Daten in eine SQL Server-Instanz mithilfe der <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse  
  
[Transaktionen und Massenkopiervorgänge](transaction-bulk-copy-operations.md)  
Beschreibt das Ausführen eines Massenkopiervorgangs innerhalb einer Transaktion, einschließlich des Commits oder Rollbacks einer Transaktion  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
