---
title: Sp_addscriptexec (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8ae792ba7f8422e841abbbe2f80b096497df993
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022448"
---
# <a name="spaddscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt ein SQL-Skript (SQL-Datei) für alle Abonnenten einer Veröffentlichung bereit. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @scriptfile = ] 'scriptfile'` Ist der vollständige Pfad zur SQL-Skriptdatei. *ScriptFile* ist **nvarchar(4000)** , hat keinen Standardwert.  
  
`[ @skiperror = ] 'skiperror'` Gibt an, ob der Verteilungs-Agent oder Merge-Agent beendet werden soll, wenn ein Fehler bei der skriptausführung auftritt. *SkipError* ist **Bit**, hat den Standardwert 0.  
  
 **0** = der Agent beendet.  
  
 **1** = der Agent das Skript weiterhin und ignoriert den Fehler.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addscriptexec** wird bei der Transaktionsreplikation und Mergereplikation verwendet.  
  
 **Sp_addscriptexec** wird bei der momentaufnahmereplikation nicht verwendet.  
  
 Verwendung von **Sp_addscriptexec**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto muss über Lese- und Schreibberechtigungen für die Momentaufnahme und Leseberechtigungen-Berechtigungen auf dem Speicherort, in dem Skripts, gespeichert werden.  
  
 Die [Hilfsprogramms "Sqlcmd"](../../tools/sqlcmd-utility.md) wird verwendet, um das Skript auf dem Abonnenten ausführen und das Skript wird im Sicherheitskontext von Verteilungs-Agent oder Merge-Agent verwendet werden, Herstellen der Verbindung mit der Abonnementdatenbank ausgeführt. Wenn der Agent ausgeführt wird, auf eine frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [Osql (Hilfsprogramm)](../../tools/osql-utility.md) anstelle [Sqlcmd](../../tools/sqlcmd-utility.md).  
  
 **Sp_addscriptexec** eignet sich die Anwendung von Skripts auf Abonnenten, und verwendet [Sqlcmd](../../tools/sqlcmd-utility.md) auf den Inhalt des Skripts auf den Abonnenten angewendet. Da Abonnentenkonfigurationen variieren können, verursachen Skripts, die vor der Bereitstellung auf dem Verleger getestet werden, möglicherweise dennoch Fehler auf einem Abonnenten. *SkipError* bietet die Möglichkeit, dass der Verteilungs-Agent oder Merge-Agent, Fehler zu ignorieren und fortfahren. Verwendung [Sqlcmd](../../tools/sqlcmd-utility.md) zum Testen von Skripts vor der Ausführung **Sp_addscriptexec**.  
  
> [!NOTE]  
>  Ausgelassene Fehler werden aus Referenzgründen weiterhin im Verlauf des Agents protokolliert.  
  
 Mithilfe von **Sp_addscriptexec** zum Bereitstellen einer Skriptdatei für Veröffentlichungen, die mithilfe von FTP für die momentaufnahmeübermittlung wird nur für unterstützt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addscriptexec**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Skripts während der Synchronisierung &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Synchronisieren von Daten](../../relational-databases/replication/synchronize-data.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
