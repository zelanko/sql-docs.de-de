---
title: MSSQLSERVER_3417 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: da66b69ab130bc45e7d52c7ef87f59d00194ee6d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795148"
---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3417|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REC_BADMASTER|  
|Meldungstext|Die master-Datenbank kann nicht wiederhergestellt werden. SQL Server kann nicht ausgeführt werden. Stellen Sie die master-Datenbank von einer vollständigen Sicherung wieder her, reparieren Sie sie, oder erstellen Sie sie neu. Weitere Informationen zum Neuerstellen der master-Datenbank finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Die **master**-Datenbank kann von SQL Server nicht gestartet werden. Wenn die Datenbanken **master** oder **tempdb** nicht in den Onlinemodus gebracht werden können, kann SQL Server nicht ausgeführt werden. Diesem Fehler sind normalerweise andere Fehler vorausgegangen. Überprüfen Sie die Fehlerprotokolle, um die eigentliche Ursache des Fehlers zu finden.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie eine Sicherung der Datenbank wieder her, oder reparieren Sie die Datenbank.  
  
