---
title: sp_rda_reconcile_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe05d88b6453bd9918b5777b3f52291ec9fefc2c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087942"
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gleicht im Azure-Remotetabelle Spalten den Spalten in der Stretch-aktivierten SQL Server-Tabelle.  
    
  **Sp_rda_reconcile_columns** fügt Spalten hinzu, an die Remotetabelle, die in der Stretch-aktivierten SQL Server-Tabelle, aber nicht in der Remotetabelle vorhanden sind. Diese Spalten möglicherweise Spalten, die Sie versehentlich aus der Remotetabelle gelöscht. Allerdings **Sp_rda_reconcile_columns** löscht keine Spalten aus der Remotetabelle, die in der Remotetabelle, aber nicht in der SQL Server-Tabelle vorhanden sind.
  
  > [!IMPORTANT]
  > Wenn **sp_rda_reconcile_columns** Spalten neu erstellt, die Sie versehentlich aus der Remotetabelle gelöscht haben, dann werden nicht die zuvor in den gelöschten Spalten enthaltenen Daten wiederhergestellt.
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argumente  
 \@Objname = '*\@Objname*"  
 Der Name des Stretch-aktivierten SQL Server-Tabelle.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  
   
## <a name="remarks"></a>Hinweise  
 Wenn Spalten in der Azure-Remotetabelle enthalten sind, die in der Stretch-aktivierten SQL Server-Tabelle nicht mehr vorhanden sind, dann verhindern diese zusätzlichen Spalten nicht, dass Stretch Database ordnungsgemäß arbeitet. Sie können die zusätzlichen Spalten optional manuell entfernen.  
  
## <a name="example"></a>Beispiel  
 Abstimmen, die die Spalten in der Azure-Remotetabelle, die folgende Anweisung ausführen.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
