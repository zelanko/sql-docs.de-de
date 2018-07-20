---
title: MSdistpublishers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0cf48f494c04bd57e1bf20930917e4f9a3d015b
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102678"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Die **MSdistpublishers** Tabelle enthält eine Zeile für jeden vom lokalen Verteiler unterstützten Remoteverleger. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Verlegerverteilers.|  
|**distribution_db**|**sysname**|Der Name der Verteilungsdatenbank.|  
|**working_directory**|**nvarchar(255)**|Der Name des Arbeitsverzeichnisses zum Speichern von Daten- und Schemadateien für die Veröffentlichung verwendet werden soll.|  
|**security_mode**|**int**|Der auf dem Verteiler implementierte Sicherheitsmodus:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.<br /><br /> **1** = Windows-Authentifizierung.|  
|**login**|**sysname**|Die Anmelde-ID für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.|  
|**password**|**nvarchar(524)**|Das (verschlüsselte) Kennwort für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung.|  
|**aktiv**|**bit**|Zeigt an, ob der lokale Verteiler zurzeit vom Remoteverleger verwendet wird.|  
|**Vertrauenswürdige**|**bit**|Zeigt an, ob auf dem Remoteverleger dasselbe Kennwort wie auf dem lokalen Verteiler verwendet wird:<br /><br /> **0** = ein Kennwort ist erforderlich, auf dem Remoteverleger eine Verbindung mit dem Verteiler herstellen.<br /><br /> **1** = kein Kennwort erforderlich ist.|  
|**Drittanbieter**|**bit**|Gibt an, ob es sich bei dem Verleger um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation handelt:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation. **1** = heterogene Datenquelle.|  
|**publisher_type**|**sysname**|Der Typ des Verlegers:<br /><br /> **MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.<br /><br /> **ORACLE** = standard-Oracle-Verleger.<br /><br /> **ORACLE-GATEWAY** = Oracle Gateway-Verleger.|  
|**storage_connection_string**|**nvarchar(779)**|Der Wert des Speicher-Verbindungszeichenfolge für Azure SQL-Datenbank.|  

  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
