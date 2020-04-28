---
title: xp_logevent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_logevent
- xp_logevent_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logevent
ms.assetid: 7b379ad0-5b12-4d2e-9c52-62465df1fdbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77275ee539a6367d7e2e04d03354155a5eff721d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68116644"
---
# <a name="xp_logevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Protokolliert eine benutzerdefinierte Meldung in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei und in der Windows-Ereignisanzeige. xp_logevent kann verwendet werden, um eine Warnung zu senden, ohne eine Nachricht an den Client zu senden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_logevent { error_number , 'message' } [ , 'severity' ]  
```  
  
## <a name="arguments"></a>Argumente  
 *error_number*  
 Eine benutzerdefinierte Fehlernummer, die größer als 50.000 ist. Der Maximalwert ist 2147483647 (2^31 - 1).  
  
 **"** *Message* **"**  
 Eine Zeichenfolge mit maximal 2048 Zeichen.  
  
 **"** *Schweregrad* **"**  
 Eine der drei folgenden Zeichenfolgen: INFORMATIONAL, WARNING oder ERROR. der *Schweregrad* ist optional. der Standardwert ist "Information".  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 xp_logevent gibt für das Codebeispiel die folgende Fehlermeldung zurück:  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie Nachrichten aus [!INCLUDE[tsql](../../includes/tsql-md.md)] Prozeduren, Triggern, Batches usw. senden, verwenden Sie die RAISERROR-Anweisung anstelle von xp_logevent. xp_logevent ruft keinen Nachrichten Handler eines Clients auf oder legt @@ERRORfest. Führen Sie die RAISERROR-Anweisung aus, um Nachrichten in die Windows-Ereignisanzeige und in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokolldatei in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu schreiben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle db_owner in der master-Datenbank oder Mitgliedschaft in der festen Serverrolle sysadmin.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Nachricht (mit den an sie übergebenen Variablen) in der Windows-Ereignisanzeige protokolliert.  
  
```  
DECLARE @@TABNAME varchar(30), @@USERNAME varchar(30), @@MESSAGE varchar(255);  
SET @@TABNAME = 'customers';  
SET @@USERNAME = USER_NAME();  
SELECT @@MESSAGE = 'The table ' + @@TABNAME + ' is not owned by the user   
   ' + @@USERNAME + '.';  
  
USE master;  
EXEC xp_logevent 60000, @@MESSAGE, informational;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [PRINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/print-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
