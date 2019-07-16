---
title: sp_rda_set_query_mode (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b1450dc8304c2e8d3db5a6fa8b2153f951e70bde
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083613"
---
# <a name="syssprdasetquerymode-transact-sql"></a>sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt an, ob Abfragen an der aktuellen aktivierter Funktion Stretch-Datenbank und die Tabellen sowohl lokale als auch Daten (Standard) oder nur lokale Daten zurückgeben.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @mode = ] *@mode*  
 Ist eine der folgenden Werte.  
  
-   **Deaktivierte** alle Abfragen für Stretch-aktivierte Tabellen fehl.  
  
-   **LOCAL_ONLY** Abfragen für Stretch-aktivierte Tabellen geben nur lokale Daten zurück.  
  
-   **LOCAL_AND_REMOTE** Abfragen für Stretch-aktivierte Tabellen geben sowohl lokale als auch Daten zurück. Dies ist das Standardverhalten.  
  
 [ @force = ]  *@force*  
 Ist ein optionaler Bitwert, den Sie auf 1 festlegen können, wenn Sie Abfragemodus ohne Überprüfung ändern möchten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder > 0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden erweiterten gespeicherten Prozeduren legen auch den Abfragemodus für eine Stretch-aktivierten Datenbank.  
  
-   **sp_rda_deauthorize_db**  
  
     Nach der Ausführung **Sp_rda_deauthorize_db** , alle Abfragen für Stretch-fähigen Datenbanken und Tabellen fehl. Die Query-Modus festgelegt ist, also deaktiviert. Um diesen Modus beenden, gehen Sie die folgenden Schritte.  
  
    -   Führen Sie [Sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) eine Verbindung mit Azure-Remotedatenbank herzustellen. Dieser Vorgang wird automatisch zurückgesetzt, den Abfragemodus zu LOCAL_AND_REMOTE, dies ist das Standardverhalten für Stretch Database. D.h., geben Abfragen Ergebnisse aus lokalen und Remotedaten zurück.  
  
    -   Führen Sie [sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) mit dem Argument "LOCAL_ONLY" Abfragen, die weiterhin für nur lokale Daten ausführen können.  
  
-   **sp_rda_reauthorize_db**  
  
     Beim Ausführen von [Sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) um erneut eine Verbindung mit der Azure-Remotedatenbank herzustellen, setzt diesen Vorgang automatisch den Abfragemodus auf LOCAL_AND_REMOTE, die das Standardverhalten ist für Stretch Database. D.h., geben Abfragen Ergebnisse aus lokalen und Remotedaten zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
