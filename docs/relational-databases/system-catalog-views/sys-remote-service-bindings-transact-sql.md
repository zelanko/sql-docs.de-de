---
title: Sys. remote_service_bindings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 2a0b326eef888ebf36fded7ae4ab95fe9f1b6bc0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785198"
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Katalogsicht enthält eine Zeile pro Remotedienstbindung. 
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name dieser Remotedienstbindung. Lässt keine NULL-Werte zu.|  
|**remote_service_binding_id**|**int**|ID dieser Remotedienstbindung. Lässt keine NULL-Werte zu.|  
|**principal_id**|**int**|ID des Datenbankprinzipals, der diese Remotedienstbindung besitzt. Lässt NULL-Werte zu.|  
|**remote_service_name**|**nvarchar(256)**|Name des Remotediensts, auf den sich diese Bindung bezieht. Lässt NULL-Werte zu.|  
|**service_contract_id**|**int**|ID des Vertrags, auf den sich diese Bindung bezieht. Der Wert 0 ist ein Platzhalter, der darauf hinweist, dass diese Bindung für alle Verträge des Diensts wirksam ist. Lässt keine NULL-Werte zu.|  
|**remote_principal_id**|**int**|ID des in der Remotedienstbindung angegebenen Benutzers. Service Broker verwendet ein Zertifikat im Besitz dieses Benutzers, um mit dem angegebenen Dienst über die angegebenen Verträge zu kommunizieren. Lässt NULL-Werte zu.|  
|**is_anonymous_on**|**bit**|Diese Remotedienstbindung verwendet die ANONYMOUS-Sicherheit. Die Identität des Benutzers, der die Konversation beginnt, wird dem Zieldienst nicht zur Verfügung gestellt. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
