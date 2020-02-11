---
title: CDC. lsn_time_mapping (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.lsn_time_mapping
- cdc.lsn_time_mapping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.lsn_time_mapping
ms.assetid: 1cb7aedc-48a4-486e-9b91-d30c4bd4084e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e89e67b49498320e4500b99332fc5584d5f38d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68066671"
---
# <a name="cdclsn_time_mapping-transact-sql"></a>cdc.lsn_time_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Transaktion zurück, für die Zeilen in einer Änderungstabelle aufgezeichnet sind. Diese Tabelle wird verwendet, um die Commitwerte der Protokollfolgenummer (Log Sequence Number, LSN) mit dem Commitzeitpunkt der Transaktion zu verknüpfen. Außerdem können Einträge protokolliert werden, für die keine Einträge in Änderungstabellen aufgezeichnet sind. Auf diese Weise kann die Tabelle den Abschluss der LSN-Verarbeitung in Phasen aufzeichnen, in denen wenige oder keine Änderungsaktivitäten stattfinden.  
  
 Es wird empfohlen, die Systemtabellen nicht direkt abzufragen. Führen Sie stattdessen die Systemfunktionen [sys. fn_cdc_map_lsn_to_time &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md) und [sys. fn_cdc_map_time_to_lsn &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md) aus.  
    
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**start_lsn**|**Binär (10)**|LSN der Transaktion, für die ein Commit ausgeführt wurde.|  
|**tran_begin_time**|**datetime**|Startzeit der Transaktion, die der LSN zugeordnet ist.|  
|**tran_end_time**|**datetime**|Zeitpunkt, zu dem die Transaktion beendet wurde.|  
|**tran_id**|**varbinary (10)**|ID der Transaktion.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Das Transaktionsprotokoll &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [CDC. &#60;capture_instance&#62;_CT &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
  
  
