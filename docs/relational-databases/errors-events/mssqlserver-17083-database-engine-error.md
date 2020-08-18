---
description: MSSQLSERVER_17083
title: MSSQLSERVER_17083 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c897b6ee380afc7882b39bca62234d509d29f80f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88332846"
---
# <a name="mssqlserver_17083"></a>MSSQLSERVER_17083
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|17083|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|P3_HEKATON_NOT_ATOMIC|  
|Meldungstext|Der Text einer systemintern kompilierten gespeicherten Prozedur muss ein ATOMIC-Block sein.|  
  
## <a name="explanation"></a>Erklärung  
Der Text einer systemintern kompilierten gespeicherten Prozedur enthielt keinen ATOMIC-Block.  
  
## <a name="user-action"></a>Benutzeraktion  
Eine systemintern kompilierte gespeicherte Prozedur muss einen ATOMIC-Block enthalten. Beispiel:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
