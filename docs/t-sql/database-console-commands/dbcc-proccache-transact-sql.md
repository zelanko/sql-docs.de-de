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
author: pmasl
ms.author: umajay
ms.openlocfilehash: 7720324915ea147cf5cac938c196957a6cb04c51
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68116460"
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Zeigt Informationen zum Prozedurcache in tabellarischer Form an.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumente  
 WITH  
 Lässt die Angabe von Optionen zu.  
  
 NO_INFOMSGS  
 Unterdrückt alle Informationsmeldungen mit einem Schweregrad von 0 bis 10.  
  
## <a name="remarks"></a>Bemerkungen  
Mit dem Prozedurcache werden kompilierte und ausführbare Pläne zwischengespeichert, um die Ausführung von Batches zu beschleunigen. Die Einträge in einem Prozedurcache erfolgen auf Batchebene. Der Prozedurcache schließt die folgenden Einträge ein:
-   Kompilierte Pläne  
-   Ausführungsplan  
-   Algebraisierungsststruktur  
-   Erweiterte Prozeduren  
  
## <a name="result-sets"></a>Resultsets  
In der folgenden Tabelle werden die Spalten des Resultsets beschrieben.
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**num proc buffs**|Gesamtanzahl von Seiten, die von allen Einträgen im Prozedurcache verwendet werden.|  
|**num proc buffs used**|Gesamtanzahl von Seiten, die von allen zurzeit verwendeten Einträgen verwendet werden.|  
|**num proc buffs active**|Nur aus Gründen der Abwärtskompatibilität beibehalten Gesamtanzahl von Seiten, die von allen zurzeit verwendeten Einträgen verwendet werden.|  
|**proc cache size**|Gesamtanzahl von Einträgen im Prozedurcache.|  
|**proc cache used**|Gesamtanzahl von Einträgen, die zurzeit verwendet werden.|  
|**proc cache active**|Nur aus Gründen der Abwärtskompatibilität beibehalten Gesamtanzahl von Einträgen, die zurzeit verwendet werden.|  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **db_owner** .
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
