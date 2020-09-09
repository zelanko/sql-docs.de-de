---
description: sp_repladdcolumn (Transact-SQL)
title: sp_repladdcolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9f4405bd222ee097d052d18648122313d9872329
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538619"
---
# <a name="sp_repladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt eine Spalte zu einem vorhandenen Tabellenartikel hinzu, der veröffentlicht worden ist. Dadurch kann die neue Spalte zu allen Verlegern hinzugefügt werden, die diese Tabelle veröffentlichen, oder die Spalte kann ausschließlich zu einer bestimmten Veröffentlichung hinzugefügt werden, die die Tabelle veröffentlicht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!IMPORTANT]
>  Diese gespeicherte Prozedur wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität unterstützt. Er sollte nur mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Verlegern und wieder Veröffentlichungs Abonnenten verwendet werden [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] . Diese Prozedur sollte nicht für Spalten mit Datentypen verwendet werden, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher eingeführt wurden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_repladdcolumn [ @source_object = ] 'source_object', [ @column = ] 'column' ]  
    [ , [ @typetext = ] 'typetext' ]  
    [ , [ @publication_to_add = ] 'publication_to_add' ]  
    [ , [ @from_agent = ] from_agent ]  
    [ , [ @schema_change_script = ] 'schema_change_script' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @source_object =] '*source_object*'  
 Ist der Name des Tabellenartikels, der die hinzuzufügende neue Spalte enthält. *source_object* ist vom Datentyp **nvarchar (358**) und hat keinen Standardwert.  
  
 [ @column =] '*Spalte*'  
 Ist der Name der Spalte in der für die Replikation hinzuzufügenden Tabelle. *Column* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @typetext = ] '*TypeText*'  
 Entspricht der Definition der Spalte, die hinzugefügt wird. *TypeText* ist vom Datentyp **nvarchar (3000)** und hat keinen Standardwert. Wenn z. b. die Spalte order_filled hinzugefügt wird und es sich um ein einzelnes Zeichenfeld (nicht null) handelt und den Standardwert **N**aufweist, ist order_filled der *Column* -Parameter, während die Definition der Spalte, **char (1) NOT NULL-Einschränkung constraint_name Standard ' n '** der *TypeText* -Parameterwert wäre.  
  
 [ @publication_to_add =] '*publication_to_add*'  
 Ist der Name der Veröffentlichung, der die neue Spalte hinzugefügt wird. *publication_to_add* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert **all**. Wenn **all**, sind alle Veröffentlichungen betroffen, die diese Tabelle enthalten. Wenn *publication_to_add* angegeben wird, wird nur dieser Veröffentlichung die neue Spalte hinzugefügt.  
  
 [ @from_agent =] *from_agent*  
 Gibt an, ob die gespeicherte Prozedur von einem Replikations-Agent ausgeführt wird. *from_agent* ist vom Datentyp **int**und hat den Standardwert **0**. der Wert **1** wird verwendet, wenn diese gespeicherte Prozedur von einem Replikations-Agent ausgeführt wird. in jedem anderen Fall sollte der Standardwert **0**verwendet werden.  
  
 [ @schema_change_script =] '*schema_change_script*'  
 Gibt den Namen und Pfad eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Skripts an, das zum Ändern der systemgenerierten bzw. benutzerdefinierten gespeicherten Prozeduren dient. *schema_change_script* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. Mithilfe der Replikation ist es möglich, mindestens eine der bei der Transaktionsreplikation verwendeten Standardprozeduren durch benutzerdefinierte gespeicherte Prozeduren zu ersetzen. *schema_change_script* wird ausgeführt, nachdem eine Schema Änderung an einem replizierten Tabellen Artikel mithilfe sp_repladdcolumn vorgenommen wurde, und kann verwendet werden, um eine der folgenden Aktionen auszuführen:  
  
-   Wenn benutzerdefinierte gespeicherte Prozeduren automatisch erneut generiert werden, können *schema_change_script* verwendet werden, um diese benutzerdefinierten gespeicherten Prozeduren zu löschen und durch benutzerdefinierte gespeicherte Prozeduren zu ersetzen, die das neue Schema unterstützen.  
  
-   Wenn benutzerdefinierte gespeicherte Prozeduren nicht automatisch erneut generiert werden, können *schema_change_script*zum erneuten Generieren dieser gespeicherten Prozeduren oder zum Erstellen benutzerdefinierter gespeicherter Prozeduren verwendet werden.  
  
 [ @force_invalidate_snapshot =] *force_invalidate_snapshot*  
 Aktiviert oder deaktiviert die Möglichkeit, eine Momentaufnahme für ungültig zu erklären. *force_invalidate_snapshot* ist ein **Bit**, der Standardwert ist **1**.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken können, dass die Momentaufnahme ungültig wird. wenn dies der Fall ist, wird mit dem Wert **1** die Berechtigung zum Eintreten der neuen Momentaufnahme erteilt.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass die Momentaufnahme ungültig wird.  
  
 [ @force_reinit_subscription =] *force_reinit_subscription*  
 Aktiviert oder deaktiviert die Möglichkeit, das Abonnement erneut zu initialisieren. *force_reinit_subscription* ist ein **Bit** mit einem Standardwert von **0**.  
  
 der Wert **0** gibt an, dass Änderungen am Artikel nicht bewirken, dass das Abonnement erneut initialisiert wird.  
  
 der Wert **1** gibt an, dass Änderungen am Artikel bewirken können, dass das Abonnement erneut initialisiert wird. wenn dies der Fall ist, wird mit dem Wert **1** die Berechtigung für die erneute Initialisierung des Abonnements erteilt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle sysadmin und der festen Datenbankrolle db_owner können sp_repladdcolumn ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Als veraltet markierte Funktionen in SQL Server-Replikation](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
