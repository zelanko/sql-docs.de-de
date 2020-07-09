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
ms.openlocfilehash: 9d246ea9033bac031da85fe4dddd968ebb9af07d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723506"
---
# <a name="mssqlserver_3417"></a>MSSQLSERVER_3417
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|3417|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REC_BADMASTER|  
|Meldungstext|Die master-Datenbank kann nicht wiederhergestellt werden. SQL Server kann nicht ausgeführt werden. Stellen Sie die master-Datenbank von einer vollständigen Sicherung wieder her, reparieren Sie sie, oder erstellen Sie sie neu. Weitere Informationen zum Neuerstellen der master-Datenbank finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Die **master**-Datenbank kann von SQL Server nicht gestartet werden. Wenn die Datenbanken **master** oder **tempdb** nicht in den Onlinemodus gebracht werden können, kann SQL Server nicht ausgeführt werden. Diesem Fehler sind normalerweise andere Fehler vorausgegangen. Überprüfen Sie die Fehlerprotokolle, um die eigentliche Ursache des Fehlers zu finden.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie eine Sicherung der Datenbank wieder her, oder reparieren Sie die Datenbank.  
  
