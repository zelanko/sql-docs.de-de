---
title: VERSION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a71eaec07e5516c0e8e9d33b9f026cc078d88e7d
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792061"
---
# <a name="version---transact-sql-metadata-functions"></a>VERSION: Metadatenfunktionen von Transact-SQL
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 Gibt die Version von [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] oder [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] zurück, die auf dem Gerät ausgeführt wird.  
  
![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol zum Themenlink") [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41; (Transact-SQL-Syntaxkonventionen (Transact-SQL))](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Argumente  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
Ein Tabellenname muss in einer [FROM](../../t-sql/queries/from-transact-sql.md)-Klausel angegeben sein, damit diese Funktion Ergebnisse zurückgibt. Eine Ergebniszeile wird für jede Zeile im Resultset der Abfrage zurückgegeben. Verwenden Sie [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md), um die Anzahl der zurückgegebenen Zeilen einzuschränken.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird die Versionsnummer zurückgegeben.  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
