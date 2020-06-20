---
title: MSSQLSERVER_7901 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fae6e55cbe7170f795aff85400da2c5cdaef780a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85032443"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7901|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Meldungstext|Die REPAIR-Anweisung wurde nicht verarbeitet. Diese Reparaturstufe wird nicht unterstützt, wenn sich die Datenbank im Notfallmodus befindet.|  
  
## <a name="explanation"></a>Erklärung  
 Die Datenbank befindet sich im Notfallmodus, und eine andere Reparaturstufe als REPAIR_ALLOW_DATA_LOSS wurde angegeben. Reparaturen können nicht im Notfallmodus durchgeführt werden, außer wenn REPAIR_ALLOW_DATA_LOSS angegeben ist.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie den Befehl erneut aus, und geben Sie die REPAIR_ALLOW_DATA_LOSS-Option an.  
  
  
