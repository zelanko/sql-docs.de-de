---
title: sys. dm_tran_commit_table (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84278124664b72c45e038de7981057eaff1014f0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82819838"
---
# <a name="change-tracking---sysdm_tran_commit_table"></a>Änderungsnachverfolgung-sys. dm_tran_commit_table
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Zeigt eine Zeile für jede Transaktion an, für die von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Änderungsnachverfolgung ein Commit für eine Tabelle ausgeführt wird, die nachverfolgt wird. Die Verwaltungs Sicht sys. dm_tran_commit_table, die für die unter Stütz barkeit bereitgestellt wird und die transaktionsbezogenen Informationen verfügbar macht, die von der Änderungs Nachverfolgung in der Systemtabelle sys. syscommittab gespeichert werden. Die Tabelle sys.syscommittab ermöglicht eine effiziente persistente Zuordnung zwischen einer datenbankspezifischen Transaktions-ID und den Commit-Protokollfolgenummern (Log Sequence Number, LSN) und den Commit-Timestamps der Transaktion. Die Daten, die in der sys. syscommittab-Tabelle gespeichert und in dieser Verwaltungs Sicht verfügbar gemacht werden, unterliegen der Bereinigung gemäß der Beibehaltungs Dauer, die bei der Konfiguration der Änderungs Nachverfolgung angegeben wurde.  
  
> [!NOTE]  
>  Um dies von oder aus aufzurufen [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , verwenden Sie den Namen **sys. dm_pdw_nodes_tran_commit_table**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|Eine monoton steigende Zahl, die als datenbankspezifischer Timestamp für jede Transaktion dient, für die ein Commit ausgeführt wurde.|  
|xdes_id|**bigint**|Eine datenbankspezifische interne ID für die Transaktion.|  
|commit_lbn|**bigint**|Die Nummer des Protokollblocks, der den Protokolldatensatz für den Commit der Transaktion enthält.|  
|commit_csn|**bigint**|Die instanzspezifische Commitfolgenummer für die Transaktion.|  
|commit_time|**smalldatetime**|Der Zeitpunkt, zu dem für die Transaktion ein Commit ausgeführt wurde.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


