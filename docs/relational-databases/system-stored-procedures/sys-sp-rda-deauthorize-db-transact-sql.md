---
title: Sys. sp_rda_deauthorize_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5d9497400cd555d3d9ce9d216ba5dd393b1d76ce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608408"
---
# <a name="syssprdadeauthorizedb-transact-sql"></a>Sys. sp_rda_deauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Entfernt die authentifizierte Verbindung zwischen einer lokalen Stretch-aktivierte Datenbank und Azure-Remotedatenbank an. Führen Sie **Sp_rda_deauthorize_db** Wenn die remote-Datenbank ist nicht erreichbar ist oder in einem inkonsistenten Zustand und Verhalten der Abfrage für alle Stretch-aktivierte Tabellen in der Datenbank ändern möchten.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  
  
## <a name="remarks"></a>Hinweise  
 Nach der Ausführung **Sp_rda_deauthorize_db** , alle Abfragen für Stretch-fähigen Datenbanken und Tabellen fehl. Die Query-Modus festgelegt ist, also deaktiviert. Um diesen Modus beenden, gehen Sie die folgenden Schritte.  
  
-   Führen Sie [Sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) eine Verbindung mit Azure-Remotedatenbank herzustellen. Dieser Vorgang wird automatisch zurückgesetzt, den Abfragemodus zu LOCAL_AND_REMOTE, dies ist das Standardverhalten für Stretch Database. D.h., geben Abfragen Ergebnisse aus lokalen und Remotedaten zurück.  
  
-   Führen Sie [sp_rda_set_query_mode &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) mit dem Argument "LOCAL_ONLY" Abfragen, die weiterhin für nur lokale Daten ausführen können.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sp_rda_set_query_mode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
