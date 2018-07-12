---
title: MSSQLSERVER_17128 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 271533cfd9ab0cdec919e5a885e0334caa4beaab
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428859"
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
    
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
  
  
