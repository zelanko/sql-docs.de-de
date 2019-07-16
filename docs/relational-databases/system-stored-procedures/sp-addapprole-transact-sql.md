---
title: Sp_addapprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addapprole_TSQL
- sp_addapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addapprole
ms.assetid: 24200295-9a54-4cab-9922-fb2e88632721
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 74860a8f4c8dee263ea7ee0eea75679c721d1fa5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032979"
---
# <a name="spaddapprole-transact-sql"></a>sp_addapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt der aktuellen Datenbank eine Anwendungsrolle hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addapprole [ @rolename = ] 'role' , [ @password = ] 'password'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'` Ist der Name der neuen Anwendungsrolle. *Rolle* ist **Sysname**, hat keinen Standardwert. *Rolle* muss ein gültiger Bezeichner sein und kann nicht in der aktuellen Datenbank bereits vorhanden.  
  
 Namen von Anwendungsrollen können zwischen 1 und 128 Zeichen (Buchstaben, Sonderzeichen und Ziffern) enthalten. Rollennamen können nicht keinen umgekehrten Schrägstrich enthalten (\\) noch NULL oder eine leere Zeichenfolge (").  
  
`[ @password = ] 'password'` Wird zum Aktivieren der Anwendungsrolle erforderliche Kennwort. *Kennwort* ist **Sysname**, hat keinen Standardwert. *Kennwort* darf nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterscheiden sich Benutzer (und Rollen) nicht vollständig von Schemas. Seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] unterscheiden sich Schemas und Rollen vollständig. Diese neue Architektur spiegelt sich im Verhalten von CREATE APPLICATION ROLE wider. Diese Anweisung hat Vorrang vor **Sp_addapprole**.  
  
 Um Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **Sp_addapprole** gehen Sie folgendermaßen vor:  
  
-   Wenn nicht bereits ein Schema mit dem gleichen Namen wie die Anwendungsrolle vorhanden ist, wird ein solches Schema erstellt. Das neue Schema ist im Besitz der Anwendungsrolle und wird als Standardschema der Anwendungsrolle verwendet.  
  
-   Wenn bereits ein Schema mit dem gleichen Namen wie die Anwendungsrolle vorhanden ist, erzeugt die Prozedur einen Fehler.  
  
-   Kennwortkomplexität wird nicht überprüft, indem **Sp_addapprole**. Von CREATE APPLICATION ROLE hingegen wird die Kennwortkomplexität überprüft.  
  
 Der Parameter *Kennwort* wird als unidirektionaler Hash gespeichert.  
  
 Die **Sp_addapprole** gespeicherte Prozedur kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
> [!IMPORTANT]  
>  Microsoft ODBC **verschlüsseln** Option wird nicht unterstützt, indem **SqlClient**. Sofern möglich, sollten Benutzer zur Eingabe der Anmeldeinformationen für Anwendungsrollen zur Laufzeit aufgefordert werden. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Anmeldeinformationen persistent gespeichert werden müssen, sollten Sie sie mithilfe der CryptoAPI-Funktionen verschlüsseln.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank. Ist nicht bereits ein Schema mit dem gleichen Namen und Besitzer wie die neue Rolle vorhanden, ist auch die CREATE SCHEMA-Berechtigung für die Datenbank erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die neue Anwendungsrolle `SalesApp` mit dem Kennwort `x97898jLJfcooFUYLKm387gf3` auf die aktuelle Datenbank.  
  
```  
EXEC sp_addapprole 'SalesApp', 'x97898jLJfcooFUYLKm387gf3' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)  
  
  
