---
description: sp_xtp_flush_temporal_history (Transact-SQL)
title: sp_xtp_flush_temporal_history | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_xtp_flush_temporal_history
- sp_xtp_flush_temporal_history_TSQL
- sys.sp_xtp_flush_temporal_history
- sys.sp_xtp_flush_temporal_history_TSQL
helpviewer_keywords:
- sp_xtp_flush_temporal_history
ms.assetid: 322e3170-93f8-468a-a123-104ce7bd7fad
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ead5aae7b27528c12c4d44d574106815ddf382f5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473325"
---
# <a name="sp_xtp_flush_temporal_history-transact-sql"></a>sp_xtp_flush_temporal_history (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Ruft den Daten Leerungs Task auf, um alle zugegebenen Zeilen aus der in-Memory-Stagingtabelle in die Datenträger basierte Verlaufs Tabelle zu verschieben.  

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_xtp_flush_temporal_history @schema_name, @object_name  
  
```  
  
## <a name="arguments"></a>Argumente  
 *\@schema_name*  
 Der Schema Name für die aktuelle oder Temporale Tabelle  
  
 *\@object_name*  
 Der Name der aktuellen oder der temporalen Tabelle.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner Berechtigungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überlegungen zur Systemleistung bei Verwendung von speicheroptimierten temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)  
  
  
