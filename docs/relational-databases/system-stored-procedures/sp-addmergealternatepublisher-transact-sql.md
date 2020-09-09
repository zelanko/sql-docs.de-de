---
description: sp_addmergealternatepublisher (Transact-SQL)
title: sp_addmergealternatepublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergealternatepublisher_TSQL
- sp_addmergealternatepublisher
helpviewer_keywords:
- sp_addmergealternatepublisher
ms.assetid: de46e0b1-d946-4021-bff6-2d8e3187656d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e0589b82f3126819e1638d90c8e67dea7556aafe
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548360"
---
# <a name="sp_addmergealternatepublisher-transact-sql"></a>sp_addmergealternatepublisher (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt die Möglichkeit hinzu, dass ein Abonnent einen alternativen Synchronisierungspartner verwendet. Die Veröffentlichungseigenschaften müssen angeben, dass Abonnenten mit anderen Verlegern synchronisieren können. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergealternatepublisher [ @publisher= ] 'publisher'  
          , [ @publisher_db= ] 'publisher_db'  
          , [ @publication= ] 'publication'  
          , [ @alternate_publisher= ] 'alternate_synchronization_partner'  
          , [ @alternate_publisher_db= ] 'alternate_publisher_db'  
          , [ @alternate_publication= ] 'alternate_synchronization_partner'  
     , [ @alternate_distributor= ] 'alternate_distributor'   
    [ , [ @friendly_name= ] 'friendly_name' ]   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @alternate_publisher = ] 'alternate_synchronization_partner'` Der Name des alternativen Verlegers. *alternate_synchronization_partner* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @alternate_publisher_db = ] 'alternate_publisher_db'` Der Name der Veröffentlichungs Datenbank auf dem alternativen Verleger. *alternate_publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @alternate_publication = ] 'alternate_synchronization_partner'` Der Name der Veröffentlichung auf dem alternativen Synchronisierungs Partner. *alternate_synchronization_partner* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @alternate_distributor = ] 'alternate_distributor'` Der Name des Verteilers für den alternativen Synchronisierungs Partner. *alternate_distributor* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @friendly_name = ] 'friendly_name'` Ein Anzeige Name, durch den die Zuordnung von Verleger, Veröffentlichung und Verteiler, aus denen ein alternativer Synchronisierungs Partner besteht, identifiziert werden kann. *friendly_name* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_addmergealternatepublisher** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergealternatepublisher**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_dropmergealternatepublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergealternatepublisher-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
