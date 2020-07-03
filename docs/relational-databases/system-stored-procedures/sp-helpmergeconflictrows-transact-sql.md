---
title: sp_helpmergeconflictrows (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergeconflictrows_TSQL
- sp_helpmergeconflictrows
helpviewer_keywords:
- sp_helpmergeconflictrows
ms.assetid: 131395a5-cb18-4795-a7ae-fa09d8ff347f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 85a5ad519f836288a98dd6327fc7ca8a15c0cf70
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893574"
---
# <a name="sp_helpmergeconflictrows-transact-sql"></a>sp_helpmergeconflictrows (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Zeilen in der angegebenen Konflikttabelle zurück. Diese gespeicherte Prozedur wird auf dem Computer ausgeführt, auf dem die Konflikttabelle gespeichert ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergeconflictrows [ [ @publication = ] 'publication' ]  
        , [ @conflict_table = ] 'conflict_table'  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publsher_db' ]   
    [ , [ @logical_record_conflicts = ] logical_record_conflicts ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** . Wenn die Veröffentlichung angegeben wird, werden alle Konflikte dieser Veröffentlichung zurückgegeben. Wenn die **MSmerge_conflict_Customers** Tabelle z. b. Konflikt Zeilen für die **WA** -und die ZS **-Veröffentlichungen enthält** , werden durch das Übergeben eines Veröffentlichungs namens **ca** Konflikte im Bezug auf die Zertifizierungs **Stellen Veröffentlichung abgerufen** .  
  
`[ @conflict_table = ] 'conflict_table'`Der Name der Konflikt Tabelle. *conflict_table* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden Konflikt Tabellen mithilfe des Artikels Format Namen mit **MSmerge_conflict \_ _Veröffentlichung \_ _** benannt, wobei jeweils eine Tabelle für jeden veröffentlichten Artikel verwendet wird.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @logical_record_conflicts = ] logical_record_conflicts`Gibt an, ob das Resultset Informationen zu Konflikten logischer Datensätze enthält. *logical_record_conflicts* ist vom Datentyp **int**und hat den Standardwert 0. **1** bedeutet, dass Informationen zu Konflikten logischer Datensätze zurückgegeben werden.  
  
## <a name="result-sets"></a>Resultsets  
 **sp_helpmergeconflictrows** gibt ein Resultset zurück, das aus der Basistabellen Struktur und diesen zusätzlichen Spalten besteht.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**origin_datasource**|**varchar (255)**|Ursprung des Konflikts.|  
|**conflict_type**|**int**|Code zur Angabe des Konflikttyps:<br /><br /> **1** = Aktualisierungs Konflikt: der Konflikt wurde auf Zeilenebene erkannt.<br /><br /> **2** = Konflikt bei der Spalten Aktualisierung: der Konflikt wurde auf Spaltenebene erkannt.<br /><br /> **3** = Update-DELETE-Konflikt: der Löschvorgang gewinnt den Konflikt.<br /><br /> **4** = Update-DELETE-Konflikt: die gelöschte ROWGUID, die den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **5** = Fehler beim Hochladen der Einfügung: der Einfügevorgang des Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **6** = Fehler beim Herunterladen der Einfügung: die Einfügung vom Verleger konnte nicht auf dem Abonnenten angewendet werden.<br /><br /> **7** = Fehler beim Hochladen der Löschung: der Löschvorgang auf dem Abonnenten konnte nicht auf den Verleger hochgeladen werden.<br /><br /> **8** = Fehler beim Herunterladen der Löschung: der Löschvorgang für den Verleger konnte nicht auf den Abonnenten heruntergeladen werden.<br /><br /> **9** = Fehler beim Hochladen des Updates: das Update auf dem Abonnenten konnte nicht auf dem Verleger angewendet werden.<br /><br /> **10** = Fehler beim Herunterladen des Updates: das Update auf dem Verleger konnte nicht auf den Abonnenten angewendet werden.<br /><br /> **12** = logischer Daten Satz Update WINS löschen: der gelöschte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.<br /><br /> **13** = logischer Daten Satz Konflikt Insert-Update: das Einfügen in einen logischen Datensatz steht in Konflikt mit einem Update.<br /><br /> **14** = logischer Datensatz: Delete WINS-Update Konflikt: der aktualisierte logische Datensatz, der den Konflikt verliert, wird in dieser Tabelle aufgezeichnet.|  
|**reason_code**|**int**|Fehlercode, der kontextabhängig sein kann.|  
|**reason_text**|**varchar (720)**|Fehlerbeschreibung, die kontextabhängig sein kann.|  
|**pubid**|**uniqueidentifier**|Veröffentlichungsbezeichner.|  
|**MSrepl_create_time**|**datetime**|Zeitpunkt, zu dem die Konfliktinformationen hinzugefügt wurden.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpmergeconflictrows** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** und der Rolle **replmonitor** in der Verteilungs Datenbank können **sp_helpmergeconflictrows**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen von Konflikt Informationen für Mergeveröffentlichungen &#40;Replikations Programmierung mit Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
