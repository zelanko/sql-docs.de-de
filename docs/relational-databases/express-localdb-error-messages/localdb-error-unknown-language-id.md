---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
ms.openlocfilehash: 053fb88279d0aa2ad664e50d4b9c6bbb454f2adb
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245932"
---
# <a name="localdb_error_unknown_language_id"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Details  
  
| attribute | Wert |
| --------- | ----- |
|Produktname|SQL Server|  
|Ereignis-ID|270|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Fehler beim Abrufen der lokalisierten Fehlermeldung. Die im LanguageID-Parameter angegebene Sprache ist unbekannt.|  
  
## <a name="explanation"></a>Erklärung  
 Die angeforderte Sprache für die Laufzeitfehlermeldung der lokalen Datenbank ist unbekannt oder wird nicht unterstützt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie, eine der unterstützten Sprachen für Laufzeitfehlermeldungen der lokalen Datenbank oder eine Standardsprache anzufordern.  
  
  
