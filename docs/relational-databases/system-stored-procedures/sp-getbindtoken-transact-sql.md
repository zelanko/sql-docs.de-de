---
description: sp_getbindtoken (Transact-SQL)
title: sp_getbindtoken (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getbindtoken
- sp_getbindtoken_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_getbindtoken
ms.assetid: 5db87d77-85fa-45a3-a23a-3ea500f9a5ac
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e0a499cabf4084ab13be08d08f5879bc6eddca31
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541774"
---
# <a name="sp_getbindtoken-transact-sql"></a>sp_getbindtoken (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt einen eindeutigen Bezeichner für die Transaktion zurück. Dieser eindeutige Bezeichner ist eine Zeichenfolge, mit der Sitzungen mithilfe von sp_bindsession gebunden werden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen Multiple Active Results Sets (MARS) oder verteilte Transaktionen. Weitere Informationen finden Sie unter [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_getbindtoken [@out_token =] 'return_value' OUTPUT   
```  
  
## <a name="arguments"></a>Argumente  
 [ @out_token =] '*return_value*'  
 Das Token, das zum Binden von Sitzungen verwendet wird. *return_value* ist vom Datentyp **varchar (255)** und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 sp_getbindtoken gibt nur dann ein gültiges Token zurück, wenn die gespeicherte Prozedur innerhalb einer aktiven Transaktion ausgeführt wird. Andernfalls gibt [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Fehlermeldung zurück. Beispiel:  
  
```  
-- Declare a variable to hold the bind token.  
-- No active transaction.  
DECLARE @bind_token varchar(255);  
-- Trying to get the bind token returns an error 3921.  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
Server: Msg 3921, Level 16, State 1, Procedure sp_getbindtoken, Line 4  
Cannot get a transaction token if there is no transaction active.  
Reissue the statement after a transaction has been started.  
```  
  
 Wenn sp_getbindtoken zum Eintragen einer verteilten Transaktions Verbindung innerhalb einer geöffneten Transaktion verwendet wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt das gleiche Token zurück. Beispiel:  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @bind_token varchar(255);  
  
BEGIN TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
  
BEGIN DISTRIBUTED TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 Beide `SELECT`-Anweisungen geben dasselbe Token zurück:  
  
```  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
```  
  
 Das Bindungstoken kann zusammen mit sp_bindsession verwendet werden, um neue Sitzungen an dieselbe Transaktion zu binden. Das Bindungstoken ist nur lokal innerhalb jeder Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] gültig und kann nicht für mehrere Instanzen freigegeben werden.  
  
 Zum Erhalten und Übergeben eines Bindungstokens muss sp_getbindtoken vor sp_bindsession ausgeführt werden, um denselben Sperrbereich gemeinsam verwenden zu können. Wenn Sie ein Bindungstoken erhalten, wird sp_bindsession ordnungsgemäß ausgeführt.  
  
> [!NOTE]  
>  Um ein Bindungstoken zu erhalten, das von einer erweiterten gespeicherten Prozedur verwendet werden kann, sollte die API-Funktion srv_getbindtoken von Open Data Services verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Bindungstoken erhalten und der Bindungstokenname angezeigt.  
  
```  
DECLARE @bind_token varchar(255);  
BEGIN TRAN;  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Token`  
  
 `----------------------------------------------------------`  
  
 `\0]---5^PJK51bP<1F<-7U-]ANZ`  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_bindsession (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [srv_getbindtoken &#40;API für erweiterte gespeicherte Prozeduren&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)  
  
  
