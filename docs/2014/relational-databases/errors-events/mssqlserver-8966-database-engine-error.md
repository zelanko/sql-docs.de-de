---
title: MSSQLSERVER_8966 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8bf378f38acb4efd25d4cd62ccab0613dfc9f94d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418169"
---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8966|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|Meldungstext|Die Seite P_ID konnte nicht gelesen und mit dem Latchtyp TYPE versehen werden. Fehler bei OPERATION.|  
  
## <a name="explanation"></a>Erklärung  
 Es ist ein Fehler bei einem Seitenlesevorgang aufgetreten, oder ein Latch konnte nicht auf einer PFS- oder GAM-Seite verwendet werden. Möglicherweise werden im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll ein Latchtimeout oder andere damit verbundenen Meldungen angezeigt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie das SQL-Fehlerprotokoll auf zugehörige Meldungen, und begeben Sie die Fehler.  
  
  
