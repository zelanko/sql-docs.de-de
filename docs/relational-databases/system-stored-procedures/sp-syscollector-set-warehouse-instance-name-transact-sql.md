---
description: sp_syscollector_set_warehouse_instance_name (Transact-SQL)
title: sp_syscollector_set_warehouse_instance_name (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_warehouse_instance_name_TSQL
- sp_syscollector_set_warehouse_instance_name
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_warehouse_instance_name
ms.assetid: 5320fcd4-bed1-468f-b784-a5e10fcfaeb6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c0b3ffda772bfbf0c25dbc3cb2e59a81c9c8d6f6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541491"
---
# <a name="sp_syscollector_set_warehouse_instance_name-transact-sql"></a>sp_syscollector_set_warehouse_instance_name (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den Instanznamen für die Verbindungszeichenfolge an, mit der die Verbindung zum Verwaltungs-Data Warehouse hergestellt wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_set_warehouse_instance_name [ @instance_name = ] 'instance_name'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @instance_name =] '*instance_name*'  
 Der Instanzenname. *instance_name* ist vom **Datentyp vom Datentyp sysname** . der Standardwert ist die lokale Instanz, wenn NULL.  
  
> **Hinweis:**_instance_name_ muss der voll qualifizierte Instanzname sein, der aus dem Computernamen und dem Instanznamen im Format *Computername* \\ *instanceName*besteht.    
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen den Datensammler deaktivieren, bevor Sie die Konfiguration für diesen gesamten Datensammler ändern. Dieser Vorgang schlägt fehl, wenn der Datensammler aktiviert ist.  
  
 Um den aktuellen Instanznamen anzuzeigen, Fragen Sie die [syscollector_config_store](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md) Systemsicht ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="examples"></a>Beispiele  
 In dem folgenden Beispiel wird veranschaulicht, wie sich der Datensammler zur Verwendung einer Verwaltungs-Data Warehouse-Instanz auf einem Remoteserver konfigurieren lässt. In diesem Beispiel erhält der Remoteserver den Namen `RemoteSERVER`, und die Datenbank ist auf der Standardinstanz installiert.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_set_warehouse_instance_name N'RemoteSERVER'; -- the default instance is assumed on the remote server  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_config_store &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)  
  
  
