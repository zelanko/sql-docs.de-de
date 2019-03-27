---
title: Sp_certify_removable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs:
- TSQL
helpviewer_keywords:
- sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 97964286b3281eee4e5b6850065c85034628bfdc
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493254"
---
# <a name="spcertifyremovable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Überprüft, ob eine Datenbank für die Verteilung auf austauschbaren Medien ordnungsgemäß konfiguriert ist, und meldet dem Benutzer alle Probleme.  
  
> **WICHTIG!** [!INCLUDE[ssNoteDepFutureAvoid](../../t-sql/statements/create-database-sql-server-transact-sql.md) instead.  
  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'` Gibt die Datenbank überprüft werden. *Dbname* ist **Sysname**.  
  
`[ @autofix = ] 'auto'` Überträgt den Besitz der Datenbank und aller Datenbankobjekte an den Systemadministrator und löscht alle vom Benutzer erstellten Datenbankbenutzer und nicht standardmäßigen Berechtigungen. *automatische* ist **nvarchar(4)**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Datenbank ordnungsgemäß konfiguriert ist, **Sp_certify_removable** führt die folgende:  
  
-   Legt den Offlinemodus für die Datenbank fest, sodass Dateien kopiert werden können.  
  
-   Aktualisiert die Statistik für alle Tabellen und meldet Besitz- oder Benutzerprobleme.  
  
-   Markiert die Datendateigruppen als schreibgeschützt, damit diese Dateien auf schreibgeschützte Medien kopiert werden können.  
  
 Der Systemadministrator muss der Besitzer der Datenbank und aller Datenbankobjekte sein. Der Systemadministrator ist ein bekannter Benutzer, die auf allen Servern vorhanden ist, die ausgeführt werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und erwartet werden kann, vorhanden sein, wenn die Datenbank später verteilt und installiert wird.  
  
 Wenn das Ausführen **Sp_certify_removable** ohne die **automatisch** Wert und gibt Informationen zu einem der folgenden Bedingungen:  
  
-   Der Systemadministrator ist nicht der Datenbankbesitzer.  
  
-   Beliebige vom Benutzer erstellte Benutzer sind bereits vorhanden.  
  
-   Der Systemadministrator besitzt nicht alle Objekte in der Datenbank.  
  
-   Es wurden von den Standardwerten abweichende Berechtigungen erteilt.  
  
 Sie können diese Bedingungen mithilfe der folgenden Möglichkeiten korrigieren:  
  
-   Verwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tools und Verfahren, und führen Sie **Sp_certify_removable** erneut aus.  
  
-   Führen Sie einfach **Sp_certify_removable** mit der **automatisch** Wert.  
  
 Beachten Sie, dass diese gespeicherte Prozedur nur Benutzer und Benutzerberechtigungen überprüft. Sie können der Datenbank Gruppen hinzufügen und diesen Berechtigungen erteilen. Weitere Informationen finden Sie unter [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)konfigurieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Führen Sie Berechtigungen sind nur von Mitgliedern der der **Sysadmin** -Serverrolle sein.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird überprüft, ob die `inventory`-Datenbank für das Entfernen vorbereitet ist.  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
