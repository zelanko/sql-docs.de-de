---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 934683cfca1a9a9c0596071824c21a0045e6ebab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85051156"
---
# <a name="localdb_error_insufficient_buffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
    
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
  
  
