---
title: sys.dm_db_xtp_merge_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: c1224e88-af74-4c99-ae32-d5d2c552a1f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c7ff8638aeeb02cdb86643fd1fc6a3241a8db26
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67732547"
---
# <a name="sysdmdbxtpmergerequests-transact-sql"></a>sys.dm_db_xtp_merge_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Verfolgt Zusammenführungsanforderungen für Datenbanken nach. Die Merge-Anforderung kann von SQL Server generiert wurden, oder die Anforderung konnte wurden von einem Benutzer mit [sp_xtp_merge_checkpoint_files (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md).

> [!NOTE]
> Diese dynamische verwaltungssicht (DMV), sys.dm_db_xtp_merge_requests, bis Microsoft SQL Server 2014 vorhanden.
> Aber beginnend mit SQL Server 2016 dieser DMV nicht mehr gilt.

## <a name="columns-in-the-report"></a>Spalten im Bericht

| Spaltenname | Datentyp | Beschreibung |
| :-- | :-- | :-- |
| request_state | TINYINT | Der Status der Zusammenführungsanforderung:<br/>0 = Requested<br/>1 = Pending<br/>2 = installiert<br/>3 = Abandoned |
| request_state_desc | nvarchar(60) | Bedeutung für den aktuellen Status der Anforderung:<br/><br/>Angeforderte - ist eine zusammenführungsanforderung vorhanden.<br/>-Steht die Zusammenführung verarbeitet wird.<br/>Installiert – ist die Zusammenführung abgeschlossen.<br/>Abgebrochen: konnte die Zusammenführung nicht abgeschlossen, möglicherweise weil der Speicher. |
| destination_file_id | GUID | Der eindeutige Bezeichner der Zieldatei für die Zusammenführung der Quelldateien. |
| lower_bound_tsn | BIGINT | Der minimale Zeitstempel für die als Ziel verwendete zusammengeführte Datei. Der niedrigste Transaktionszeitstempel aller zusammenzuführenden Quelldateien. |
| upper_bound_tsn | BIGINT | Der maximale Zeitstempel für die als Ziel verwendete zusammengeführte Datei. Der höchste Transaktionszeitstempel aller zusammenzuführenden Quelldateien. |
| collection_tsn | BIGINT | Der Zeitstempel, bei dem die aktuelle Zeile gesammelt werden kann.<br/><br/>Eine Zeile mit dem Status "Installed" wird entfernt, wenn checkpoint_tsn größer als collection_tsn ist.<br/><br/>Wenn checkpoint_tsn kleiner als collection_tsn ist, wird eine Zeile mit dem Status "Abandoned" entfernt. |
| checkpoint_tsn | BIGINT | Die Zeit, zu der der Prüfpunkt gestartet wurde.<br/><br/>Alle Löschvorgänge, die von Transaktionen mit einem niedrigeren Zeitstempel ausgeführt werden, werden in der neuen Datendatei berücksichtigt. Die übrigen Löschvorgänge werden in die als Ziel verwendete Änderungsdatei verschoben. |
| sourcenumber_file_id | GUID | Bis zu 16 interne Datei-IDs, die die Quelldateien in der Zusammenführung eindeutig zu identifizieren. |

## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW DATABASE STATE-Berechtigung für die aktuelle Datenbank.

## <a name="see-also"></a>Siehe auch

[Dynamische Verwaltungssichten für Speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)
