---
title: Massenkopiervorgänge in SQL Server
description: Beschreibt die Massenkopierfunktionen für den .NET-Datenanbieter für SQL Server.
ms.date: 09/30/2019
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 70eed483eb7cb857e23b110b7149badff14ab46f
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452290"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Massenkopiervorgänge in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Microsoft SQL Server enthält ein beliebtes Befehlszeilen-Hilfsprogramm mit dem Namen **bcp** zum schnellen Massenkopieren großer Dateiumfänge in Tabellen oder Ansichten in SQL Server-Datenbanken. Die <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse ermöglicht es Ihnen, Lösungen für verwalteten Code zu schreiben, die eine ähnliche Funktionalität bereitstellen. Es gibt eine Reihe weiterer Verfahren, Daten in eine SQL-Server-Tabelle zu laden (beispielsweise INSERT-Anweisungen), doch bietet <xref:Microsoft.Data.SqlClient.SqlBulkCopy> ihnen gegenüber einen erheblichen Leistungsvorteil.  
  
Mit der <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse können Sie Folgendes ausführen:  
  
- Einen einzelnen Massenkopiervorgang  
  
- Mehrere Massenkopiervorgänge  
  
- Einen Massenkopiervorgang innerhalb einer Transaktion  
  
> [!NOTE]
>  Wenn Sie .NET Framework, Version 1.1 oder früher, verwenden (bei diesen Versionen wird die <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse nicht unterstützt), können Sie die **BULK INSERT**-Anweisung von Transact-SQL für SQL Server mit dem <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt ausführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Einrichten des Massenkopierbeispiels](bulk-copy-example-setup.md)  
Beschreibt die Tabellen, die in den Massen Kopier Beispielen verwendet werden, und stellt SQL-Skripts zum Erstellen der Tabellen in der AdventureWorks-Datenbank bereit.  
  
[Einzelne Massenkopiervorgänge](single-bulk-copy-operations.md)  
Beschreibt das Ausführen eines einzelnen Massen Kopierens von Daten in eine Instanz von SQL Server mithilfe der <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse und das Ausführen des Massen Kopiervorgangs mithilfe von Transact-SQL-Anweisungen und der <xref:Microsoft.Data.SqlClient.SqlCommand>-Klasse.  
  
[Mehrere Massenkopiervorgänge](multiple-bulk-copy-operations.md)  
Beschreibt das Ausführen mehrerer Massen Kopiervorgänge von Daten in eine Instanz von SQL Server mithilfe der <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse.  
  
[Transaktionen und Massenkopiervorgänge](transaction-bulk-copy-operations.md)  
Beschreibt, wie ein Massen Kopiervorgang innerhalb einer Transaktion ausgeführt wird, einschließlich des Commits oder Rollbacks der Transaktion.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
