---
title: MSSQLSERVER_7711 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f9dd9ab3600f51cc44b8678b050e8d61ffb2a63
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414339"
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
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
  
  
