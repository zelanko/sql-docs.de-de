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
ms.openlocfilehash: 8b21d9137483b7d7b76c6e91f0fd44363bf58f7c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85641793"
---
# <a name="localdb_error_insufficient_buffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
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
  
  
