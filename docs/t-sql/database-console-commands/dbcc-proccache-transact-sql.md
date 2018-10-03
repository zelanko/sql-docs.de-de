---
title: DBCC PROCCACHE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: 2d4580bb57680392c1e3901c2fd64b399c125736
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741108"
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Zeigt Informationen zum Prozedurcache in tabellarischer Form an.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumente  
 mit  
 Lässt die Angabe von Optionen zu.  
  
 NO_INFOMSGS  
 Unterdrückt alle Informationsmeldungen mit einem Schweregrad von 0 bis 10.  
  
## <a name="remarks"></a>Remarks  
Mit dem Prozedurcache werden kompilierte und ausführbare Pläne zwischengespeichert, um die Ausführung von Batches zu beschleunigen. Die Einträge in einem Prozedurcache erfolgen auf Batchebene. Der Prozedurcache schließt die folgenden Einträge ein:
-   Kompilierte Pläne  
-   Ausführungsplan  
-   Algebraisierungsststruktur  
-   Erweiterte Prozeduren  
  
## <a name="result-sets"></a>Resultsets  
In der folgenden Tabelle werden die Spalten des Resultsets beschrieben.
  
|Spaltenname|und Beschreibung|  
|-----------------|-----------------|  
|**num proc buffs**|Gesamtanzahl von Seiten, die von allen Einträgen im Prozedurcache verwendet werden.|  
|**num proc buffs used**|Gesamtanzahl von Seiten, die von allen zurzeit verwendeten Einträgen verwendet werden.|  
|**num proc buffs active**|Nur aus Gründen der Abwärtskompatibilität beibehalten Gesamtanzahl von Seiten, die von allen zurzeit verwendeten Einträgen verwendet werden.|  
|**proc cache size**|Gesamtanzahl von Einträgen im Prozedurcache.|  
|**proc cache used**|Gesamtanzahl von Einträgen, die zurzeit verwendet werden.|  
|**proc cache active**|Nur aus Gründen der Abwärtskompatibilität beibehalten Gesamtanzahl von Einträgen, die zurzeit verwendet werden.|  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **db_owner** .
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
