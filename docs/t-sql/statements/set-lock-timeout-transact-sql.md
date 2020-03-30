---
title: SET LOCK_TIMEOUT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LOCK_TIMEOUT_TSQL
- SET_LOCK_TIMEOUT_TSQL
- SET LOCK_TIMEOUT
- LOCK_TIMEOUT
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- releasing locks
- LOCK_TIMEOUT option
- SET LOCK_TIMEOUT statement
- locking [SQL Server], time-outs
- wait time for lock releases [SQL Server]
ms.assetid: dd0c389e-956d-435e-bf71-e16624a0a215
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 97bdfbe485c129e7040235db7fffe296bb16897a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67928908"
---
# <a name="set-lock_timeout-transact-sql"></a>SET LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt an, wie viele Millisekunden eine Anweisung auf die Aufhebung einer Sperre wartet.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
SET LOCK_TIMEOUT timeout_period  
```  
  
## <a name="arguments"></a>Argumente  
 *timeout_period*  
 Anzahl der Millisekunden, die vergehen, bevor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Sperrfehler zurückgibt. Der Wert -1 (Standardwert) gibt an, dass keine Wartezeit festgelegt ist (d. h., es wird ewig gewartet).  
  
 Wenn die Wartezeit auf eine Sperre den Timeoutwert überschreitet, wird ein Fehler zurückgegeben. Der Wert 0 gibt an, dass nicht gewartet und eine Meldung zurückgegeben wird, sobald eine Sperre auftritt.  
  
## <a name="remarks"></a>Bemerkungen  
 Zu Beginn einer Verbindung besitzt diese Einstellung den Wert -1. Nach einer Änderung bleibt die neue Einstellung für die restliche Verbindungsdauer bestehen.  
  
 Die Einstellung von SET LOCK_TIMEOUT wird zur Ausführungszeit und nicht zur Analysezeit festgelegt.  
  
 Der READPAST-Sperrhinweis stellt eine Alternative zu dieser SET-Option dar.  
  
 CREATE DATABASE-, ALTER DATABASE- und DROP DATABASE-Anweisungen erkennen die SET LOCK_TIMEOUT-Einstellung nicht an.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-set-the-lock-timeout-to-1800-milliseconds"></a>A: Festlegen des Sperrtimeout auf 1800 Millisekunden  
 Im folgenden Beispiel wird der Sperrtimeout auf `1800` Millisekunden festgelegt.  
  
```sql  
SET LOCK_TIMEOUT 1800;  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-set-the-lock-timeout-to-wait-forever-for-a-lock-to-be-released"></a>B. Festlegen des Sperrtimeouts, sodass dieses für immer darauf wartet, dass eine Sperre aufgehoben wird.  
 Im folgenden Beispiel wird festgelegt, dass das Sperrtimeout für immer wartet und nie abläuft. Dabei handelt es sich um das Standardverhalten, das bereits zu Beginn jeder Verbindung festgelegt wird.  
  
```sql  
SET LOCK_TIMEOUT -1;  
```  
  
 Im folgenden Beispiel wird der Sperrtimeout auf `1800` Millisekunden festgelegt. In diesem Release analysiert [!INCLUDE[ssDW](../../includes/ssdw-md.md)] die Anweisung zwar erfolgreich, ignoriert dabei aber den Wert 1800 und verwendet weiterhin das Standardverhalten.  
  
```sql  
SET LOCK_TIMEOUT 1800;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [@@LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [SET-Anweisungen &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

