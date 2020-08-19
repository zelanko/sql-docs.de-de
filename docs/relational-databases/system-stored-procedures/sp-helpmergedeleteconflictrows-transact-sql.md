---
description: sp_helpmergedeleteconflictrows (Transact-SQL)
title: sp_helpmergedeleteconflictrows (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c4cda70ec894a50561cd62dc459bac915f437cc3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447028"
---
# <a name="sp_helpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu Datenzeilen zurück, die Löschkonflikte verloren haben. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt, wenn die Konfliktprotokollierung dezentralisiert erfolgt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** . Wenn die Veröffentlichung angegeben wird, werden alle Konflikte dieser Veröffentlichung zurückgegeben.  
  
`[ @source_object = ] 'source_object'` Der Name des Quell Objekts. *source_object* ist vom Datentyp **nvarchar (386)** und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar (386)**|Quellobjekt für den Löschkonflikt.|  
|**ROWGUID**|**uniqueidentifier**|Zeilenbezeichner für den Löschkonflikt.|  
|**conflict_type**|**int**|Code, der den Typ des Konflikts angibt:<br /><br /> **1** = UpdateConflict: der Konflikt wurde auf Zeilenebene erkannt.<br /><br /> **2** = ColumnUpdateConflict: der Konflikt wurde auf Spaltenebene erkannt.<br /><br /> **3** = UpdateDeleteWinsConflict: der Löschvorgang gewinnt den Konflikt.<br /><br /> **4** = UpdateWinsDeleteConflict: die gelöschte ROWGUID, die den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **5** = UploadInsertFailed: der Einfügevorgang vom Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **6** = DownloadInsertFailed: der Einfügevorgang vom Verleger konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **7** = UploadDeleteFailed: der Löschvorgang auf dem Abonnenten konnte nicht auf den Verleger hochgeladen werden.<br /><br /> **8** = DownloadDeleteFailed: der Löschvorgang auf dem Verleger konnte nicht auf den Abonnenten heruntergeladen werden.<br /><br /> **9** = UploadUpdateFailed: das Update auf dem Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **10** = DownloadUpdateFailed: das Update auf dem Verleger konnte nicht auf den Abonnenten angewendet werden.|  
|**reason_code**|**Int**|Fehlercode, der kontextabhängig sein kann.|  
|**reason_text**|**varchar (720)**|Fehlerbeschreibung, die kontextabhängig sein kann.|  
|**origin_datasource**|**varchar (255)**|Ursprung des Konflikts.|  
|**pubid**|**uniqueidentifier**|Veröffentlichungsbezeichner.|  
|**MSrepl_create_time**|**datetime**|Zeitpunkt, zu dem die Konfliktinformationen hinzugefügt wurden.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpmergedeleteconflictrows** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** und der festen Daten Bank Rolle **db_owner** können **sp_helpmergedeleteconflictrows**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
