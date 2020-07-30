---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 636080d7247345cca8f6a6b74fbd19c9e8a487d9
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246147"
---
# <a name="localdb_error_instance_already_shared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Details  
  
| attribute | Wert |
| --------- | ----- |
|Produktname|SQL Server|  
|Ereignis-ID|284|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Die angegebene lokale Datenbankinstanz ist bereits freigegeben.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene lokale Datenbankinstanz ist bereits unter einem anderen Freigabenamen freigegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
 Heben Sie die Freigabe der freigegebenen Instanz auf, bevor Sie sie erneut unter einem anderen Freigabenamen freigeben.  
  
  
