---
title: Definieren von UDT-Tabellen und-Spalten | Microsoft-Dokumentation
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
ms.openlocfilehash: 8386da85d22f50b45492ecd52588e6d06fe80590
ms.sourcegitcommit: 0d34b654f0b3031041959e87f5b4d4f0a1af6a29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2019
ms.locfileid: "74901953"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Arbeiten mit benutzerdefinierten Typen: Definieren von UDT-Tabellen und -Spalten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Nachdem die Assembly, die die UDT-Definition (User-Defined Type, benutzerdefinierter Typ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) enthält, in einer-Datenbank registriert wurde, kann Sie in einer Spaltendefinition verwendet werden. Weitere Informationen finden Sie unter [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
## <a name="creating-tables-with-udts"></a>Erstellen von Tabellen mit UDTs  
 Es gibt keine spezielle Syntax für das Erstellen einer UDT-Spalte in einer Tabelle. Sie können den Namen des UDT in einer Spaltendefinition verwenden, als wäre er einer der systeminternen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die folgende CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung erstellt eine Tabelle mit dem Namen " **Points**" mit einer Spalte mit dem Namen " **ID",** die als **int** -Identitäts Spalte und Primärschlüssel für die Tabelle definiert ist. Die zweite Spalte hat den Namen **PointValue**und den Datentyp **Point**. Der in diesem Beispiel verwendete Schema Name lautet **dbo**. Beachten Sie, dass Sie über die erforderlichen Berechtigungen verfügen müssen, um einen Schemanamen anzugeben. Wenn Sie den Schemanamen nicht angeben, wird das Standardschema für den Datenbankbenutzer verwendet.  
  
```sql  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Erstellen von Indizes für UDT-Spalten  
 Es gibt zwei Optionen für das Indizieren einer UDT-Spalte:  
  
-   **Indizieren Sie den vollständigen Wert.** In diesem Fall, wenn der UDT binär sortiert ist, können Sie einen Index über die gesamte UDT-Spalte mithilfe der CREATE INDEX-[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erstellen.  
  
-   **Indizieren Sie UDT-Ausdrücke.** Sie können Indizes auf persistenten berechneten Spalten über UDT-Ausdrücken erstellen. Der UDT-Ausdruck kann ein Feld, eine Methode oder eine Eigenschaft eines UDT sein. Der Ausdruck muss deterministisch sein und darf keinen Datenzugriff ausführen.  
  
 Weitere Informationen finden Sie unter [Create Index &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit benutzerdefinierten Typen in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)     
 [Create Type (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)     
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)     
