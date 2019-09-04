---
title: '@@MAX_CONNECTIONS (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@MAX_CONNECTIONS'
- '@@MAX_CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- simultaneous connections [SQL Server]
- maximum number of simultaneous user connections
- '@@MAX_CONNECTIONS function'
- connections [SQL Server], simultaneous
- number of simultaneous user connections
ms.assetid: 57eb9f4b-548f-4212-9684-a11d831c4732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0066488fd917e5ffbe88767318954c1727adf238
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130328"
---
# <a name="x40x40max_connections-transact-sql"></a>&#x40;&#x40;MAX_CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die maximale Anzahl gleichzeitiger Benutzerverbindungen an, die für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zulässig sind. Die zurückgegebene Anzahl ist nicht notwendigerweise die aktuell konfigurierte Anzahl.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
@@MAX_CONNECTIONS  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **integer**  
  
## <a name="remarks"></a>Bemerkungen  
 Die tatsächliche Anzahl der zulässigen Benutzerverbindungen hängt außerdem von der installierten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sowie den Beschränkungen durch Ihre Anwendungen und Hardware ab.  
  
 Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure **, um**für eine kleinere Anzahl von Verbindungen neu zu konfigurieren.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die maximale Anzahl von Benutzerverbindungen für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zurückgegeben. Im Beispiel wird vorausgesetzt, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht für eine geringere Anzahl von Benutzerverbindungen neu konfiguriert wurde.  
  
```  
SELECT @@MAX_CONNECTIONS AS 'Max Connections';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Max Connections  
---------------  
32767            
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Konfigurationsfunktionen](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Konfigurieren der Serverkonfigurationsoption Benutzerverbindungen](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
  
  
