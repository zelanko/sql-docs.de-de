---
description: sys.routes (Transact-SQL)
title: sys. routes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 1ed6da90c7cfaa198e22d91d17be2ca88fc8457f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447799"
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Diese Katalogsicht enthält eine Zeile pro Route. Service Broker verwendet Routen zur Suche der Netzwerkadresse für einen Dienst.   

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Route, der innerhalb der Datenbank eindeutig ist. Lässt keine NULL-Werte zu.|  
|**route_id**|**int**|Der Bezeichner für die Route. Lässt keine NULL-Werte zu.|  
|**principal_id**|**int**|Der Bezeichner des Datenbankprinzipals, der diese Route besitzt. Lässt NULL-Werte zu.|  
|**remote_service_name**|**nvarchar(256)**|Der Name des Remotediensts. Lässt NULL-Werte zu.|  
|**broker_instance**|**nvarchar(128)**|Der Bezeichner des Brokers, der als Host des Remotediensts verwendet wird. Lässt NULL-Werte zu.|  
|**Lebensdauer**|**datetime**|Datum und Uhrzeit des Ablaufs der Route. Beachten Sie, dass dieser Wert nicht die lokale Zeitzone verwendet. Stattdessen zeigt der Wert die Ablaufzeit in UTC. Lässt NULL-Werte zu.|  
|**address**|**nvarchar(256)**|Netzwerkadresse, an die Service Broker Nachrichten für den Remotedienst sendet. Lässt NULL-Werte zu. Für SQL verwaltete Instanz muss address local lauten.|  
|**mirror_address**|**nvarchar(256)**|Netzwerkadresse des Spiegelungspartners für den in der Adresse angegebenen Server. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
