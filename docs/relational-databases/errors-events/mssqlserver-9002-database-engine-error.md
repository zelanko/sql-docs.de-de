---
title: MSSQLSERVER_9002 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6e888a44cd96eeaa93f49c02128e48763b66a9ee
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85636637"
---
# <a name="mssqlserver_9002"></a>MSSQLSERVER_9002
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|9002|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOG_IS_FULL|  
|Meldungstext|Das Transaktionsprotokoll für die '%.*ls'-Datenbank ist voll. Die log_reuse_wait_desc-Spalte von sys.databases enthält Informationen dazu, warum Protokollspeicherplatz nicht erneut verwendet werden kann.|  
  
## <a name="explanation"></a>Erklärung  
Das Datenbankprotokoll hat nicht mehr genügend Speicherplatz zur Verfügung. Die **log_reuse_wait_desc**-Spalte in **sys.databases** beschreibt, warum Protokollspeicherplatz nicht erneut verwendet werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
Bestimmen Sie mit **sys.databases**, warum das Protokoll voll ist, und korrigieren Sie dann die Bedingung. Weitere Informationen finden Sie unter „Problembehandlung bei vollen Transaktionsprotokollen (Fehler 9002)“ in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
[Problembehandlung bei vollen Transaktionsprotokollen &#40;SQL Server-Fehler 9002&#41;](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
