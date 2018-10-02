---
title: DBCC DROPCLEANBUFFERS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs:
- TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
author: uc-msft
ms.author: umajay
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2ac58dec08cd70a051062fdd08118d321e87ae2f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722218"
---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Entfernt alle leeren Puffer aus dem Pufferpool und alle Columnstore-Objekte aus dem Columnstore-Objektpool.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax
Syntax für SQL Server: 

```sql
DBCC DROPCLEANBUFFERS [ WITH NO_INFOMSGS ]  
```  
Syntax für Azure SQL Warehouse und Parallel Data Warehouse:

```sql  
DBCC DROPCLEANBUFFERS ( COMPUTE | ALL ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumente  
 WITH NO_INFOMSGS  
 Alle Informationsmeldungen werden unterdrückt. Informationsmeldungen werden bei [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] immer unterdrückt.  
  
 COMPUTE  
 Löschen Sie den Datencache im Arbeitsspeicher jedes Computeknotens.  
  
 ALL  
 Löschen Sie den Datencache im Arbeitsspeicher jedes Computerknotens und des Steuerknotens. Wenn Sie keinen Wert angeben, handelt es sich dabei um den Standardwert.  
  
## <a name="remarks"></a>Remarks  
Verwenden Sie DBCC DROPCLEANBUFFERS, um Abfragen mit einem frischen Puffercache zu testen, ohne den Server herunterzufahren und neu zu starten.
Sie müssen zunächst mithilfe von CHECKPOINT einen neuen Puffercache erzeugen, um leere Puffer aus dem Pufferpool und Columnstore-Objekte aus dem Columnstore-Objektpool zu entfernen. Dadurch wird erzwungen, dass alle modifizierten Seiten der aktuellen Datenbank auf den Datenträger geschrieben und die Puffer geleert werden. Anschließend können Sie durch Ausführen des DBCC DROPCLEANBUFFERS-Befehls alle Puffer aus dem Pufferpool entfernen.
  
## <a name="result-sets"></a>Resultsets  
DBCC DROPCLEANBUFFERS gibt bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Folgendes zurück:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Berechtigungen  

Gilt für: SQL Server, Parallel Data Warehouse 

- Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  

Gilt für: Azure SQL Data Warehouse

- Erfordert die Mitgliedschaft in der festen Serverrolle DB_OWNER.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  
