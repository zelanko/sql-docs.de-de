---
description: DBCC OUTPUTBUFFER (Transact-SQL)
title: DBCC OUTPUTBUFFER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC OUTPUTBUFFER
- OUTPUTBUFFER_TSQL
- OUTPUTBUFFER
- DBCC_OUTPUTBUFFER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC OUTPUTBUFFER statement
- output buffers
- current output buffer
ms.assetid: e912a06d-9fde-4e26-b057-801255d79504
author: pmasl
ms.author: umajay
ms.openlocfilehash: 567f303b2ebd78fab3f6803ad2490ca1dc059e2b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88311256"
---
# <a name="dbcc-outputbuffer-transact-sql"></a>DBCC OUTPUTBUFFER (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Gibt den Inhalt des aktuellen Ausgabepuffers für die angegebene *session_id*in hexadezimaler Schreibweise und im ASCII-Format zurück.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
```syntaxsql
DBCC OUTPUTBUFFER ( session_id [ , request_id ])  
[ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *session_id*  
 Die Sitzungs-ID, die jeweils einer aktiven primären Verbindung zugeordnet ist.  
  
 *request_id*  
 Die genaue Anforderung (Batch), nach der in der aktuellen Sitzung gesucht werden soll.  
 Die folgende Abfrage gibt *request_id*zurück:  
  
```sql
SELECT request_id   
FROM sys.dm_exec_requests   
WHERE session_id = @@spid;  
```  
  
 WITH  
 Lässt die Angabe von Optionen zu.  
  
 NO_INFOMSGS  
 Unterdrückt alle Informationsmeldungen mit einem Schweregrad von 0 bis 10.  
  
## <a name="remarks"></a>Bemerkungen  
DBCC OUTPUTBUFFER zeigt die Ergebnisse an, die an den angegebenen Client (*session_id*) gesendet wurden. Bei Prozessen, die keine Ausgabedatenströme umfassen, wird eine Fehlermeldung ausgegeben.
  
Führen Sie DBCC INPUTBUFFER aus, um die ausgeführte Anweisung anzuzeigen, die die von DBCC OUTPUTBUFFER dargestellten Ergebnisse zurückgegeben hat.
  
## <a name="result-sets"></a>Resultsets  
DBCC OUTPUTBUFFER gibt Folgendes zurück (die tatsächlichen Werte können davon abweichen):
  
```sql
Output Buffer                                                              
------------------------------------------------------------------------   
01fb8028:  04 00 01 5f 00 00 00 00 e3 1b 00 01 06 6d 00 61  ..._.........m.a  
01fb8038:  00 73 00 74 00 65 00 72 00 06 6d 00 61 00 73 00  .s.t.e.r..m.a.s.  
'...'  
01fb8218:  04 17 00 00 00 00 00 d1 04 18 00 00 00 00 00 d1  ................  
01fb8228:   .  
  
(33 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel werden die Informationen zum aktuellen Ausgabepuffer für eine angenommene Sitzungs-ID von `52`zurückgegeben.
  
```sql
DBCC OUTPUTBUFFER (52);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
[Ablaufverfolgungsflags &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  
