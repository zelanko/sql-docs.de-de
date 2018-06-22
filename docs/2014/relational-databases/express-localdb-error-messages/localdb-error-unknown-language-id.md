---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID | Microsoft Docs
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
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ad7e5dd5f24a966c6130a88a7f0fa4034070a2f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149885"
---
# <a name="localdberrorunknownlanguageid"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|270|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Fehler beim Abrufen der lokalisierten Fehlermeldung. Die im LanguageID-Parameter angegebene Sprache ist unbekannt.|  
  
## <a name="explanation"></a>Erklärung  
 Die angeforderte Sprache für die Laufzeitfehlermeldung der lokalen Datenbank ist unbekannt oder wird nicht unterstützt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie, eine der unterstützten Sprachen für Laufzeitfehlermeldungen der lokalen Datenbank oder eine Standardsprache anzufordern.  
  
  