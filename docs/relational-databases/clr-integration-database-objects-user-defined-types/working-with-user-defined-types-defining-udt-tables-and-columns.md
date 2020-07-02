---
title: Definieren von UDT-Tabellen und-Spalten | Microsoft-Dokumentation
description: Nachdem Sie die Assembly, die eine UDT-Definition enthält, registriert haben, können Sie Sie in einer Spaltendefinition verwenden.
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fc857b99772983d925504357f641f89780fdd67
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727766"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Arbeiten mit benutzerdefinierten Typen: Definieren von UDT-Tabellen und -Spalten
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Nachdem die Assembly, die die UDT-Definition (User-Defined Type, benutzerdefinierter Typ) enthält, in einer-Datenbank registriert wurde [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , kann Sie in einer Spaltendefinition verwendet werden. Weitere Informationen finden Sie unter [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
## <a name="creating-tables-with-udts"></a>Erstellen von Tabellen mit UDTs  
 Es gibt keine spezielle Syntax für das Erstellen einer UDT-Spalte in einer Tabelle. Sie können den Namen des UDT in einer Spaltendefinition verwenden, als wäre er einer der systeminternen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die folgende CREATE TABLE- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung erstellt eine Tabelle mit dem Namen " **Points**" mit einer Spalte mit dem Namen " **ID",** die als **int** -Identitäts Spalte und Primärschlüssel für die Tabelle definiert ist. Die zweite Spalte hat den Namen **PointValue**und den Datentyp **Point**. Der in diesem Beispiel verwendete Schema Name lautet **dbo**. Beachten Sie, dass Sie über die erforderlichen Berechtigungen verfügen müssen, um einen Schemanamen anzugeben. Wenn Sie den Schemanamen nicht angeben, wird das Standardschema für den Datenbankbenutzer verwendet.  
  
```sql  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Erstellen von Indizes für UDT-Spalten  
 Es gibt zwei Optionen für das Indizieren einer UDT-Spalte:  
  
-   **Indizieren Sie den vollständigen Wert.** In diesem Fall, wenn der UDT binär sortiert ist, können Sie einen Index über die gesamte UDT-Spalte mithilfe der CREATE INDEX-[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erstellen.  
  
-   **Indizieren Sie UDT-Ausdrücke.** Sie können Indizes auf persistenten berechneten Spalten über UDT-Ausdrücken erstellen. Der UDT-Ausdruck kann ein Feld, eine Methode oder eine Eigenschaft eines UDT sein. Der Ausdruck muss deterministisch sein und darf keinen Datenzugriff ausführen.  
  
 Weitere Informationen finden Sie unter [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit benutzerdefinierten Typen in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)     
 [Create Type (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)     
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)     
