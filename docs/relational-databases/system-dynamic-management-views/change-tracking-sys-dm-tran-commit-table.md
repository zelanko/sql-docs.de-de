---
title: dm_tran_commit_table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_commit_table
- dm_tran_commit_table_TSQL
- sys.dm_tran_commit_table
- sys.dm_tran_commit_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_commit_table dynamic management view
ms.assetid: 732d23c5-1f6c-4e96-bc85-8f29b520cf0e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 33cd6bb98fe17121a3903a82566dded929af6c8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603769"
---
# <a name="change-tracking---sysdmtrancommittable"></a>"Änderungen nachverfolgen" - dm_tran_commit_table
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Zeigt eine Zeile für jede Transaktion, die ein Commit für eine Tabelle ausgeführt wird, die vom nachverfolgt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Änderungen nachverfolgen". Die verwaltungssicht dm_tran_commit_table, die aus Gründen der unterstützbarkeit bereitgestellt wird, und macht die transaktionsbezogenen Informationen, die nachverfolgung von Änderungen werden in der Systemtabelle sys.syscommittab speichert. Die Tabelle sys.syscommittab ermöglicht eine effiziente persistente Zuordnung zwischen einer datenbankspezifischen Transaktions-ID und den Commit-Protokollfolgenummern (Log Sequence Number, LSN) und den Commit-Timestamps der Transaktion. Die Daten, die in der sys.syscommittab-Tabelle gespeichert und in dieser verwaltungssicht verfügbar gemacht werden gemäß dem Cleanup gemäß der Beibehaltungsdauer angegeben, bei der änderungsnachverfolgung konfiguriert wurde.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_tran_commit_table**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|Eine monoton steigende Zahl, die als datenbankspezifischer Timestamp für jede Transaktion dient, für die ein Commit ausgeführt wurde.|  
|xdes_id|**bigint**|Eine datenbankspezifische interne ID für die Transaktion.|  
|commit_lbn|**bigint**|Die Nummer des Protokollblocks, der den Protokolldatensatz für den Commit der Transaktion enthält.|  
|commit_csn|**bigint**|Die instanzspezifische Commitfolgenummer für die Transaktion.|  
|commit_time|**smalldatetime**|Der Zeitpunkt, zu dem für die Transaktion ein Commit ausgeführt wurde.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


