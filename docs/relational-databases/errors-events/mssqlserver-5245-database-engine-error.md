---
title: MSSQLSERVER_5245 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1d0c05f5439bbeea03895a4c0611b1aca6f35ed
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68062620"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5245|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Meldungstext|Objekt-ID O_ID ('NAME'-Objekt): DBCC konnte keine Sperre für dieses Objekt erhalten, da das Timeout für die Sperranforderung überschritten wurde. Das Objekt wurde ausgelassen und wird nicht verarbeitet.|  
  
## <a name="explanation"></a>Erklärung  
Ein Sperrtimeout ist aufgetreten, während DBCC auf eine Tabellensperre für das angegebene Objekt gewartet hat.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie den DBCC-Befehl erneut aus.  
  
