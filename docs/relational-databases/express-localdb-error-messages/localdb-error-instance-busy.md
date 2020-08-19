---
description: LOCALDB_ERROR_INSTANCE_BUSY
title: LOCALDB_ERROR_INSTANCE_BUSY | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 0ed9d0f8-3297-4e31-a3e9-4a827f381789
author: stevestein
ms.author: sstein
ms.openlocfilehash: 663b37d3667ce3751f78d322415ae80677ac3f02
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475899"
---
# <a name="localdb_error_instance_busy"></a>LOCALDB_ERROR_INSTANCE_BUSY
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Details  
  
| attribute | Wert |
| --------- | ----- |
|Produktname|SQL Server|  
|Ereignis-ID|274|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Der angeforderte Vorgang für die lokale Datenbankinstanz kann nicht ausgeführt werden, weil die angegebene Instanz gerade verwendet wird. Beenden Sie die Instanz, und wiederholen Sie den Vorgang.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene Instanz wird ausgeführt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stoppen Sie die angegebene Laufzeitinstanz der lokalen Datenbank, und versuchen Sie es erneut.  
  
  
