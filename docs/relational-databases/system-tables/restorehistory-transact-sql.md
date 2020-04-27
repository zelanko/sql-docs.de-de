---
title: restorehistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorehistory
- restorehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorehistory system table
ms.assetid: 9140ecc1-d912-4d76-ae70-e2a857da6d44
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1565adfedca53dfe6e9ddf66af559adff23337d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67910151"
---
# <a name="restorehistory-transact-sql"></a>restorehistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Wiederherstellungsvorgang. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Eine Nummer als eindeutiger Bezeichner, der jeden Wiederherstellungsvorgang angibt. Identität, Primärschlüssel.|  
|**restore_date**|**datetime**|Datum und Uhrzeit des Starts des Wiederherstellungs Vorgangs. Kann den Wert NULL haben.|  
|**destination_database_name**|**nvarchar(128)**|Name der Zieldatenbank für den Wiederherstellungsvorgang. Kann den Wert NULL haben.|  
|**user_name**|**nvarchar(128)**|Name des Benutzers, der den Wiederherstellungsvorgang ausgeführt hat. Kann den Wert NULL haben.|  
|**backup_set_id**|**int**|Eindeutige ID, die den wiederhergestellten Sicherungssatz bezeichnet. Verweise **(backup_set_id)**.|  
|**restore_type**|**char (1)**|Typ des Wiederherstellungsvorgangs:<br /><br /> D = Datenbank<br /><br /> F = Datei<br /><br /> G = Dateigruppe<br /><br /> I = Differenziell<br /><br /> L = Protokoll<br /><br /> V = Nur überprüfen<br /><br /> Kann den Wert NULL haben.|  
|**replace**|**bit**|Zeigt an, ob der Wiederherstellungsvorgang die Option REPLACE angegeben hat:<br /><br /> 1 = Angegeben<br /><br /> 0 = Nicht angegeben<br /><br /> Kann den Wert NULL haben.<br /><br /> Wenn eine Datenbank mit einer Datenbankmomentaufnahme wiederhergestellt wird, ist 0 die einzige mögliche Option.|  
|**recovery**|**bit**|Zeigt an, ob der Wiederherstellungsvorgang die Option RECOVERY oder NORECOVERY angegeben hat:<br /><br /> 1 = RECOVERY<br /><br /> Kann den Wert NULL haben.<br /><br /> Wenn eine Datenbank mit einer Daten Bank Momentaufnahme wieder hergestellt wird, ist 1 die einzige Option.<br /><br /> 0 = NORECOVERY|  
|**restart**|**bit**|Zeigt an, ob der Wiederherstellungsvorgang die Option RESTART angegeben hat:<br /><br /> 1 = Angegeben<br /><br /> 0 = Nicht angegeben<br /><br /> Kann den Wert NULL haben.<br /><br /> Wenn eine Datenbank mit einer Datenbankmomentaufnahme wiederhergestellt wird, ist 0 die einzige mögliche Option.|  
|**stop_at**|**datetime**|Zeitpunkt, bis zu dem die Datenbank wiederhergestellt wurde. Kann den Wert NULL haben.|  
|**device_count**|**tinyint**|Anzahl der am Wiederherstellungsvorgang beteiligten Geräte. Diese Anzahl kann niedriger sein als die Anzahl der Medienfamilien für die Sicherung. Kann den Wert NULL haben.<br /><br /> Wenn eine Datenbank mit einer Datenbankmomentaufnahme wiederhergestellt wird, ist der Wert immer 1.|  
|**stop_at_mark_name**|**nvarchar(128)**|Zeigt an, dass die Wiederherstellung bis zu der Transaktion erfolgt ist, die die benannte Markierung enthält. Kann den Wert NULL haben.<br /><br /> Wenn eine Datenbank mit einer Datenbankmomentaufnahme wiederhergestellt wird, ist dieser Wert NULL.|  
|**stop_before**|**bit**|Zeigt an, ob die Transaktion, die die benannte Markierung enthält, in den Wiederherstellungsvorgang eingeschlossen wurde:<br /><br /> 0 = Wiederherstellung hielt vor der markierten Transaktion an.<br /><br /> 1 = Wiederherstellung schloss die markierte Transaktion ein.<br /><br /> Kann den Wert NULL haben.<br /><br /> Wenn eine Datenbank mit einer Datenbankmomentaufnahme wiederhergestellt wird, ist dieser Wert NULL.|  
  
## <a name="remarks"></a>Hinweise  
 Führen Sie die gespeicherte Prozedur [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) aus, um die Anzahl der Zeilen in dieser Tabelle und in anderen Sicherungs-und Verlaufs Tabellen zu verringern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorefilegroup &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
