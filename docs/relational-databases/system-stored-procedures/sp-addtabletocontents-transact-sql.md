---
title: sp_addtabletocontents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addtabletocontents_TSQL
- sp_addtabletocontents
helpviewer_keywords:
- sp_addtabletocontents
ms.assetid: 2ea27001-74f4-463e-bf1b-b6b5a86b9219
author: stevestein
ms.author: sstein
ms.openlocfilehash: e9d5e0e22f5dcca3611923782786a83ada1672ca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68117932"
---
# <a name="sp_addtabletocontents-transact-sql"></a>sp_addtabletocontents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt in die Mergenachverfolgungstabellen Verweise auf alle Zeilen in einer Quelltabelle ein, die derzeit nicht in den Nachverfolgungstabellen eingeschlossen sind. Verwenden Sie diese Option, wenn Sie eine große Datenmenge mithilfe von **bcp**Massen geladen haben, wodurch keine mergeüberwachungsertrigger ausgelöst werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addtabletocontents [ @table_name = ] 'table_name'  
    [ , [ @owner_name = ] 'owner_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_name = ] 'table_name'`Der Name der Tabelle. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @owner_name = ] 'owner_name'`Der Name des Besitzers der Tabelle. *owner_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @filter_clause = ] 'filter_clause'`Gibt eine Filter Klausel an, die steuert, welche Zeilen der neu geladenen Daten den Mergenachverfolgungstabellen hinzugefügt werden sollen. *filter_clause* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. Wenn *filter_clause* **null**ist, werden alle Massen geladenen Zeilen hinzugefügt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addtabletocontents** wird nur bei der Mergereplikation verwendet.  
  
 Auf die Zeilen in der *table_name* wird von der **ROWGUIDCOL** verwiesen, und die Verweise werden den mergeverfolgungs-Tabellen hinzugefügt. **sp_addtabletocontents** sollte nach dem Massen Kopieren von Daten in eine Tabelle verwendet werden, die mithilfe der Mergereplikation veröffentlicht wird. Die gespeicherte Prozedur veranlasst die Nachverfolgung der kopierten Zeilen und gewährleistet, dass die neuen Zeilen bei der nächsten Synchronisation berücksichtigt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addtabletocontents**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
