---
title: MSSQLSERVER_9790 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5747a13e60182596610f25dd4ed1243670ff5018
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62912174"
---
# <a name="mssqlserver_9790"></a>MSSQLSERVER_9790
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9790|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Meldungstext|Die eingehende Nachricht kann nicht geroutet werden. Die MSDB-Systemdatenbank, die Routinginformationen enthält, befindet sich im Einzelbenutzermodus.|  
  
## <a name="explanation"></a>Erklärung  
 Beim Klassifizieren einer empfangenen Nachricht ist ein Fehler aufgetreten, da die MSDB-Datenbank im SINGLE USER-Modus war.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie die MSDB-Datenbank mit dem Befehl ALTER DATABASE auf den MULTI USER-Modus.  
  
  
