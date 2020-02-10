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
manager: craigg
ms.openlocfilehash: faf43de11a0c1779f043c6dd854e361c0396dc6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913568"
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
  
  
