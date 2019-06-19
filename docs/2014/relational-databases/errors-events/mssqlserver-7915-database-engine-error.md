---
title: MSSQLSERVER_7915 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fb60bfa05e75c06b7da04042aa1abfbd42b756c0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62761905"
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7915|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Meldungstext|Reparaturvorgang: IAM-Kette für Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, zuordnungseinheits-ID A_ID (Type-Typ) wurde vor Seite P_ID abgeschnitten und wird neu erstellt.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist eine Informationsmeldung, die von REPAIR gesendet wurde und anzeigt, dass die angegebene IAM-Kette (Index Allocation Map) gepatcht wurde, damit sie neu erstellt werden konnte. Für diesen Patch war möglicherweise die Zuordnung eines neuen Kopfteils der IAM-Kette oder die Entfernung von fehlerhaften Seiten aus der Kette erforderlich.  
  
## <a name="user-action"></a>Benutzeraktion  
 None  
  
  
