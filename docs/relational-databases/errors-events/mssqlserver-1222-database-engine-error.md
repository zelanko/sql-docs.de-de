---
title: MSSQLSERVER_1222 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99add77f12934928a72354e40e87b5025bdd6ec7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72908639"
---
# <a name="mssqlserver_1222"></a>MSSQLSERVER_1222
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1222|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LK_TIMEOUT|  
|Meldungstext|Das Timeout für Sperranforderung wurde überschritten.|  
  
## <a name="explanation"></a>Erklärung  
Eine erforderliche Ressource wurde durch eine weitere Transaktion länger gesperrt, als diese Abfrage warten konnte.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie die folgenden Aufgaben aus, um das Problem zu beheben:  
  
1.  Lokalisieren Sie nach Möglichkeit die Transaktion, durch die die erforderliche Ressource gesperrt wird. Verwenden Sie die dynamischen Verwaltungssichten **sys.dm_os_waiting_tasks** und **sys.dm_tran_locks**.  
  
2.  Beenden Sie gegebenenfalls die Transaktion, wenn die Sperre durch die Transaktion weiterhin besteht.  
  
3.  Führen Sie die Abfrage erneut aus.  

Ändern Sie das Sperrtimeout oder die problematischen Transaktionen, sodass die Sperre für eine kürzere Zeit besteht, wenn der Fehler häufiger auftritt.  
  
