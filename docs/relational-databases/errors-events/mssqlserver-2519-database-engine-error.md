---
title: MSSQLSERVER_2519 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 233d7d3a6ae29fe2e83272f36ed3e952e8bdd1dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138480"
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
## <a name="see-also"></a>Weitere Informationen  
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
