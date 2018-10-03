---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1084075fe90a752a07a7abc1feb46679bd9cf5d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058044"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|260|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Die vollständige Pfadlänge des Ordners der lokalen Datenbankinstanz ist länger als MAX_PATH. Die Instanz muss im Ordner gespeichert werden: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server lokale DB\Instances\\< Instanzname\>.|  
  
## <a name="explanation"></a>Erklärung  
 Der Pfad, unter dem die Instanz gespeichert werden soll, ist länger als MAX_PATH.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erstellen Sie einen neuen Pfad, der kürzer als MAX_PATH ist.  
  
  
