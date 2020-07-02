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
ms.openlocfilehash: 488199547cd5b96190b30ab415b08f9be2b4bd66
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85641271"
---
# <a name="localdb_error_unknown_language_id"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|270|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Fehler beim Abrufen der lokalisierten Fehlermeldung. Die im LanguageID-Parameter angegebene Sprache ist unbekannt.|  
  
## <a name="explanation"></a>Erklärung  
 Die angeforderte Sprache für die Laufzeitfehlermeldung der lokalen Datenbank ist unbekannt oder wird nicht unterstützt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie, eine der unterstützten Sprachen für Laufzeitfehlermeldungen der lokalen Datenbank oder eine Standardsprache anzufordern.  
  
  
