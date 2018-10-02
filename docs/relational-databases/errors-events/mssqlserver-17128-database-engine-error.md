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
manager: craigg
ms.openlocfilehash: 1b06392073917d16b27846f7233f798871f8fa14
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729318"
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17128|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|INIT_NOBUFSPACE|  
|Meldungstext|initdata: Nicht genügend Arbeitsspeicher für Kernelpuffer.|  
  
## <a name="explanation"></a>Erklärung  
Die ursprünglichen Speicherbelegungen oder -reservierungen des Pufferpools sind fehlgeschlagen, und SQL Server wird beendet.  
  
## <a name="user-action"></a>Benutzeraktion  
Wird normalerweise durch das Starten von SQL Server auf einem Computer mit extrem geringer Kapazität (unter den minimalen Systemanforderungen) verursacht.  
  
