---
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
ms.openlocfilehash: 210df5d533908e75e83b348ac6c9a84a22198f4b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68131815"
---
# <a name="mssqlserver_17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
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
  
