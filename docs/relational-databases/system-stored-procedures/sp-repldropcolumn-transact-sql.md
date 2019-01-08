---
title: Sp_repldropcolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repldropcolumn_TSQL
- sp_repldropcolumn
helpviewer_keywords:
- sp_repldropcolumn
ms.assetid: fdc1ec5f-f108-42b4-a2d8-f06a71913ab8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2c2a269abf3e7f465c71e09437c313196e1dcd30
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205689"
---
# <a name="sprepldropcolumn-transact-sql"></a>sp_repldropcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine Spalte aus einem vorhandenen Tabellenartikel, der veröffentlicht worden ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]
>  Diese gespeicherte Prozedur wurde als veraltet markiert und wird hauptsächlich aus Gründen der Abwärtskompatibilität unterstützt. Sie sollten nur mit verwendet werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Herausgeber und [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Wiederveröffentlichungsabonnenten. Diese Prozedur sollte nicht für Spalten mit Datentypen verwendet werden, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher eingeführt wurden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_repldropcolumn [ @source_object = ] 'source_object', [ @column = ] 'column'   
    [ , [ @from_agent = ] from_agent]   
    [ , [ @schema_change_script = ] 'schema_change_script' ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>Argumente  
 [ @source_object =] '*Source_object*"  
 Ist der Name des Tabellenartikels, der die zu löschende Spalte enthält. *Source_object* ist vom Datentyp nvarchar(258) und hat keinen Standardwert.  
  
 [ @column =] '*Spalte*"  
 Entspricht dem Namen der Spalte in der zu löschenden Tabelle. *Spalte* ist vom Datentyp Sysname und hat keinen Standardwert.  
  
 [ @from_agent =] *From_agent*  
 Gibt an, ob die gespeicherte Prozedur von einem Replikations-Agent ausgeführt wird. *From_agent* ist "Int" hat den Standardwert 0 (null), in denen der Wert 1 verwendet wird, wenn es sich bei dieser gespeicherten Prozedur von einem Replikations-Agent ausgeführt wird, und in allen anderen Fällen sollte der Standardwert 0 verwendet werden.  
  
 [ @schema_change_script =] '*Schema_change_script*"  
 Gibt den Namen und Pfad eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Skripts an, das zum Ändern der systemgenerierten bzw. benutzerdefinierten gespeicherten Prozeduren dient. *Schema_change_script* ist vom Datentyp nvarchar(4000) und hat den Standardwert NULL. Mithilfe der Replikation ist es möglich, mindestens eine der bei der Transaktionsreplikation verwendeten Standardprozeduren durch benutzerdefinierte gespeicherte Prozeduren zu ersetzen. *Schema_change_script* wird ausgeführt, nachdem eine schemaänderung erfolgt, um zu einem replizierten Tabellenartikel, die mithilfe von Sp_repldropcolumn und kann verwendet werden, um einen der folgenden Schritte aus:  
  
-   Wenn benutzerdefinierte gespeicherte Prozeduren automatisch erneut generiert werden, *Schema_change_script* dienen kann, löschen diese benutzerdefinierten gespeicherten Prozeduren, und Ersetzen Sie sie durch eine benutzerdefinierte benutzerdefinierte gespeicherte Prozeduren, die das neue Schema unterstützen.  
  
-   Wenn benutzerdefinierte gespeicherte Prozeduren nicht automatisch erneut generiert werden, *Schema_change_script*können verwendet werden, um diese gespeicherten Prozeduren neu zu generieren, oder erstellen Sie benutzerdefinierte gespeicherte Prozeduren.  
  
 [ @force_invalidate_snapshot =] *Force_invalidate_snapshot*  
 Aktiviert oder deaktiviert die Möglichkeit, eine Momentaufnahme für ungültig zu erklären. *Force_invalidate_snapshot* ist vom Datentyp Bit hat den Standardwert 1.  
  
 Der Wert 1 gibt an, dass Änderungen am Artikel bewirken können, dass die Momentaufnahme ungültig wird. Wenn dies zutrifft, wird mit dem Wert 1 die Berechtigung für das Auftreten de neuen Momentaufnahme erteilt.  
  
 Der Wert 0 gibt an, dass Änderungen am Artikel nicht bewirken, dass die Momentaufnahme ungültig wird.  
  
 [ @force_reinit_subscription =] *Force_reinit_subscription*  
 Aktiviert oder deaktiviert die Möglichkeit, das Abonnement erneut zu initialisieren. *Force_reinit_subscription* ähnelt ein wenig mit dem Standardwert 0.  
  
 Der Wert 0 gibt an, dass Änderungen am Artikel nicht bewirken, dass das Abonnement erneut initialisiert wird.  
  
 Der Wert 1 gibt an, dass Änderungen am Artikel bewirken können, dass das Abonnement erneut initialisiert wird. Wenn dies zutrifft, wird mit dem Wert 1 die Berechtigung für das Auftreten der erneuten Initialisierung des Abonnements erteilt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle sysadmin auf dem Verleger oder Mitglieder der festen Datenbankrollen db_owner oder db_ddladmin für die Veröffentlichungsdatenbank können sp_repldropcolumn ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Als veraltet markierte Funktionen in SQL Server-Replikation](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
