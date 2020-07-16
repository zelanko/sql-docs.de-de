---
title: SESSION_ID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
author: VanMSFT
ms.author: vanto
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ce5ba2ef3b5bcb3849a710744bfb8de701b418c3
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196826"
---
# <a name="session_id-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Gibt die ID der aktuellen [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]- oder [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)]-Sitzung zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen **nvarchar(32)** -Wert zurück.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Die Sitzungs-ID wird jeder Benutzerverbindung beim Herstellen der Verbindung zugewiesen und bleibt für die Dauer der Verbindung bestehen. Wenn die Verbindung beendet wird, wird die Sitzungs-ID freigegeben.  
  
 Die Sitzungs-ID beginnt mit den Buchstaben „SID“. Für diese muss die Groß-/Kleinschreibung beachtet werden. Außerdem müssen sie groß geschrieben werden, wenn die Sitzungs-ID in [!INCLUDE[DWsql](../../includes/dwsql-md.md)]-Befehlen verwendet wird.  
  
 Sie können die Sicht [sys.dm_pdw_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) abfragen, um dieselben Informationen wie diese Funktion abzurufen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die ID der aktuellen Sitzung zurückgegeben.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION &#40;SQL Data Warehouse&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
