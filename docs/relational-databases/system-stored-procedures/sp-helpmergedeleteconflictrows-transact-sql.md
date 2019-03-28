---
title: Sp_helpmergedeleteconflictrows (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c60f56980aedc29c8262089748a77f113cc0449
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536482"
---
# <a name="sphelpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu Datenzeilen zurück, die Löschkonflikte verloren haben. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt, wenn die Konfliktprotokollierung dezentralisiert erfolgt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert **%**. Wenn die Veröffentlichung angegeben wird, werden alle Konflikte dieser Veröffentlichung zurückgegeben.  
  
`[ @source_object = ] 'source_object'` Ist der Name des Quellobjekts. *Source_object* ist **nvarchar(386)**, hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Verleger* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386)**|Quellobjekt für den Löschkonflikt.|  
|**rowguid**|**uniqueidentifier**|Zeilenbezeichner für den Löschkonflikt.|  
|**conflict_type**|**int**|Code, der angibt, der Art des Konflikts:<br /><br /> **1** = UpdateConflict: Konflikt wird auf der Zeilenebene erkannt.<br /><br /> **2** = ColumnUpdateConflict: Konflikt auf Spaltenebene erkannt.<br /><br /> **3** = UpdateDeleteWinsConflict: Löschvorgang gewinnt den Konflikt.<br /><br /> **4** = UpdateWinsDeleteConflict: Der gelöschte Zeilen-GUID, die den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **5** = UploadInsertFailed: Einfügevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **6** = DownloadInsertFailed: Einfügevorgang des Verlegers konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **7** = UploadDeleteFailed: Löschvorgang des Abonnenten konnte nicht an den Verleger hochgeladen werden.<br /><br /> **8** = DownloadDeleteFailed: Löschvorgang des Verlegers konnte nicht auf den Abonnenten heruntergeladen werden.<br /><br /> **9** = UploadUpdateFailed: Updatevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **10** = DownloadUpdateFailed: Updatevorgang des Verlegers konnte nicht auf dem Abonnenten angewendet werden.|  
|**reason_code**|**Int**|Fehlercode, der kontextabhängig sein kann.|  
|**reason_text**|**varchar(720)**|Fehlerbeschreibung, die kontextabhängig sein kann.|  
|**origin_datasource**|**varchar(255)**|Ursprung des Konflikts.|  
|**pubid**|**uniqueidentifier**|Veröffentlichungsbezeichner.|  
|**MSrepl_create_time**|**datetime**|Zeitpunkt, zu dem die Konfliktinformationen hinzugefügt wurden.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpmergedeleteconflictrows** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** Serverrolle und die **Db_owner** feste Datenbankrolle können ausführen **Sp_helpmergedeleteconflictrows**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
