---
title: DBCC HELP (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC HELP
- DBCC_HELP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC statement syntax information
- DBCC HELP statement
ms.assetid: 306092c6-4354-4e47-928b-606124fbdc6e
author: pmasl
ms.author: umajay
ms.openlocfilehash: aa73ad04708c75a474fade49a183b2f66b55c006
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86485025"
---
# <a name="dbcc-help-transact-sql"></a>DBCC HELP (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

Gibt Syntaxinformationen für den angegebenen DBCC-Befehl zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC HELP ( 'dbcc_statement' | @dbcc_statement_var | '?' )  
[ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *dbcc_statement* |  *\@dbcc_statement_var*  
 Der Name des DBCC-Befehls, für den Syntaxinformationen angefordert werden. Geben Sie nur den Teil des DBCC-Befehls an, der auf DBCC folgt, z. B. CHECKDB anstelle von DBCC CHECKDB.  
  
 ?  
 Gibt alle DBCC-Befehle zurück, für die Hilfe verfügbar ist.  
  
 WITH NO_INFOMSGS  
 Unterdrückt alle Informationsmeldungen mit einem Schweregrad von 0 bis 10.  
  
## <a name="result-sets"></a>Resultsets  
DBCC HELP gibt ein Resultset zurück, das die Syntax für den angegebenen DBCC-Befehl anzeigt.
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .
  
## <a name="examples"></a>Beispiele  
### <a name="a-using-dbcc-help-with-a-variable"></a>A. Verwenden von DBCC HELP mit einer Variablen  
Mit dem folgenden Beispiel werden die Syntaxinformationen für DBCC `CHECKDB` zurückgegeben.
  
```sql  
DECLARE @dbcc_stmt sysname;  
SET @dbcc_stmt = 'CHECKDB';  
DBCC HELP (@dbcc_stmt);  
GO  
```  
  
### <a name="b-using-dbcc-help-with-the--option"></a>B. Verwenden von DBCC HELP mit ? Option  
Mit dem folgenden Beispiel werden alle DBCC-Anweisungen zurückgegeben, für die Hilfe zur Verfügung steht.
  
```sql  
DBCC HELP ('?');  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
