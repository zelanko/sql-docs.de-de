---
title: MSSQLSERVER_9692 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7041aa3e2262932541c4d81fe93dd1d9a740c97a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "67903813"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9692|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SB2_CANT_LISTEN_PORT_IN_USE|  
|Meldungstext|Der %S_MSG-Protokolltransport kann nicht an Port %d lauschen, weil er von einem anderen Prozess verwendet wird|  
  
## <a name="explanation"></a>Erklärung  
Ein anderes Programm auf dem Computer verwendet den angegebenen TCP-Port.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie **netstat -aon** aus, um zu bestimmen, welches Programm den Port verwendet. Deaktivieren Sie die entsprechende Anwendung, oder geben Sie einen anderen Port für Service Broker an.  
  
