---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94439a6981a2cf891a55bcbda7498db83e1fa52e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62990570"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|260|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Die vollständige Pfadlänge des Ordners der lokalen Datenbankinstanz ist länger als MAX_PATH. Die Instanz muss im Ordner gespeichert werden: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server lokale DB\Instances\\< Instanzname\>.|  
  
## <a name="explanation"></a>Erklärung  
 Der Pfad, unter dem die Instanz gespeichert werden soll, ist länger als MAX_PATH.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erstellen Sie einen neuen Pfad, der kürzer als MAX_PATH ist.  
  
  
