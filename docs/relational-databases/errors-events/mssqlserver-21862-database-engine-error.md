---
title: MSSQLSERVER_21862 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f2dce4f256ca0bed1da86a6205e18e04c341f52
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321231"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|21862|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum21862|  
|Meldungstext|FILESTREAM-Spalten können nicht in einer Veröffentlichung mit der Synchronisierungsmethode 'database snapshot' oder 'database snapshot character' veröffentlicht werden.|  
  
## <a name="explanation"></a>Erklärung  
Da der Zugriff auf FILESTREAM-Daten über eine Datenbankmomentaufnahme nicht möglich ist, kann der Momentaufnahme-Agent FILESTREAM-Daten nicht lesen, wenn für die Synchronisierungsmethode der Veröffentlichung der *Datenbankmomentaufnahme* - oder der *database_snapshot_character*-Parameter angegeben wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
Verwenden Sie für die Veröffentlichung eine andere Synchronisierungsmethode als die *Datenbankmomentaufnahme* oder *database_snapshot_character*, oder schließen Sie die FILESTREAM-Spalte aus der Veröffentlichung aus.  
  
