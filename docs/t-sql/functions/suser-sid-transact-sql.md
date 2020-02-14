---
title: SUSER_SID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SUSER_SID
- SUSER_SID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], users
- SIDs [SQL Server]
- security identifiers [SQL Server]
- users [SQL Server], logins
- 15401 (Database Engine error)
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- SUSER_SID function
ms.assetid: 57b42a74-94e1-4326-85f1-701b9de53c7d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a31be66b07c6d5c463f5220e6359942cd507849b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "73981747"
---
# <a name="suser_sid-transact-sql"></a>SUSER_SID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die SID (Sicherheits-ID) für den angegebenen Anmeldenamen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SUSER_SID ( [ 'login' ] [ , Param2 ] )   
```  
  
## <a name="arguments"></a>Argumente  
 **'** *login* **'**  
**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher
  
 Der Anmeldename des Benutzers. *login* ist vom Datentyp **sysname**. *login* ist optional und kann eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung oder ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzer bzw. eine -Gruppe darstellen. Falls *login* nicht angegeben wird, werden Informationen über den aktuellen Sicherheitskontext zurückgegeben. Wenn der Parameter das Wort NULL enthalten ist, wird NULL zurückgegeben.  
  
 *Param2*  
**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher
  
 Gibt an, ob der Anmeldename validiert wird. *Param2* weist den Typ **int** auf und ist optional. Wenn *Param2* den Wert 0 hat, wird der Anmeldename nicht überprüft. Wenn für*Param2* nicht der Wert 0 angegeben wird, wird überprüft, ob der Windows-Anmeldename genau mit dem in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherten Anmeldenamen übereinstimmt.  
  
## <a name="return-types"></a>Rückgabetypen  
 **varbinary(85)**  
  
## <a name="remarks"></a>Bemerkungen  
 SUSER_SID kann als DEFAULT-Einschränkung in ALTER TABLE oder CREATE TABLE verwendet werden. SUSER_SID kann in der SELECT-Liste, in einer WHERE-Klausel und überall dort verwendet werden, wo ein Ausdruck zulässig ist. Auf SUSER_SID müssen immer Klammern folgen, selbst wenn kein Parameter angegeben wird.  
  
 Bei einem Aufruf ohne Argument gibt SUSER_SID die SID des aktuellen Sicherheitskontexts zurück. Bei einem Aufruf ohne Argument innerhalb eines Batches, bei dem der Kontext mithilfe von EXECUTE AS gewechselt wurde, gibt SUSER_SID die SID des Kontexts an, dessen Identität angenommen wurde. Wenn SUSER_SID(ORIGINAL_LOGIN()) aus einem Kontext aufgerufen wird, dessen Identität angenommen wurde, wird die SID des ursprünglichen Kontexts zurückgegeben.  
  
 Unterscheiden sich die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sortierung und die Windows-Sortierung, kann SUSER_SID fehlschlagen, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows die Anmeldung in einem unterschiedlichen Format speichern. Falls der Windows-Computer "TestComputer" z. B. über den Anmeldenamen "User" verfügt und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Anmeldung als TESTCOMPUTER\User speichert, kann die Suche nach der Anmeldung "TestComputer\User" den Anmeldenamen ggf. nicht richtig auflösen. Verwenden Sie *Param2*, um diese Überprüfung des Anmeldenamens zu überspringen. Abweichende Sortierungen sind häufig die Ursache für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehler 15401:  
  
 `Windows NT user or group '%s' not found. Check the name again.`  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-suser_sid"></a>A. Verwenden von SUSER_SID  
 Im folgenden Beispiel wird die Sicherheits-ID (SID) für den aktuellen Sicherheitskontext zurückgegeben.  
  
```  
SELECT SUSER_SID();  
```  
  
### <a name="b-using-suser_sid-with-a-specific-login"></a>B. Verwenden von SUSER_SID mit bestimmten Anmeldedaten  
 Im folgenden Beispiel wird die Sicherheits-ID für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa`-Anmeldenamen zurückgegeben.  
  
**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher
  
```  
SELECT SUSER_SID('sa');  
GO  
```  
  
### <a name="c-using-suser_sid-with-a-windows-user-name"></a>C. Verwenden von SUSER_SID mit einem Windows-Benutzernamen  
 Im folgenden Beispiel wird die Sicherheits-ID für den Windows-Benutzer `London\Workstation1` zurückgegeben.  
  
**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher
  
```  
SELECT SUSER_SID('London\Workstation1');  
GO  
```  
  
### <a name="d-using-suser_sid-as-a-default-constraint"></a>D: Verwenden von SUSER_SID als DEFAULT-Einschränkung  
 Im folgenden Beispiel wird `SUSER_SID` als `DEFAULT`-Einschränkung in einer `CREATE TABLE`-Anweisung verwendet.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sid_example  
(  
login_sid   varbinary(85) DEFAULT SUSER_SID(),  
login_name  varchar(30) DEFAULT SYSTEM_USER,  
login_dept  varchar(10) DEFAULT 'SALES',  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sid_example DEFAULT VALUES;  
GO  
```  
  
### <a name="e-comparing-the-windows-login-name-to-the-login-name-stored-in-sql-server"></a>E. Vergleichen des Windows-Anmeldenamens mit dem in SQL Server gespeicherten Anmeldenamen  
 Das folgende Beispiel zeigt, wie Sie *Param2* zum Abrufen der SID von Windows verwenden und wie diese SID als Eingabe für die `SUSER_SNAME`-Funktion verwendet wird. Im Beispiel wird die Anmeldung in dem Format verwendet, in dem sie unter Windows gespeichert ist (`TestComputer\User`). Die Anmeldung wird dann in dem Format zurückgegeben, in dem sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert ist (`TESTCOMPUTER\User`).  
  
**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher
  
```  
SELECT SUSER_SNAME(SUSER_SID('TestComputer\User', 0));  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ORIGINAL_LOGIN &#40;Transact-SQL&#41;](../../t-sql/functions/original-login-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [binary und varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)   
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
