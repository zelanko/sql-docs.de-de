---
title: MSSQLSERVER_2519 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec6663028f2c0e133996053a31acfc0e04b49738
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914679"
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2519|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_NO_EXPRESSION_EVALUATOR|  
|Meldungstext|Berechnete Spalten und benutzerdefinierte Typen können für die Objekt-ID ID O_ID ("O_NAME"-Objekt) nicht überprüft werden, weil die interne Ausdrucksauswertung nicht initialisiert werden konnte.|  
  
## <a name="explanation"></a>Erklärung  
 Die Informationsmeldung gibt an, dass DBCC vom Abfrageprozessor kein internes Objekt zur Verfügung gestellt werden konnte, um die Auswertung berechneter Spalten und benutzerdefinierter CLR-Typen (Common Language Runtime) zu ermöglichen. Dies bedeutet, dass berechnete Spalten und benutzerdefinierte CLR-Typen nicht auf ihre Richtigkeit hin überprüft oder verwendet werden, wenn von DBCC die Konsistenz zwischen Indizes und Basistabellen überprüft wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 None  
  
## <a name="see-also"></a>Siehe auch  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
