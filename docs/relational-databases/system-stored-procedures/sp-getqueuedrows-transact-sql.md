---
title: sp_getqueuedrows (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 57e4551743a535c78e33b4682f8ea19132bc75a9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881590"
---
# <a name="sp_getqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ruft beim Abonnenten Zeilen ab, die über ausstehende Updates in der Warteschlange verfügen. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tablename = ] 'tablename'`Der Name der Tabelle. *TableName* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Die Tabelle muss Teil eines Abonnements in einer Warteschlange sein.  
  
`[ @owner = ] 'owner'`Der Besitzer des Abonnements. *Owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @tranid = ] 'transaction_id'`Ermöglicht das Filtern der Ausgabe nach der Transaktions-ID. *TRANSACTION_ID* ist vom Datentyp **nvarchar (70)** und hat den Standardwert NULL. Falls angegeben, wird die Transaktions-ID angezeigt, die dem Befehl in der Warteschlange zugeordnet ist. Bei einem Wert von NULL werden alle Befehle in der Warteschlange angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Zeigt alle Zeilen an, die zurzeit über mindestens eine Transaktion in der Warteschlange für die abonnierte Tabelle verfügen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Aktion**|**nvarchar (10)**|Aktionstyp, der bei der Synchronisierung durchgeführt werden soll.<br /><br /> INS= Einfügen<br /><br /> DEL = Löschen<br /><br /> UPD = Aktualisieren|  
|**Tranid**|**nvarchar (70)**|Die Transaktions-ID, unter der der Befehl ausgeführt wurde.|  
|**table column1...n**||Der Wert für jede Spalte der Tabelle, die in *TableName*angegeben ist.|  
|**msrepl_tran_version**|**uniqueidentifier**|Diese Spalte wird zum Nachverfolgen von Änderungen an replizierten Daten und für die Konflikterkennung auf dem Verleger verwendet. Diese Spalte wird automatisch der Tabelle hinzugefügt.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_getqueuedrows** wird auf Abonnenten verwendet, die am verzögertem Update über eine Warteschlange  
  
 **sp_getqueuedrows** ermittelt Zeilen einer bestimmten Tabelle in einer Abonnement Datenbank, die an einem verzögertem Update in der Warteschlange beteiligt waren, aber derzeit noch nicht vom Warteschlangen Lese-Agent aufgelöst wurden.  
  
## <a name="permissions"></a>Berechtigungen  
 **sp_getqueuedrows** erfordert SELECT-Berechtigungen für die Tabelle, die in *TableName*angegeben ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisierbare Abonnements für die Transaktions Replikation](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Erkennen und Auflösen von Konflikten beim Aktualisieren von verzögertem Update](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
