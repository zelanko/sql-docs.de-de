---
title: MSSQLSERVER_2519 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c892653a8ba283095e5b3ae58d09992571ba1e7c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2519|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_NO_EXPRESSION_EVALUATOR|  
|Meldungstext|Berechnete Spalten und benutzerdefinierte Typen können für die Objekt-ID ID O_ID ("O_NAME"-Objekt) nicht überprüft werden, weil die interne Ausdrucksauswertung nicht initialisiert werden konnte.|  
  
## <a name="explanation"></a>Erklärung  
Die Informationsmeldung gibt an, dass DBCC vom Abfrageprozessor kein internes Objekt zur Verfügung gestellt werden konnte, um die Auswertung berechneter Spalten und benutzerdefinierter CLR-Typen (Common Language Runtime) zu ermöglichen. Dies bedeutet, dass berechnete Spalten und benutzerdefinierte CLR-Typen nicht auf ihre Richtigkeit hin überprüft oder verwendet werden, wenn von DBCC die Konsistenz zwischen Indizes und Basistabellen überprüft wird.  
  
## <a name="user-action"></a>Benutzeraktion  
Keine  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
