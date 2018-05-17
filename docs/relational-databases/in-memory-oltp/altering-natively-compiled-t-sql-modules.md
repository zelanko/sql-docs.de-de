---
title: Ändern von systemintern kompilierten T-SQL-Modulen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e1be524afd73d1486d2a5e3904c69275cd4c89db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="altering-natively-compiled-t-sql-modules"></a>Ändern von nativ kompilierten T-SQL-Modulen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], können Sie mithilfe der `ALTER`-Anweisung `ALTER`-Vorgänge für nativ kompilierte gespeicherte Prozeduren und weitere nativ kompilierte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Module ausführen, etwa skalare benutzerdefinierte Funktionen und Trigger.  
  
Bei der Ausführung von `ALTER` für ein nativ kompiliertes [!INCLUDE[tsql](../../includes/tsql-md.md)]-Modul wird das Modul mit einer neuen Definition neu kompiliert. Während der Neukompilierung steht die alte Version des Moduls nach wie vor noch für die Ausführung zur Verfügung. Nach Abschluss der Kompilierung werden die Modulausführungen entladen und die neue Version des Moduls wird installiert. Bei der Änderung eines nativ kompilierten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Moduls können die folgenden Optionen geändert werden.  
  
-   Parameter  
-   EXECUTE AS  
-   TRANSACTION ISOLATION LEVEL  
-   LANGUAGE  
-   DATEFIRST  
-   DATEFORMAT  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
> Nativ kompilierte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Module können nicht in nicht-nativ kompilierte Module konvertiert werden. Nicht-nativ kompilierte T-SQL-Module können nicht in nativ kompilierte Module konvertiert werden.  
  
Weitere Informationen zu `ALTER PROCEDURE`-Funktionen und deren Syntax finden Sie unter [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md).  
  
Sie können [sp_recompile](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md) für ein nativ kompiliertes [!INCLUDE[tsql](../../includes/tsql-md.md)]-Modul ausführen, wodurch das Modul bei der nächsten Ausführung erneut kompiliert.  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt die Erstellung einer speicheroptimierten Tabelle (T1) und einer systemintern kompilierten gespeicherten Prozedur (ups_1), die alle Spalten von Tabelle T1 auswählt. Anschließend wird usp_1 geändert, um die Klausel `EXECUTE AS` zu entfernen, `LANGUAGE` zu ändern und nur eine Spalte (C1) von T1 auszuwählen.  
  
```sql  
CREATE TABLE [dbo].[T1] (  
  [c1] [int] NOT NULL,  
  [c2] [float] NOT NULL,  
  CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
  ) WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
   SELECT c1, c2 FROM dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
   SELECT c1 FROM dbo.T1  
END  
GO    
```   
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Systemintern kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)    
