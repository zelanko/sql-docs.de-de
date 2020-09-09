---
title: sys. sp_rda_reconcile_indexes (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie mehr über sys. sp_rda_reconcile_indexes. Weitere Informationen finden Sie unter Verwenden dieser gespeicherten Transact-SQL-Prozedur zum Abgleichen von Indizes in einer Remote Tabelle.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2d224f5ea2b20f684fdd9e484304639114fd2d2e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544671"
---
# <a name="syssp_rda_reconcile_indexes-transact-sql"></a>sys. sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

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
  
  
