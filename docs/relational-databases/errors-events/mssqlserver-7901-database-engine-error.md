---
title: MSSQLSERVER_7901 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3eeee976a45817b155c86ae99bd2cbd229324d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601078"
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7901|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Meldungstext|Die REPAIR-Anweisung wurde nicht verarbeitet. Diese Reparaturstufe wird nicht unterstützt, wenn sich die Datenbank im Notfallmodus befindet.|  
  
## <a name="explanation"></a>Erklärung  
Die Datenbank befindet sich im Notfallmodus, und eine andere Reparaturstufe als REPAIR_ALLOW_DATA_LOSS wurde angegeben. Reparaturen können nicht im Notfallmodus durchgeführt werden, außer wenn REPAIR_ALLOW_DATA_LOSS angegeben ist.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie den Befehl erneut aus, und geben Sie die REPAIR_ALLOW_DATA_LOSS-Option an.  
  
