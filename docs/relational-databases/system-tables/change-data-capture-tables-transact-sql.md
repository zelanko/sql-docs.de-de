---
title: Change Data Capture-Tabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e98c770db0f1fc9c89275fc973a2bdee8ee4508f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825939"
---
# <a name="change-data-capture-tables-transact-sql"></a>Change Data Capture-Tabellen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Change Data Capture ermöglicht eine Änderungsnachverfolgung für Tabellen, sodass DML (Data Manipulation Language)- und DDL (Data Definition Language)-Änderungen an den Tabellen inkrementell in ein Data Warehouse geladen werden können. In den Themen in diesem Abschnitt werden die Systemtabellen beschrieben, in denen die von Change Data Capture-Vorgängen verwendeten Informationen gespeichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [capture_instance>_CT CDC. <](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
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
  
 [dbo. cdc_jobs &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 Gibt die Konfigurationsparameter für Change Data Capture-Agentaufträge zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für Change Data Capture &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Change Data Capture-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
