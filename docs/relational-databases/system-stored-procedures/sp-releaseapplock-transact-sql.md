---
title: sp_releaseapplock (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs:
- TSQL
helpviewer_keywords:
- sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7ad6ca284f99a777b8909d2f96ea68ff83c9f467
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82817993"
---
# <a name="sp_releaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine Sperre für eine Anwendungsressource frei.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @Resource =] '*resource_name*'  
 Der Name einer Sperrressource, der von der Clientanwendung angegeben wird. In der Anwendung muss sichergestellt sein, dass die Ressource eindeutig ist. Der angegebene Name wird intern als Hashwert in einem Wert gespeichert, der im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sperren-Manager gespeichert werden kann. *resource_name* ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert. *resource_name* ist binär verglichen. Daher wird die Groß-/Kleinschreibung unabhängig von den Sortierungs Einstellungen der aktuellen Datenbank beachtet.  
  
 [ @LockOwner =] '*lock_owner*'  
 Der Besitzer der Sperre. Dabei handelt es sich um den Wert von *lock_owner* beim Anfordern der Sperre. *lock_owner* ist vom Datentyp **nvarchar(32)**. Der Wert kann **Transaction** (Standard) oder **Session** sein. Wenn der *lock_owner* Wert **Transaction**ist, wird standardmäßig sp_getapplock der innerhalb einer Transaktion ausgeführt werden muss.  
  
 [ @DbPrincipal =] '*database_principal*'  
 Der Benutzer, die Rolle oder die Anwendungsrolle mit Berechtigungen für ein Objekt in einer Datenbank. Der Aufrufer der Funktion muss ein Member von *database_principal*, dbo oder der db_owner Fixed-Daten Bank Rolle sein, damit die Funktion erfolgreich aufgerufen werden kann. Der Standardwert ist public.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 \>= 0 (Erfolg) oder < 0 (Fehler)  
  
|Wert|Ergebnis|  
|-----------|------------|  
|0|Die Sperre wurde erfolgreich aufgehoben.|  
|-999|Weist auf einen Fehler bei der Parameterüberprüfung oder einen anderen Aufruffehler hin.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Anwendung mehrere Male sp_getapplock für dieselbe Sperrenressource aufruft, muss sp_releaseapplock genauso oft aufgerufen werden, um die Sperre aufzuheben.  
  
 Wenn der Server aus irgendeinem Grund heruntergefahren wird, werden die Sperren freigegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Sperre, die der aktuellen Transaktion zugeordnet ist, für die Ressource `Form1` in der `AdventureWorks2012`-Datenbank aufgehoben.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [APPLOCK_MODE &#40;Transact-SQL-&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;Transact-SQL-&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_getapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  
