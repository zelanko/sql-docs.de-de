---
title: sp_startpublication_snapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_startpublication_snapshot
- sp_startpublication_snapshot_TSQL
helpviewer_keywords:
- sp_startpublication_snapshot
ms.assetid: 2cf568ee-0679-4d19-a394-27210bff61e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab1b3487c3a1affe7a0dc40f62d241d19b29186b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032759"
---
# <a name="sp_startpublication_snapshot-transact-sql"></a>sp_startpublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird verwendet, um den Auftrag des Momentaufnahme-Agents zu starten, mit dem die Anfangsmomentaufnahme für eine Veröffentlichung generiert wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_startpublication_snapshot [ @publication = ] 'publication'   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'`Der Name eines nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Sie sollten diesen Parameter nicht für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger festlegen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_startpublication_snapshot** wird bei allen Replikations Typen verwendet.  
  
 Bei einem nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger wird diese gespeicherte Prozedur auf dem Verteiler für die Verteilungs Datenbank ausgeführt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_startpublication_snapshot**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Anwenden der Anfangs Momentaufnahme](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)  
  
  
