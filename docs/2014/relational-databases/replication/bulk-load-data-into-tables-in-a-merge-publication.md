---
title: Massenladen von Daten in Tabellen in einer Mergeveröffentlichung (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 09e535057fcf573dfa189b7e5fdc0e0df06e5d4a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721762"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a>Massenladen von Daten in Tabellen in einer Mergeveröffentlichung (Replikationsprogrammierung mit Transact-SQL)
  Beim Laden von Daten in Tabellen unter Berücksichtigung der Informationen in [bcp Utility](../../tools/bcp-utility.md) oder mithilfe des [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) -Befehls werden die Mergereplikationstrigger, die die internen Überwachungsdaten in der [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) -Systemtabelle verwalten, standardmäßig nicht ausgelöst. Sie haben die Möglichkeit, das Auslösen der Mergereplikationstrigger beim Laden der Daten zu erzwingen, oder Sie können die generierten Replikationsmetadaten programmgesteuert nach dem Massenkopiervorgang mithilfe gespeicherter Replikationsprozeduren einfügen.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>So können Sie mit dem Hilfsprogramm "bcp" Daten per Massenladevorgang in mithilfe der Mergereplikation veröffentlichte Tabellen laden  
  
1.  Führen Sie auf dem Verleger oder dem Abonnenten das Hilfsprogramm [bcp Utility](../../tools/bcp-utility.md) oder [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) aus, um Daten in eine mithilfe der Mergereplikation veröffentlichte Tabelle einzufügen.  
  
2.  Verwenden Sie eine der folgenden Methoden, um sicherzustellen, dass die Replikationsmetadaten für die eingefügten Daten generiert werden.  
  
    -   Führen Sie den Massenkopiervorgang mithilfe der FIRE_TRIGGERS-Option aus.  
  
    -   Führen Sie in der Datenbank, in die Daten eingefügt wurden, [sp_addtabletocontents (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql) aus. Geben Sie den Namen der Tabelle an, in die die Daten für **@table_name** aus.  
  
  
