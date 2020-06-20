---
title: MSSQLSERVER_11409 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3afbea77db6fa0685644ed7a55ef31a9050b0cfc
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968030"
---
# <a name="mssqlserver_11409"></a>MSSQLSERVER_11409
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|11409|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|ALTERCOL_COLSET_DROP|  
|Meldungstext|Der '%.*ls'-Spaltensatz in der '%.\*ls'-Tabelle kann nicht entfernt werden, da die Tabelle mehr als 1025 Spalten enthält.|  
  
## <a name="explanation"></a>Erklärung  
 Tabellen können maximal 1024 Spalten enthalten, die nicht als Spalte mit geringer Dichte oder berechnete Spalte festgelegt sind. Wenn die Tabelle aufgrund von Sparsespalten mehr als 1024 Spalten aufweist, muss für die Tabelle ein Spaltensatz definiert werden. Die Tabelle, auf die verwiesen wird, weist mehr als 1024 Spalten auf, und Sie haben versucht, den Spaltensatz zu entfernen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Mit den aktuellen Spalten in der Tabelle müssen Sie den Spaltensatz beibehalten.  
  
 Zum Entfernen des Spaltensatzes entfernen Sie zunächst Spalten aus der Tabelle, bis nur noch 1024 Spalten enthalten sind. Dann können Sie den Spaltensatz entfernen.  
  
  
