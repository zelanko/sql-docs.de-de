---
description: sp_resetstatus (Transact-SQL)
title: sp_resetstatus (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_resetstatus
- sp_resetstatus_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resetstatus
ms.assetid: b892727f-ea3b-4b94-88d9-f2386ad4962c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f76738491704d04b033126f88750670eec230a38
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541543"
---
# <a name="sp_resetstatus-transact-sql"></a>sp_resetstatus (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Setzt den Status einer fehlerverdächtigen Datenbank zurück.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_resetstatus [ @dbname = ] 'database'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @dbname =] '*Datenbank*'  
 Der Name der Datenbank, die zurückgesetzt werden soll. *Database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_resetstatus deaktiviert das Fehlerverdächtig-Flag einer Datenbank. Diese Prozedur aktualisiert die Spalten für den Modus und den Status der benannten Datenbank in sysdatabases. Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll sollte vor dem Ausführen dieser Prozedur angezeigt sowie alle Probleme behoben werden. Beenden Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nachdem Sie sp_resetstatus ausgeführt haben, und starten Sie sie neu.  
  
 Es gibt verschiedene Gründe dafür, dass eine Datenbank als fehlerverdächtig eingestuft wird. Mögliche Ursachen sind u. a. die Zugriffsverweigerung zu einer Datenbankressource durch das Betriebssystem sowie die fehlende Verfügbarkeit oder die Beschädigung einer oder mehrerer Datenbankdateien.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Status der `AdventureWorks2012`-Datenbank zurückgesetzt.  
  
```  
EXEC sp_resetstatus 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
