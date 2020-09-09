---
description: sys.sp_cdc_enable_db (Transact-SQL)
title: sys. sp_cdc_enable_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_enable_db_TSQL
- sp_cdc_enable_db
- sys.sp_cdc_enable_db
- sys.sp_cdc_enable_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_enable_db
- change data capture [SQL Server], enabling databases
- sp_cdc_enable_db
ms.assetid: 176d83b3-493d-43cd-800e-aa123c3bdf17
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c40d3904737c7740c3658eda12e2f9c9df340b0a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534717"
---
# <a name="syssp_cdc_enable_db-transact-sql"></a>sys.sp_cdc_enable_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Aktiviert Change Data Capture für die aktuelle Datenbank. Diese Prozedur muss für eine Datenbank ausgeführt werden, bevor Tabellen in dieser Datenbank für Change Data Capture aktiviert werden können. Change Data Capture zeichnet an aktivierten Tabellen vorgenommene Einfüge-, Update- und Löschvorgänge auf und stellt Informationen zu den einzelnen Änderungen in einem leicht verarbeitbaren relationalen Format dar. Für die geänderten Zeilen werden Spaltendaten, die die Spaltenstruktur der nachverfolgten Quelltabelle widerspiegeln, sowie die Metadaten aufgezeichnet, die zur Anwendung der Änderungen in einer Zielumgebung erforderlich sind.  
  
> [!IMPORTANT]
>  Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_enable_db  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Change Data Capture kann nicht für [System Datenbanken](../../relational-databases/databases/system-databases.md) oder Verteilungs Datenbanken aktiviert werden.  
  
 sys.sp_cdc_enable_db erstellt die Change Data Capture-Objekte, deren Bereich datenbankweit ist, einschließlich von Metatabellen und DDL-Triggern. Außerdem erstellt er das CDC-Schema und den CDC-Datenbankbenutzer und legt die is_cdc_enabled Spalte für den Datenbankeintrag in der [sys. Database](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) -Katalog Sicht auf 1 fest.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird Change Data Capture aktiviert.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_db;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. sp_cdc_disable_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)  
  
  
