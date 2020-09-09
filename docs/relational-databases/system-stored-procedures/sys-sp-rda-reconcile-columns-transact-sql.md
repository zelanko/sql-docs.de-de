---
title: sys. sp_rda_reconcile_columns (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie mehr über sys. sp_rda_reconcile_columns. Verwenden Sie diese gespeicherte Prozedur, um Spalten in Azure-Remote Tabellen und Stretch-aktivierten SQL Server Tabellen abzustimmen.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1788e373c8bab330182df9338e447946cda87bd3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538442"
---
# <a name="syssp_rda_reconcile_columns-transact-sql"></a>sys. sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Gibt die Spalten in der Azure-Remote Tabelle mit den Spalten in der Stretch-aktivierten SQL Server Tabelle aus.  
    
  **sp_rda_reconcile_columns** fügt der Remote Tabelle Spalten hinzu, die in der Stretch-aktivierten SQL Server Tabelle, jedoch nicht in der Remote Tabelle vorhanden sind. Diese Spalten können Spalten sein, die Sie versehentlich aus der Remote Tabelle gelöscht haben. Allerdings werden von **sp_rda_reconcile_columns** keine Spalten aus der Remote Tabelle gelöscht, die in der Remote Tabelle vorhanden sind, aber nicht in der SQL Server Tabelle enthalten sind.
  
  > [!IMPORTANT]
  > Wenn **sp_rda_reconcile_columns** Spalten neu erstellt, die Sie versehentlich aus der Remotetabelle gelöscht haben, dann werden nicht die zuvor in den gelöschten Spalten enthaltenen Daten wiederhergestellt.
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argumente  
 \@objname = '* \@ objname*'  
 Der Name der SQL Server Tabelle, für die Stretch aktiviert ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner Berechtigungen.  
   
## <a name="remarks"></a>Hinweise  
 Wenn die Azure-Remotetabelle Spalten enthält, die in der Stretch-fähigen SQL Server-Tabelle nicht mehr vorhanden sind, verhindern diese zusätzlichen Spalten nicht die normale Funktionsweise von Stretch Database. Sie können die zusätzlichen Spalten optional manuell entfernen.  
  
## <a name="example"></a>Beispiel  
 Führen Sie die folgende Anweisung aus, um die Spalten in der Azure-Remote Tabelle abzustimmen.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
