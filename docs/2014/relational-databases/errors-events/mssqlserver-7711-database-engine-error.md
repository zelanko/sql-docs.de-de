---
title: MSSQLSERVER_7711 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec3bd035f1d8c3998189c819b9fdcf9fa98b1037
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62762661"
---
# <a name="mssqlserver_7711"></a>MSSQLSERVER_7711
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7711|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PRT_RANGE_OVERLAP|  
|Meldungstext|Die DATA_COMPRESSION-Option wurde für die Tabelle oder, sofern sie partitioniert ist, für mindestens eine ihrer Partitionen mehrfach angegeben.|  
  
## <a name="explanation"></a>Erklärung  
 In einer der folgenden Anweisungen ist ein Fehler in der DATA_COMPRESSION-Option aufgetreten:  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
 Wenn die angegebene Tabelle bzw. der angegebene Index partitioniert ist, wurde die DATA_COMPRESSION-Option für mindestens eine der Partitionen mehrfach aufgeführt. Wenn die Tabelle bzw. der Index nicht partitioniert ist, wurde die DATA_COMPRESSION-Option mehrfach angegeben.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie bei einer partitionierten Tabelle bzw. einem partitionierten Index sicher, dass die DATA_COMPRESSION-Option für jede Partition nur einmal angegeben wird. Verwenden Sie für eine nicht partitionierte Tabelle bzw. einen nicht partitionierten Index die DATA_COMPRESSION-Option nur einmal in der Anweisung.  
  
  
