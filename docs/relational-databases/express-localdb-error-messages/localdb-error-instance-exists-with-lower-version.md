---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b07c4eebc34872868da61d7af633d29f1758e313
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246067"
---
# <a name="localdb_error_instance_exists_with_lower_version"></a>LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Details  
  
| attribute | Wert |
| --------- | ----- |
|Produktname|SQL Server|  
|Ereignis-ID|258|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Es konnte keine lokale Datenbankinstanz der angegebenen Version erstellt werden. Eine Instanz mit diesem Namen ist zwar bereits vorhanden, aber deren Version ist niedriger als die angegebene Version.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene Instanz ist bereits vorhanden, aber ihre Version ist niedriger als angefordert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie die vorhandene Instanz, und wiederholen Sie den Vorgang.  
  
  
