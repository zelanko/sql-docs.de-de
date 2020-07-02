---
title: sp_browsesnapshotfolder (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0ea912014440191f1d5e200ed583366ad43ecb27
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715998"
---
# <a name="sp_browsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt den vollständigen Pfad für die letzte Momentaufnahme zurück, die für eine Veröffentlichung generiert wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, die den Artikel enthält. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_db = ] 'subscriber_db'`Der Name der Abonnement Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|Vollständiger Pfad zum Momentaufnahmeverzeichnis.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_browsesnapshotfolder** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 Wenn die Felder " *Abonnent* " und " *subscriber_db* " den Wert NULL haben, gibt die gespeicherte Prozedur den Momentaufnahme Ordner der letzten Momentaufnahme zurück, die für die Veröffentlichung gefunden werden kann. Wenn die Felder *Abonnent* und *subscriber_db* angegeben werden, gibt die gespeicherte Prozedur den Momentaufnahme Ordner für das angegebene Abonnement zurück. Wenn keine Momentaufnahme für die Veröffentlichung generiert wurde, wird ein leeres Resultset zurückgegeben.  
  
 Wenn die Veröffentlichung so eingerichtet ist, dass sie Momentaufnahmedateien sowohl im Arbeitsverzeichnis als auch im Momentaufnahmeordner des Verlegers generiert, dann enthält das Resultset zwei Zeilen. Die erste Zeile enthält den Veröffentlichungsmomentaufnahmeordner, und die zweite Zeile enthält das Verlegerarbeitsverzeichnis. **sp_browsesnapshotfolder** ist nützlich, um das Verzeichnis zu ermitteln, in dem Momentaufnahme Dateien generiert werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_browsesnapshotfolder**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
