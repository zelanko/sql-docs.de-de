---
title: Sys.Routes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b4a7ab2ef3fa5f632b78124734181e0cff80440a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39554210"
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Diese Katalogsicht enthält eine Zeile pro Route. Service Broker verwendet Routen zur Suche der Netzwerkadresse für einen Dienst.   

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Route, der innerhalb der Datenbank eindeutig ist. Lässt keine NULL-Werte zu.|  
|**route_id**|**int**|Der Bezeichner für die Route. Lässt keine NULL-Werte zu.|  
|**principal_id**|**int**|Der Bezeichner des Datenbankprinzipals, der diese Route besitzt. Lässt NULL-Werte zu.|  
|**remote_service_name**|**nvarchar(256)**|Der Name des Remotediensts. Lässt NULL-Werte zu.|  
|**broker_instance**|**nvarchar(128)**|Der Bezeichner des Brokers, der als Host des Remotediensts verwendet wird. Lässt NULL-Werte zu.|  
|**lifetime**|**datetime**|Datum und Uhrzeit des Ablaufs der Route. Beachten Sie, dass dieser Wert nicht die lokale Zeitzone verwendet. Stattdessen zeigt der Wert die Ablaufzeit in UTC. Lässt NULL-Werte zu.|  
|**address**|**nvarchar(256)**|Netzwerkadresse, an die Service Broker Nachrichten für den Remotedienst sendet. Lässt NULL-Werte zu. Für verwaltete SQL-Datenbankinstanz muss die Adresse lokal sein.|  
|**mirror_address**|**nvarchar(256)**|Netzwerkadresse des Spiegelungspartners für den in der Adresse angegebenen Server. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
