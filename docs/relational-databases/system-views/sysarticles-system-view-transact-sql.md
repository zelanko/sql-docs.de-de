---
description: sysarticles (Systemsicht) (Transact-SQL)
title: sysarticles (System Sicht) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticles
- sysarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticles view
ms.assetid: 18f8c9b3-cab7-4e8f-8754-11ac38c3f789
author: stevestein
ms.author: sstein
ms.openlocfilehash: f926cb0f00f8975afe065ccab87a8aa7a1436266
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463851"
---
# <a name="sysarticles-system-view-transact-sql"></a>sysarticles (Systemsicht) (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **sysarticles** -Sicht macht Artikeleigenschaften verfügbar. Diese Sicht wird in der distribution-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Die Identitätsspalte, die eine eindeutige ID für den Artikel bereitstellt.|  
|**creation_script**|**nvarchar(255)**|Das Schemaskript für den Artikel.|  
|**del_cmd**|**nvarchar(255)**|Der bei einer DELETE-Anweisung auszuführende Befehl, wird sonst aus dem Protokoll konstruiert|  
|**Beschreibung**|**nvarchar(255)**|Der Beschreibungseintrag für den Artikel.|  
|**dest_table**|**sysname**|Der Name der Zieltabelle|  
|**filter**|**int**|Die ID der gespeicherten Prozedur, die für horizontales Partitionieren verwendet wird.|  
|**filter_clause**|**ntext**|Die WHERE-Klausel des Artikels, die für horizontales Filtern verwendet wird.|  
|**ins_cmd**|**nvarchar(255)**|Der beim Ausführen einer INSERT-Anweisung auszuführende Befehl. Andernfalls wird der Befehl aus dem Protokoll konstruiert.|  
|**name**|**sysname**|Der mit dem Artikel verknüpfte Name, der innerhalb der Veröffentlichung eindeutig ist.|  
|**objid**|**int**|Die Objekt-ID der veröffentlichten Tabelle.|  
|**pubid**|**int**|Die ID der Veröffentlichung, zu der der Artikel gehört.|  
|**pre_creation_cmd**|**tinyint**|Der Voraberstellungsbefehl für DROP TABLE, DELETE TABLE oder TRUNCATE:<br /><br /> **0** = keine.<br /><br /> **1** = DROP.<br /><br /> **2** = DELETE.<br /><br /> **3** = TRUNCATE.|  
|**status**|**tinyint**|Die Bitmaske der Artikeloptionen und der Status, die das Ergebnis des bitweisen logischen OR von mindestens einem der folgenden Werte sein können:<br /><br /> **1** = Artikel ist aktiv.<br /><br /> **8** = Den Spaltennamen in INSERT-Anweisungen einschließen.<br /><br /> **16** = Parametrisierte Anweisungen verwenden.<br /><br /> **24** = Sowohl den Spaltennamen in INSERT-Anweisungen einschließen als auch parametrisierte Anweisungen verwenden.<br /><br /> **64** = die horizontale Partition des Artikels wird durch ein transformier bares Abonnement definiert.<br /><br /> Ein aktiver Artikel, der parametrisierte Anweisungen verwendet, würde in dieser Spalte beispielsweise den Wert **17** aufweisen. Der Wert **0** bedeutet, dass der Artikel inaktiv ist und keine zusätzlichen Eigenschaften definiert sind.|  
|**sync_objid**|**int**|Die ID der Tabelle oder Sicht, die die Artikeldefinition darstellt.|  
|**type**|**tinyint**|Der Artikeltyp:<br /><br /> **1** = Protokollbasierter Artikel.<br /><br /> **3** = Protokollbasierter Artikel mit manuell erstelltem Filter.<br /><br /> **5** = Protokollbasierter Artikel mit manuell erstellter Sicht.<br /><br /> **7** = Protokollbasierter Artikel mit manuell erstelltem Filter und manuell erstellter Sicht.<br /><br /> **8** = Ausführung gespeicherter Prozeduren.<br /><br /> **24** = serialisierbare Ausführung gespeicherter Prozeduren.<br /><br /> **32** = gespeicherte Prozedur (nur Schema).<br /><br /> **64** = Ansicht (nur Schema).<br /><br /> **128** = Funktion (nur Schema).|  
|**upd_cmd**|**nvarchar(255)**|Der bei einer UPDATE-Anweisung auszuführende Befehl, wird sonst aus dem Protokoll konstruiert|  
|**schema_option**|**Binär (8)**|Die Bitmaske der Schemagenerierungsoptionen für den Artikel, die steuern, welche Teile des Artikelschemas zur Übermittlung an den Abonnenten ausgegeben werden. Weitere Informationen zu den Schemaoptionen finden Sie unter [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**sysname**|Der Besitzer der Tabelle in der Zieldatenbank|  
|**ins_scripting_proc**|**int**|Die registrierte benutzerdefinierte gespeicherte Prozedur oder das Skript, die/das beim Replizieren einer INSERT-Anweisung ausgeführt wird.|  
|**del_scripting_proc**|**int**|Die registrierte benutzerdefinierte gespeicherte Prozedur oder das Skript, die/das beim Replizieren einer DELETE-Anweisung ausgeführt wird.|  
|**upd_scripting_proc**|**int**|Die registrierte benutzerdefinierte gespeicherte Prozedur oder das Skript, die/das beim Replizieren einer UPDATE-Anweisung ausgeführt wird.|  
|**custom_script**|**nvarchar (2048)**|Die registrierte benutzerdefinierte gespeicherte Prozedur oder das Skript, die/das am Ende des DDL-Triggers ausgeführt wird|  
|**fire_triggers_on_snapshot**|**bit**|Gibt an, ob replizierte Trigger beim Anwenden der Momentaufnahme ausgeführt werden. Es werden folgende Werte unterstützt:<br /><br /> **0** = Trigger werden nicht ausgeführt.<br /><br /> **1** = Trigger werden ausgeführt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
