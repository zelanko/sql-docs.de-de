---
title: MSSQLSERVER_5515 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: f3da12118485c8aa64a493529914cd83094695b9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver5515"></a>MSSQLSERVER_5515
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|5515|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FS_OPEN_CONTAINER_FAILED|  
|Meldungstext|Das Containerverzeichnis ''%.*ls'' der FILESTREAM-Datei kann nicht geöffnet werden. Das Betriebssystem hat den Windows-Statuscode 0x%x zurückgegeben.|  
  
## <a name="explanation"></a>Erklärung  
Das angegebene Containerverzeichnis der FILESTREAM-Datei kann nicht geöffnet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
Die Ursache des Fehlers finden Sie im angegebenen Windows-Statuscode.  
  
