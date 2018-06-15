---
title: '@@CONNECTIONS (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 39767751186028fd5cd8b93621d7465094d99264
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33050397"
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Die Funktion gibt die Anzahl der versuchten Verbindungen – sowohl der erfolgreichen als auch der nicht erfolgreichen – seit dem letzten Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
@@CONNECTIONS  
```  
  
## <a name="return-types"></a>Rückgabetypen
**integer**
  
## <a name="remarks"></a>Remarks  
Verbindungen sind nicht von Benutzern abhängig. Eine Anwendung kann z. B. mehrere Verbindungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] öffnen, ohne dass der Benutzer diese Verbindungen wahrnimmt.
  
Führen Sie **sp_monitor** aus, um einen Bericht zu erstellen, der verschiedene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Statistiken enthält, einschließlich der Anzahl der Verbindungsversuche.
  
@@MAX_CONNECTIONS ist die maximal zulässige Anzahl gleichzeitiger Verbindungen mit dem Server. @@CONNECTIONS wird bei jedem Anmeldeversuch inkrementiert, daher kann @@CONNECTIONS @@MAX_CONNECTIONS überschreiten.
  
## <a name="examples"></a>Beispiele  
In diesem Beispiel wird die Anzahl der Anmeldeversuche bis zum aktuellen Datum und der aktuellen Uhrzeit zurückgegeben.
  
```sql
SELECT GETDATE() AS 'Today''s Date and Time',   
@@CONNECTIONS AS 'Login Attempts';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Today's Date and Time  Login Attempts  
---------------------- --------------  
12/5/2006 10:32:45 AM  211023         
```  
  
## <a name="see-also"></a>Siehe auch
[System Statistical Functions &#40;Transact-SQL&#41; (Statistische Systemfunktionen (Transact-SQL))](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)
  
  
