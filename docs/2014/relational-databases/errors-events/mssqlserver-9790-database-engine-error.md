---
title: MSSQLSERVER_9790 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: abc78d3fa5ef749afc32a9a7efab6c9df9a15223
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048738"
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9790|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Meldungstext|Die eingehende Nachricht kann nicht geroutet werden. Die MSDB-Systemdatenbank, die Routinginformationen enthält, befindet sich im Einzelbenutzermodus.|  
  
## <a name="explanation"></a>Erklärung  
 Beim Klassifizieren einer empfangenen Nachricht ist ein Fehler aufgetreten, da die MSDB-Datenbank im SINGLE USER-Modus war.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie die MSDB-Datenbank mit dem Befehl ALTER DATABASE auf den MULTI USER-Modus.  
  
  