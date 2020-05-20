---
title: sys. sp_rda_reconcile_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 504085ff53415a7cf84bdb4aabf5eff567391a0c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827399"
---
# <a name="syssp_rda_reconcile_indexes-transact-sql"></a>sys. sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Fügt eine Schema Aufgabe in die Warteschlange ein, um Indizes für die Remote Tabelle abzustimmen. Nachdem diese Aufgabe erfolgreich abgeschlossen wurde, verfügt die Remote Tabelle über dieselben Indizes, die in der lokalen Stretch-aktivierten Tabelle vorhanden sind.  
  
 Wenn eine andere Aufgabe in eine Warteschlange eingereiht ist, um Indizes beim Abrufen von **sp_rda_reconcile_indexes**abzugleichen, fügt diese gespeicherte Prozedur keinen doppelten Task in die Warteschlange ein.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>Argumente  
 [ @objname =] *' objname '*  
 Der qualifizierte oder nicht qualifizierte Name der Stretch-aktivierten Tabelle, für die Indizes abgeglichen werden sollen. Anführungszeichen sind nur erforderlich, wenn Sie ein qualifiziertes Objekt angeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
