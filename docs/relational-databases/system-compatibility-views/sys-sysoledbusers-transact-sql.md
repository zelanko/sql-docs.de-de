---
title: sys.sysoledbusers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
author: rothja
ms.author: jroth
ms.openlocfilehash: 331e0feea8fb0e1e7eb9637640a8bcebce3ee992
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764344"
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

    
> [!IMPORTANT]  
>  Diese [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-Systemtabelle wird nur aus Gründen der Abwärtskompatibilität als Sicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt. Es wird empfohlen, stattdessen [Katalog Sichten](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) zu verwenden.  
  
 Enthält eine Zeile für jede Benutzer- und Kennwortzuordnung für den angegebenen Verbindungsserver. **sysoledbusers** wird in der **Master** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|Sicherheits-ID (SID) des Servers.|  
|**rmtloginame**|**nvarchar (** 128 **)**|Der Name des Remote Anmelde namens, dem **LoginSID** für die verknüpfte **rmtservid**zugeordnet ist.|  
|**rmtpassword**|**nvarchar (** 128 **)**|Gibt NULL zurück.|  
|**LoginSID**|**varbinary (** 85 **)**|SID des lokalen Anmeldenamens, der zugeordnet werden soll.|  
|**status**|**smallint**|Wenn 1, sollten die Anmeldeinformationen des Benutzers für die Zuordnung verwendet werden.|  
|**changedate**|**datetime**|Datum, an dem die Zuordnungsinformationen zuletzt geändert wurden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
