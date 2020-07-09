---
title: MSSQLSERVER_8642 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ced4c9b3e690b709be9d8f500ff2656cf6b5e220
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727427"
---
# <a name="mssqlserver_8642"></a>MSSQLSERVER_8642
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|8642|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|EXCHNGSTART_ERR|  
|Meldungstext|Der Abfrageprozessor konnte die erforderlichen Threadressourcen für die parallele Abfrageausführung nicht starten.|  
  
## <a name="explanation"></a>Erklärung  
Auf dem Server gibt es nicht genügend Threadressourcen.  
  
## <a name="user-action"></a>Benutzeraktion  
Verringern Sie die Last auf dem Server, und führen Sie die Abfrage erneut aus.  
  
