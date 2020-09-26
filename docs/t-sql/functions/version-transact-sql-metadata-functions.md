---
description: 'VERSION: Metadatenfunktionen von Transact-SQL'
title: VERSION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
author: julieMSFT
ms.author: jrasnick
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1866248cf8f60f55ab0fd0d809c1ce55f7d24f59
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380525"
---
# <a name="version---transact-sql-metadata-functions"></a>VERSION: Metadatenfunktionen von Transact-SQL
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

 Gibt die Version von [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] oder [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] zurück, die auf dem Gerät ausgeführt wird.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
-- Azure Synapse Analytics and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Argumente  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
Ein Tabellenname muss in einer [FROM](../../t-sql/queries/from-transact-sql.md)-Klausel angegeben sein, damit diese Funktion Ergebnisse zurückgibt. Eine Ergebniszeile wird für jede Zeile im Resultset der Abfrage zurückgegeben. Verwenden Sie [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md), um die Anzahl der zurückgegebenen Zeilen einzuschränken.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird die Versionsnummer zurückgegeben.  
  
```sql
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Weitere Informationen 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
