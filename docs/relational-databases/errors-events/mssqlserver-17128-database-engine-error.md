---
description: MSSQLSERVER_17128
title: MSSQLSERVER_17128 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1902d498a93555957b0c240d349a951327086382
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88410986"
---
# <a name="mssqlserver_17128"></a>MSSQLSERVER_17128
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
|Ereignis-ID|17128|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|INIT_NOBUFSPACE|  
|Meldungstext|initdata: Nicht genügend Arbeitsspeicher für Kernelpuffer.|  
  
## <a name="explanation"></a>Erklärung  
Die ursprünglichen Speicherbelegungen oder -reservierungen des Pufferpools sind fehlgeschlagen, und SQL Server wird beendet.  
  
## <a name="user-action"></a>Benutzeraktion  
Wird normalerweise durch das Starten von SQL Server auf einem Computer mit extrem geringer Kapazität (viel geringer als die minimalen Systemanforderungen) verursacht.  
  
