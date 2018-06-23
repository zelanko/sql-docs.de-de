---
title: MSSQLSERVER_7916 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b6f885042c469bab28ed15e0e18ba39a5a94f17f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046911"
---
# <a name="mssqlserver7916"></a>MSSQLSERVER_7916
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7916|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_RECORD_DELETED|  
|Meldungstext|Reparaturvorgang: Der Datensatz für Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (TYPE-Typ) auf der Seite P_ID, Slot S_ID wurde gelöscht. Die Indizes werden neu erstellt.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist eine Informationsmeldung von REPAIR, die angibt, dass der angegebene Datensatz aus der Seite gelöscht wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 InclusionThresholdSetting  
  
  