---
title: Sp_fulltext_database (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 5ee4cb63c476b898c286f6223e9e56d1778e6a47
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39563904"
---
# <a name="spfulltextdatabase-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Hat keine Auswirkung auf Volltextkataloge in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen und wird nur für Abwärtskompatibilität unterstützt. 
  **sp_fulltext_database** deaktiviert nicht die Volltext-Engine für eine bestimmte Datenbank. Alle durch Benutzer erstellten Datenbanken in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützen standardmäßig die Volltextindizierung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@action=**] **'***action***'**  
 Die Aktion, die ausgeführt werden soll. **action** ist vom Datentyp **varchar(20)**. Die folgenden Werte sind möglich:  
  
|value|Description|  
|-----------|-----------------|  
|**Aktivieren**|Wird nur aus Gründen der Abwärtskompatibilität unterstützt. Hat keine Auswirkung auf die Volltextkataloge in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen.|  
|**disable**|Wird nur aus Gründen der Abwärtskompatibilität unterstützt. Hat keine Auswirkung auf die Volltextkataloge in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen kann die Volltextindizierung nicht deaktiviert werden. Bei der Deaktivierung der Volltextindizierung werden keine Zeilen aus **sysfulltextcatalogs** gelöscht, und es wird auch nicht bewirkt, dass volltextfähige Tabellen nicht mehr für die Volltextindizierung markiert sind. Alle Definitionen von Volltextmetadaten sind weiterhin in den Systemtabellen vorhanden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** und der festen Datenbankrolle **db_owner** können **sp_fulltext_database**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
