---
description: '&#x40;&#x40;CPU_BUSY (Transact-SQL)'
title: CPU_BUSY (Transact-SQL)
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@CPU_BUSY_TSQL'
- '@@CPU_BUSY'
dev_langs:
- TSQL
helpviewer_keywords:
- CPU [SQL Server]
- status information [SQL Server], CPU
- ticks [SQL Server]
- time [SQL Server], CPU activity
- '@@CPU_BUSY function'
- statistical information [SQL Server], CPU
- CPU [SQL Server], activity
ms.assetid: 81ae0e64-79fa-4a74-9aa5-37045c4cd211
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8d921cdb5e8550942ade08f0e68d0337864d2e38
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91114853"
---
# <a name="x40x40cpu_busy-transact-sql"></a>&#x40;&#x40;CPU_BUSY (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Diese Funktion gibt die Zeit zurück, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seit dem letzten Start im aktiven Betrieb war. `@@CPU_BUSY` gibt ein in CPU-Zeitinkrementen ("Ticks") gemessenes Ergebnis zurück. Dieser Wert ist für alle CPUs kumulativ und kann daher höher sein als die tatsächlich verstrichene Zeit. Um den Wert in Mikrosekunden zu konvertieren, multiplizieren Sie ihn mit [@@TIMETICKS](./timeticks-transact-sql.md).
  
> [!NOTE]  
>  Wenn die in @@CPU_BUSY oder @@IO_BUSY zurückgegebene Zeit 49 Tage (näherungsweise) kumulierter CPU-Zeit überschreitet, erhalten Sie möglicherweise eine Warnung wegen arithmetischem Überlauf. In diesem Fall sind die Werte der Variablen `@@CPU_BUSY`, `@@IO_BUSY` und `@@IDLE` nicht genau.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
@@CPU_BUSY  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]


## <a name="return-types"></a>Rückgabetypen
**integer**
  
## <a name="remarks"></a>Hinweise  
Um einen Bericht anzuzeigen, der mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Statistiken enthält, einschließlich der CPU-Aktivität, führen Sie „[sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)“ aus.
  
## <a name="examples"></a>Beispiele  
Im diesem Beispiel werden die Rückgabewerte der CPU-Aktivität für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum aktuellen Datum und der aktuellen Uhrzeit angezeigt. Das Beispiel konvertiert einen der Werte in den Datentyp `float`. Dies vermeidet Probleme mit arithmetischem Überlauf bei der Berechnung von Werten in Mikrosekunden.
  
```sql
SELECT @@CPU_BUSY * CAST(@@TIMETICKS AS FLOAT) AS 'CPU microseconds',   
   GETDATE() AS 'As of' ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
CPU microseconds As of
---------------- -----------------------
18406250         2006-12-05 17:00:50.600
```
  
## <a name="see-also"></a>Siehe auch
[sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE &#40;Transact-SQL&#41;](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)  
[sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)  
[System Statistical Functions &#40;Transact-SQL&#41; (Statistische Systemfunktionen (Transact-SQL))](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  
