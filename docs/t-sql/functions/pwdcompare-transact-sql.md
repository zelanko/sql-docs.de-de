---
description: PWDCOMPARE (Transact-SQL)
title: PWDCOMPARE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PWDCOMPARE
- PWDCOMPARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sa account
- passwords [SQL Server], blank
- PWDCOMPARE function [Transact-SQL]
ms.assetid: 5f84ff9e-c1ec-46aa-8501-50f854ebcc3a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 38c35f039701d68eddfee86f4fb558a3689033d8
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380715"
---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Führt Hashing für ein Kennwort aus und vergleicht den Hash mit dem Hash eines vorhandenen Kennworts. PWDCOMPARE kann verwendet werden, um nach leeren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldekennwörtern oder allgemeinen unsicheren Kennwörtern zu suchen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 **'** *clear_text_password* **'**  
 Das unverschlüsselte Kennwort. *clear_text_password* ist vom Datentyp **sysname** (**nvarchar(128)**).  
  
 *password_hash*  
 Der Verschlüsselungshash eines Kennworts. *password_hash* ist vom Datentyp **varbinary(128)**.  
  
 *version*  
 Veralteter Parameter, der auf 1 festgelegt werden kann, wenn *password_hash* einen Wert einer Anmeldung von einer Version vor [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] darstellt, der in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher migriert, aber nie in das [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-System konvertiert wurde. *version* ist vom Datentyp **int**  
  
> [!CAUTION]  
>  Dieser Parameter wird für die Abwärtskompatibilität bereitgestellt, wird jedoch ignoriert, da Kennworthash-BLOBs nun eigene Versionsbeschreibungen enthalten. [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
 Gibt 1 zurück, wenn der Hash von *clear_text_password* mit dem Parameter *password_hash* übereinstimmt und gibt 0 (null) zurück, wenn dies nicht der Fall ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Die PWDCOMPARE-Funktion stellt keine Bedrohung der Sicherheit von Kennworthashs dar, da der gleiche Test ausgeführt werden kann, indem sich ein Benutzer mit dem als erstem Parameter bereitgestellten Kennwort anmeldet.  
  
 **PWDCOMPARE** kann nicht mit den Kennwörtern der Benutzer eigenständiger Datenbanken verwendet werden. Es gibt keine Entsprechung für eigenständige Datenbanken.  
  
## <a name="permissions"></a>Berechtigungen  
 PWDENCRYPT steht für die Öffentlichkeit zur Verfügung.  
  
 Die CONTROL SERVER-Berechtigung ist erforderlich, um die Spalte password_hash von sys.sql_logins zu untersuchen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-identifying-logins-that-have-no-passwords"></a>A. Identifizieren von Anmeldungen, die keine Kennwörter aufweisen  
 Im folgenden Beispiel werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen identifiziert, die keine Kennwörter aufweisen.  
  
```sql  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('', password_hash) = 1 ;  
```  
  
### <a name="b-searching-for-common-passwords"></a>B. Suchen nach allgemeinen Kennwörtern  
 Um nach allgemeinen Kennwörtern zu suchen, geben Sie das Kennwort als ersten Parameter an. Führen Sie z. B. die folgende Anweisung aus, um nach einem mit `password` angegebenen Kennwort zu suchen.  
  
```sql  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('password', password_hash) = 1 ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [PWDENCRYPT &#40;Transact-SQL&#41;](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
