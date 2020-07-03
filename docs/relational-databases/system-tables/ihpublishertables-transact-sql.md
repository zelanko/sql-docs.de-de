---
title: IHpublishertables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishertables
- IHpublishertables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishertables system table
ms.assetid: 7d16ac39-633a-4fe2-8f22-1d9afc191ee9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b0d04f3fea97e4943fbbaecf83637141afce482f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890237"
---
# <a name="ihpublishertables-transact-sql"></a>IHpublishertables (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **IHpublishertables** -Systemtabelle stellt Metadaten dar, die auf dem Verleger gespeichert werden. Diese Tabelle enthält eine Zeile für jede Quelltabelle, die von einem anderen als einem SQL Server-Verleger mithilfe des aktuellen Verteilers veröffentlicht wurde. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Identifiziert eine veröffentlichte Tabelle|  
|**publisher_id**|**smallint**|Identifiziert den Nicht-SQL Server-Verleger, aus dem die Tabelle veröffentlicht wird|  
|**name**|**sysname**|Der Name der veröffentlichten Tabelle|  
|**Eigentor**|**sysname**|Der Tabellenbesitzer|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Replikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
