---
description: sp_db_vardecimal_storage_format (Transact-SQL)
title: sp_db_vardecimal_storage_format (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_vardecimal_storage_format
- sp_db_vardecimal_storage_format_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_vardecimal_storage_format
- decimal data type, compressing
- compressing decimal data
- numeric data type, compressing
- database compression [SQL Server]
- table compression [SQL Server]
ms.assetid: 9920b2f7-b802-4003-913c-978c17ae4542
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4c521931a96701101c7db2eac8027dc0223b53f3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543559"
---
# <a name="sp_db_vardecimal_storage_format-transact-sql"></a>sp_db_vardecimal_storage_format (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den aktuellen vardecimal-Speicherformatstatus einer Datenbank zurück oder aktiviert das vardecimal-Speicherformat für eine Datenbank.  Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sind Benutzerdatenbanken immer aktiviert. Datenbanken müssen nur in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] für das vardecimal-Speicherformat aktiviert werden.  
  
> [!IMPORTANT]  
>  Durch Ändern des vardecimal-Speicherformatstatus einer Datenbank können Sicherung und Wiederherstellung, Datenbankspiegelung, sp_attach_db, Protokollversand sowie die Replikation beeinflusst werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_db_vardecimal_storage_format [ [ @dbname = ] 'database_name']   
    [ , [ @vardecimal_storage_format = ] { 'ON' | 'OFF' } ]   
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @dbname =] '*database_name*'  
 Der Name der Datenbank, für die das Speicherformat geändert werden soll. *database_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn der Datenbankname ausgelassen wird, wird der vardecimal-Speicherformatstatus aller Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegeben.  
  
 [ @vardecimal_storage_format =] {' On ' | ' Aus "}"  
 Gibt an, ob das vardecimal-Speicherformat aktiviert ist. @vardecimal_storage_format kann ON oder OFF sein. Der-Parameter ist vom Datentyp **varchar (3)** und hat keinen Standardwert. Wenn ein Datenbankname angegeben ist, @vardecimal_storage_format jedoch ausgelassen wird, wird die aktuelle Einstellung der angegebenen Datenbank zurückgegeben. Dieses Argument hat keine Auswirkungen auf [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder höhere Versionen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn das Datenbankspeicherformat nicht geändert werden kann, wird von sp_db_vardecimal_storage_format ein Fehler zurückgegeben. Wenn sich die Datenbank bereits im angegebenen Zustand befindet, bleibt die gespeicherte Prozedur ohne Wirkung.  
  
 Wenn das @vardecimal_storage_format -Argument nicht angegeben wird, gibt den Spaltendaten Banknamen und den vardecimal-Status zurück.  
  
## <a name="remarks"></a>Hinweise  
 sp_db_vardecimal_storage_format gibt den vardecimal-Status zurück, kann den vardecimal-Status aber nicht ändern.  
  
 Unter den folgenden Umständen treten für sp_db_vardecimal_storage_format Fehler auf:  
  
-   In der Datenbank sind aktive Benutzer vorhanden.  
  
-   Für die Datenbank sind Spiegelungen aktiviert.  
  
-   In der Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird das vardecimal-Speicherformat nicht unterstützt.  
  
 Wenn der vardecimal-Speicherformatstatus in OFF geändert werden soll, muss eine Datenbank auf den einfachen Wiederherstellungsmodus festgelegt werden. Wenn eine Datenbank auf den einfachen Wiederherstellungsmodus festgelegt ist, wird die Protokollkette unterbrochen. Führen Sie eine vollständige Datenbanksicherung aus, nachdem Sie den vardecimal-Speicherformatstatus auf OFF festgelegt haben.  
  
 Der Status kann nicht in OFF geändert werden, wenn für einige Tabellen die vardecimal-Datenbankkomprimierung verwendet wird. Verwenden Sie [sp_tableoption](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md), um das Speicherformat einer Tabelle zu ändern. Wenn Sie bestimmen möchten, für welche Tabellen in einer Datenbank das vardecimal-Speicherformat verwendet wird, verwenden Sie die `OBJECTPROPERTY`-Funktion, und suchen Sie nach der `TableHasVarDecimalStorageFormat`-Eigenschaft, wie im folgenden Beispiel veranschaulicht.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT name, object_id, type_desc  
FROM sys.objects   
 WHERE OBJECTPROPERTY(object_id,   
   N'TableHasVarDecimalStorageFormat') = 1 ;  
GO  
```  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Code werden die Komprimierung in der `AdventureWorks2012`-Datenbank aktiviert, der Status bestätigt und anschließend die Spalten decimal und numeric in der `Sales.SalesOrderDetail`-Tabelle komprimiert.  
  
```  
USE master ;  
GO  
  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON' ;  
GO  
  
-- Check the vardecimal storage format state for  
-- all databases in the instance.  
EXEC sp_db_vardecimal_storage_format ;  
GO  
  
USE AdventureWorks2012 ;  
GO  
  
EXEC sp_tableoption 'Sales.SalesOrderDetail', 'vardecimal storage format', 1 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
