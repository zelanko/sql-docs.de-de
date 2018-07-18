---
title: MSSQLSERVER_7915 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21c43e914c933463028e6815f698ee6c1c71a5de
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34324941"
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7915|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Meldungstext|Reparaturvorgang: Die IAM-Kette für Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (Typ TYPE), wurde vor Seite P_ID abgeschnitten und wird neu erstellt.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist eine Informationsmeldung, die von REPAIR gesendet wurde und anzeigt, dass die angegebene IAM-Kette (Index Allocation Map) gepatcht wurde, damit sie neu erstellt werden konnte. Für diesen Patch war möglicherweise die Zuordnung eines neuen Kopfteils der IAM-Kette oder die Entfernung von fehlerhaften Seiten aus der Kette erforderlich.  
  
## <a name="user-action"></a>Benutzeraktion  
InclusionThresholdSetting  
  
