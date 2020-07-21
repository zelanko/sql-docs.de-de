---
title: MSSQLSERVER_617 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31953e9f8cef351819d5b1cd47195e9bf9308738
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551105"
---
# <a name="mssqlserver_617"></a>MSSQLSERVER_617
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|617|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NODESHASH|  
|Meldungstext|Der Deskriptor für die Objekt-ID %ld in der Datenbank mit der ID %d wurde in der Hashtabelle beim Versuch, ihn aus dieser zu entfernen, nicht gefunden. In einer Arbeitstabelle fehlt ein Eintrag. Führen Sie die Abfrage erneut aus. Falls ein Cursor beteiligt ist, schließen Sie den Cursor, und öffnen Sie ihn erneut.|  
  
## <a name="explanation"></a>Erklärung  
 SQL Server kann die Arbeitstabelle für einen bestimmten Eintrag nicht finden.  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Falls ein Cursor beteiligt ist, schließen Sie den Cursor, und öffnen Sie ihn dann erneut.  
  
2.  Führen Sie die Abfrage erneut aus.  
  
  
