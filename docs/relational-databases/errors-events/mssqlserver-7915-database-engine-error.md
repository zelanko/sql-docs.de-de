---
description: MSSQLSERVER_7915
title: MSSQLSERVER_7915 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6627ee24fc9b5f3e53334c8b085aef2698835e11
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448729"
---
# <a name="mssqlserver_7915"></a>MSSQLSERVER_7915
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|7915|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Meldungstext|Reparaturvorgang: Die IAM-Kette für Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (Typ TYPE), wurde vor Seite P_ID abgeschnitten und wird neu erstellt.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist eine Informationsmeldung, die von REPAIR gesendet wurde und anzeigt, dass die angegebene IAM-Kette (Index Allocation Map) gepatcht wurde, damit sie neu erstellt werden konnte. Für diesen Patch war möglicherweise die Zuordnung eines neuen Kopfteils der IAM-Kette oder die Entfernung von fehlerhaften Seiten aus der Kette erforderlich.  
  
## <a name="user-action"></a>Benutzeraktion  
Keine  
  
