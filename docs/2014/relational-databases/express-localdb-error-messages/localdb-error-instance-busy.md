---
title: LOCALDB_ERROR_INSTANCE_BUSY | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0ed9d0f8-3297-4e31-a3e9-4a827f381789
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: af0971ab3bf12b13f46ad5c4533b7ee57877c26a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159504"
---
# <a name="localdberrorinstancebusy"></a>LOCALDB_ERROR_INSTANCE_BUSY
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|274|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Der angeforderte Vorgang für die lokale Datenbankinstanz kann nicht ausgeführt werden, weil die angegebene Instanz gerade verwendet wird. Beenden Sie die Instanz, und wiederholen Sie den Vorgang.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene Instanz wird ausgeführt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stoppen Sie die angegebene Laufzeitinstanz der lokalen Datenbank, und versuchen Sie es erneut.  
  
  