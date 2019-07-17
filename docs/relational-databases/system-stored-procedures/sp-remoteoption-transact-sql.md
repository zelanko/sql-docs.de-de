---
title: Sp_remoteoption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remoteoption_TSQL
- sp_remoteoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remoteoption
ms.assetid: c9a7309b-eab7-4192-a414-e282581af4e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93e65bb7d72b15dcb29763a1c02845b6ff5faa01
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215935"
---
# <a name="spremoteoption-transact-sql"></a>sp_remoteoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert oder zeigt Optionen für einen Remoteanmeldenamen an, der auf dem lokalen Server definiert ist, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]Sp_remoteoption ändert keine Optionen und gibt eine Fehlermeldung zurück. Diese gespeicherte Prozedur wird nur aus Gründen der Abwärtskompatibilität unterstützt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_remoteoption [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @loginame = ] 'loginame' ]   
     [ , [ @remotename = ] 'remotename' ]   
     [ , [ @optname = ] 'optname' ]   
     [ , [ @optvalue = ] 'optvalue' ]  
```  
  
## <a name="remarks"></a>Hinweise  
 Diese gespeicherte Prozedur gibt folgende Fehlermeldung zurück:  
  
 `The trusted option in remote login mapping is no longer supported.`  
  
## <a name="see-also"></a>Siehe auch  
 [Verbindungsserver &#40;Datenbank-Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
  
