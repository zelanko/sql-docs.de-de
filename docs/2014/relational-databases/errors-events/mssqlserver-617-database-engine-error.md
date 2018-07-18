---
title: MSSQLSERVER_617 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f79f2f585eeffde4cb7e81a322a7b5c089f5212a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430999"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
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
  
  
