---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d4053fd7633d642c0cc139826ca8e30ed3fa3fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777788"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
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
  
  
