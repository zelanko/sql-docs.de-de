---
title: '@@IDLE (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@IDLE_TSQL'
- '@@IDLE'
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], idle
- ticks [SQL Server]
- '@@IDLE function'
- status information [SQL Server], idle time
- idle time [SQL Server]
ms.assetid: 8f49c62a-8da5-4afd-a5eb-4df8ef8be755
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c17b356a3409128e0fedd9378d82cf0acb7d8781
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894312"
---
# <a name="x40x40idle-transact-sql"></a>&#x40;&#x40;IDLE (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Zeit zurück, während der sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seit dem letzten Start im Leerlauf befunden hat. Das Ergebnis wird in CPU-Zeiteinheiten oder "Takten" angegeben. Es ist für alle CPUs kumulativ und kann also höher sein als die tatsächlich abgelaufende Zeit. Führen Sie eine Multiplikation mit @@TIMETICKS durch, um einen Wert in Mikrosekunden zu konvertieren.  
  
> [!NOTE]  
>  Wenn die Zeit, die in @@CPU_BUSY oder @@IO_BUSY zurückgegeben wird, die kumulierte CPU-Zeit um etwa 49 Tage überschreitet, wird eine Warnung zu einem arithmetischen Überlauf ausgegeben. In diesem Fall sind die Werte der Variablen @@CPU_BUSY, @@IO_BUSY und @@IDLE nicht zutreffend.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
@@IDLE  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **integer**  
  
## <a name="remarks"></a>Bemerkungen  
 Zur Anzeige eines Berichts, der mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Statistiken enthält, führen Sie **sp_monitor** aus.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie die Millisekunden zurückgegeben werden, während derer sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zwischen der Startzeit und der aktuellen Zeit im Leerlauf befand. Damit das Konvertieren des Wertes in Mikrosekunden keinen arithmetischen Überlauf zur Folge hat, wird in dem Beispiel einer der Werte in den Datentyp `float` konvertiert.  
  
```  
SELECT @@IDLE * CAST(@@TIMETICKS AS float) AS 'Idle microseconds',  
   GETDATE() AS 'as of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
I  
Idle microseconds  as of                   
----------------- ----------------------  
8199934           12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)   
 [System Statistical Functions &#40;Transact-SQL&#41; (Statistische Systemfunktionen (Transact-SQL))](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
