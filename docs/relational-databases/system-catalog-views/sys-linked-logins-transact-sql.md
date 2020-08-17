---
description: sys.linked_logins (Transact-SQL)
title: sys. linked_logins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dd84d1a373fdfa78e7c91f64857cc8adaffa8bdd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88323956"
---
# <a name="syslinked_logins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile pro Verbindungsserver-Anmeldungszuordnung zurück und wird von Remoteprozeduraufrufen (Remote Procedure Call, RPC) und verteilten Abfragen vom lokalen Server zum entsprechenden Verbindungsserver verwendet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID des Servers in **sys.servers**.|  
|**local_principal_id**|**int**|Serverprinzipal, für den die Zuordnung gilt.<br /><br /> 0 = Platzhalter oder public.|  
|**uses_self_credential**|**bit**|Wenn der Wert 1 ist, gibt die Zuordnung für die Sitzung an, dass die eigenen Anmeldeinformationen verwendet werden sollen. Ist der Wert 0, verwendet die Sitzung den Namen und das Kennwort, die bereitgestellt sind.|  
|**remote_name**|**sysname**|Remotebenutzername, der beim Herstellen einer Verbindung verwendet wird. Das Kennwort wird auch gespeichert, jedoch nicht in den Katologsichtschnittstellen verfügbar gemacht.|  
|**modify_date**|**datetime**|Datum, an dem die verknüpfte Anmeldung zuletzt geändert wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Verknüpfte Server-Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
