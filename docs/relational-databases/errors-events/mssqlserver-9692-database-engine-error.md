---
description: MSSQLSERVER_9692
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
ms.openlocfilehash: 8bf2d195fcb46ecc4cfd5e5f295542b76fc8b3bb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460851"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
