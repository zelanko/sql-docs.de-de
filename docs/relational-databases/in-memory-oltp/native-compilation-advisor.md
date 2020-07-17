---
title: Ratgeber für native Kompilierung | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie den Ratgeber für native Kompilierung nutzen, um eine interpretierte gespeicherte Prozedur im Rahmen der Migration zu In-Memory OLTP zur nativen Kompilierung migrieren.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql13.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e31863944670cbb6e32e999ec06164792848236a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722447"
---
# <a name="native-compilation-advisor"></a>Ratgeber für native Kompilierung
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Berichte zur Transaktionsleistungsanalyse informieren Sie darüber, welche interpretierten gespeicherten Prozeduren in der Datenbank von einer Portierung zur nativen Kompilierung profitieren. Details finden Sie unter [Bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur zu In-Memory OLTP portiert werden soll](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md).  
  
 Nachdem Sie eine gespeicherte Prozedur identifiziert haben, die Sie zur Verwendung der nativen Kompilierung portieren möchten, können Sie den Ratgeber für native Kompilierung verwenden, um die Migration der interpretierten gespeicherten Prozedur zur nativen Kompilierung zu vereinfachen. Weitere Informationen zu systemintern kompilierten gespeicherten Prozeduren finden Sie unter [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
 In einer bestimmten interpretierten gespeicherten Prozedur können Sie mit dem Ratgeber für native Kompilierung alle Features identifizieren, die in nativen Modulen nicht unterstützt werden. Der Ratgeber für native Kompilierung bietet Links zu Problemumgehungen oder Lösungen an.  
  
 Weitere Informationen zu Migrationsmethoden finden Sie unter [In-Memory OLTP - Common Workload Patterns and Migration Considerations (In-Memory-OLTP: Allgemeine Workloadmuster und Überlegungen zur Migration)](https://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>Exemplarische Vorgehensweise: Ratgeber für native Kompilierung  
 Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die gespeicherte Prozedur, die Sie konvertieren möchten, und wählen Sie **Ratgeber für native Kompilierung**aus. Daraufhin wird die Willkommensseite für **Ratgeber für die native Kompilierung gespeicherter Prozeduren**angezeigt. Klicken Sie auf zum Fortfahren auf **Weiter**.  
  
### <a name="stored-procedure-validation"></a>Überprüfung der gespeicherten Prozedur  
 Auf dieser Seite wird angezeigt, ob die gespeicherte Prozedur Konstrukte verwendet, die mit der nativen Kompilierung nicht kompatibel sind. Klicken Sie auf **Weiter** , um weitere Details anzuzeigen. Wenn Konstrukte vorhanden sind, die nicht mit der nativen Kompilierung kompatibel sind, können Sie durch Klicken auf **Weiter** zusätzliche Details abrufen.  
  
### <a name="stored-procedure-validation-result"></a>Überprüfungsergebnis der gespeicherten Prozedur  
 Wenn Konstrukte vorhanden sind, die nicht mit der nativen Kompilierung kompatibel sind, werden auf der Seite **Überprüfungsergebnis der gespeicherten Prozedur** detaillierte Informationen angezeigt. Sie können (durch Klicken auf **Bericht generieren**) einen Bericht generieren, den **Ratgeber für native Kompilierung**beenden und den Code aktualisieren, sodass er mit der nativen Kompilierung kompatibel ist.  
  
## <a name="code-sample"></a>Codebeispiel  
 Im folgenden Beispiel werden eine interpretierte gespeicherte Prozedur und die *äquivalente* gespeicherte Prozedur für die native Kompilierung erläutert. Das in diesem Beispiel verwendete Verzeichnis ist c:\data.  
  
> [!NOTE]  
>  Wie üblich gelten das **FILEGROUP** -Element und die **USE** MyDatabase-Anweisung für Microsoft SQL Server, jedoch nicht für die Azure SQL-Datenbank.  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
go  
  
USE Demo;  
go  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
     CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
) WITH ( BUCKET_COUNT = 2097152)  
) WITH ( MEMORY_OPTIMIZED = ON )  
go  
  
-- Interpreted.  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  INSERT dbo.SalesOrders VALUES (@id, @date, @status);  
END  
go  
  
-- Natively Compiled.  
CREATE PROCEDURE [dbo].[InsertOrderXTP]  
      @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
     (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
     )  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status);  
END  
go  
  
SELECT * from SalesOrders;  
go  
  
EXECUTE dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1;  
EXECUTE dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2;  
  
SELECT * from SalesOrders;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)   
 [Anforderungen für die Verwendung speicheroptimierter Tabellen](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)  
  
  
