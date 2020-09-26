---
description: '&#x40;&#x40;TOTAL_READ (Transact-SQL)'
title: '@@TOTAL_READ (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_READ_TSQL'
- '@@TOTAL_READ'
dev_langs:
- TSQL
helpviewer_keywords:
- number of disk reads
- disks [SQL Server], number of disk reads
- '@@TOTAL_READ function'
- total read [SQL Server]
- read activity since last started
ms.assetid: b505fbe9-9569-4f3d-80b9-b64b5109ac98
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 7f31072dc67bb72fcbf484d74d697594425c1256
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379545"
---
# <a name="x40x40total_read-transact-sql"></a>&#x40;&#x40;TOTAL_READ (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Anzahl der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seit dem letzten Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführten Lesezugriffe auf den Datenträger, nicht auf den Cache, zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
@@TOTAL_READ  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 **integer**  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie einen Bericht anzeigen möchten, der mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Statistiken enthält (einschließlich Lese- und Schreibaktivitäten), führen Sie **sp_monitor** aus.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Rückgabe der Gesamtanzahl von Lese- und Schreibzugriffen auf den Datenträger bis zum aktuellen Datum und der aktuellen Uhrzeit angezeigt.  
  
```sql
SELECT @@TOTAL_READ AS 'Reads', @@TOTAL_WRITE AS 'Writes', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Reads       Writes      As of                   
----------- ----------- ----------------------  
7760        97263       12/5/2006 10:23:00 PM   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [System Statistical Functions &#40;Transact-SQL&#41; (Statistische Systemfunktionen (Transact-SQL))](../../t-sql/functions/system-statistical-functions-transact-sql.md)   
 [@@TOTAL_WRITE &#40;Transact-SQL&#41;](../../t-sql/functions/total-write-transact-sql.md)  
  
  
