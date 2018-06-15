---
title: MSSQLSERVER_7910 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 30d3ce8149e5f805bc583737b75d7387347f15ca
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34324381"
---
# <a name="mssqlserver7910"></a>MSSQLSERVER_7910
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7910|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_PAGE_ALLOCATED|  
|Meldungstext|Reparaturvorgang: Die Seite P_ID wurde der Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (Typ TYPE) zugeordnet.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist eine Informationsmeldung von REPAIR, die besagt, dass eine Seite dem Einzelseiten-Slotarray einer IAM-Seite (Index Allocation Map) zugeordnet wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
InclusionThresholdSetting  
  
