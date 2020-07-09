---
title: MSSQLSERVER_5515 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
author: MashaMSFT
ms.author: mathoma
robots: noindex,nofollow
ms.openlocfilehash: a9456aed02e9e1a2566bf0281dacd07f435af44b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728374"
---
# <a name="mssqlserver_5515"></a>MSSQLSERVER_5515
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
