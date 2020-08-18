---
description: MSSQLSERVER_8966
title: MSSQLSERVER_8966 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0359c734fae801d7f1c2dded751043f8d1ae5d1f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88331486"
---
# <a name="mssqlserver_8966"></a>MSSQLSERVER_8966
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|8966|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|Meldungstext|Die Seite P_ID konnte nicht gelesen und mit dem Latchtyp TYPE versehen werden. Fehler bei OPERATION.|  
  
## <a name="explanation"></a>Erklärung  
Es ist ein Fehler bei einem Seitenlesevorgang aufgetreten, oder ein Latch konnte nicht auf einer PFS- oder GAM-Seite verwendet werden. Möglicherweise werden im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll ein Latchtimeout oder andere damit verbundenen Meldungen angezeigt.  
  
## <a name="user-action"></a>Benutzeraktion  
Überprüfen Sie das SQL-Fehlerprotokoll auf zugehörige Meldungen, und begeben Sie die Fehler.  
  
