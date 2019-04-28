---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b16cd79186357dafd07fa5f0f19dee05b03722f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990442"
---
# <a name="localdberrorinsufficientbuffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|276|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Der an die API-Methode der lokalen Datenbankinstanz übergebene Puffer ist nicht groß genug.|  
  
## <a name="explanation"></a>Erklärung  
 Der Eingabepuffer ist zu kurz. Abschneiden wurde nicht angefordert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie einen Puffer von der angegebenen Größe bereit.  
  
  
