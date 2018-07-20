---
title: Ändern von Data-Capture-Tabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a07c68784114879d99127cac19725481be42de2a
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101488"
---
# <a name="change-data-capture-tables-transact-sql"></a>Change Data Capture-Tabellen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Change Data Capture ermöglicht eine Änderungsnachverfolgung für Tabellen, sodass DML (Data Manipulation Language)- und DDL (Data Definition Language)-Änderungen an den Tabellen inkrementell in ein Data Warehouse geladen werden können. In den Themen in diesem Abschnitt werden die Systemtabellen beschrieben, in denen die von Change Data Capture-Vorgängen verwendeten Informationen gespeichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [cdc.<capture_instance>_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
 Gibt eine Zeile für jede Änderung an einer aufgezeichneten Spalte in der zugeordneten Quelltabelle zurück.  
  
 [cdc.captured_columns](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
 Gibt eine Zeile für jede in einer Aufzeichnungsinstanz nachverfolgte Spalte zurück.  
  
 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
 Gibt eine Zeile pro Änderungstabelle in der Datenbank zurück.  
  
 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)  
 Gibt eine Zeile für jede Änderung an der Datendefinitionssprache (DDL) zurück, die an Tabellen vorgenommen wurde, die für Change Data Capture aktiviert wurden.  
  
 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)  
 Gibt eine Zeile für jede Transaktion zurück, für die Zeilen in einer Änderungstabelle aufgezeichnet sind. Diese Tabelle wird verwendet, um die Commitwerte der Protokollfolgenummer (Log Sequence Number, LSN) mit dem Commitzeitpunkt der Transaktion zu verknüpfen.  
  
 [cdc.index_columns](../../relational-databases/system-tables/cdc-index-columns-transact-sql.md)  
 Gibt eine Zeile für jede Indexspalte zurück, die einer Änderungstabelle zugeordnet ist.  
  
 [cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 Gibt die Konfigurationsparameter für Change Data Capture-Agentaufträge zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Change Data Capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Ändern Sie die Data Capture-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
