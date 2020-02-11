---
title: sp_addscriptexec (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022448"
---
# <a name="sp_addscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt ein SQL-Skript (SQL-Datei) für alle Abonnenten einer Veröffentlichung bereit. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @scriptfile = ] 'scriptfile'`Der vollständige Pfad zur SQL-Skriptdatei. *scriptfile ist vom Datentyp* **nvarchar (4000)** und hat keinen Standardwert.  
  
`[ @skiperror = ] 'skiperror'`Gibt an, ob die Verteilungs-Agent oder Merge-Agent bei Auftreten eines Fehlers während der Skript Verarbeitung angehalten werden sollen. *SkipError* ist vom Typ **Bit**. der Standardwert ist 0.  
  
 **0** = der Agent wird beendet.  
  
 **1** = der Agent setzt das Skript fort und ignoriert den Fehler.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte beim Veröffentlichen von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger nicht verwendet werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addscriptexec** wird bei der Transaktions Replikation und bei der Mergereplikation verwendet.  
  
 **sp_addscriptexec** wird nicht für die Momentaufnahme Replikation verwendet.  
  
 Um **sp_addscriptexec**verwenden zu können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , muss das-Dienst Konto über Lese-und Schreibberechtigungen für den Momentaufnahme Speicherort und Leseberechtigungen für den Speicherort verfügen, an dem Skripts gespeichert werden.  
  
 Das [Hilfsprogramm sqlcmd](../../tools/sqlcmd-utility.md) wird zum Ausführen des Skripts auf dem Abonnenten verwendet, und das Skript wird in dem Sicherheitskontext ausgeführt, der vom Verteilungs-Agent oder Merge-Agent verwendet wird, wenn eine Verbindung mit der Abonnement Datenbank hergestellt wird. Wenn der Agent auf einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird, wird das [Hilfsprogramm osql](../../tools/osql-utility.md) anstelle von [sqlcmd](../../tools/sqlcmd-utility.md)verwendet.  
  
 **sp_addscriptexec** ist hilfreich beim Anwenden von Skripts auf Abonnenten und verwendet [sqlcmd](../../tools/sqlcmd-utility.md) , um den Inhalt des Skripts auf den Abonnenten anzuwenden. Da Abonnentenkonfigurationen variieren können, verursachen Skripts, die vor der Bereitstellung auf dem Verleger getestet werden, möglicherweise dennoch Fehler auf einem Abonnenten. *SkipError* bietet die Möglichkeit, die Verteilungs-Agent oder Merge-Agent Fehler zu ignorieren und fortzufahren. Verwenden Sie [sqlcmd](../../tools/sqlcmd-utility.md) , um Skripts vor dem Ausführen **sp_addscriptexec**zu testen.  
  
> [!NOTE]  
>  Ausgelassene Fehler werden aus Referenzgründen weiterhin im Verlauf des Agents protokolliert.  
  
 Die Verwendung von **sp_addscriptexec** zum Bereitstellen einer Skriptdatei für Veröffentlichungen per FTP für die Momentaufnahme [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Übermittlung wird nur für Abonnenten unterstützt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addscriptexec**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Skripts während der Synchronisierung &#40;Replikations&#41;Programmierung mit Transact-SQL](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Synchronisieren von Daten](../../relational-databases/replication/synchronize-data.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
