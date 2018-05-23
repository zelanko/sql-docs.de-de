---
title: MSSQLSERVER_1803 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c2ea56f5845dca5478ddd16b9a5061cef733fc72
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver1803"></a>MSSQLSERVER_1803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1803|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NO_SPACE|  
|Meldungstext|Fehler bei CREATE DATABASE. Die primäre Datei muss mindestens %d MB haben, um eine Kopie der model-Datenbank aufnehmen zu können.|  
  
## <a name="explanation"></a>Erklärung  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt eine Datenbank aus einer Kopie der Modelldatenbank. Die Kopie wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umbenannt, und die neue Datenbank wird auf die angeforderte Größe vergrößert. In diesem Fall versuchte der Benutzer, eine Datenbank zu erstellen, die kleiner als die Modelldatenbank war. Der Vorgang ist fehlgeschlagen, da die Kopie der Modelldatenbank nicht in die primäre Datendatei gepasst hat, da die Datei kleiner als die Modelldatenbank war.  
  
## <a name="user-action"></a>Benutzeraktion  
Erstellen Sie die Datenbank, und geben Sie eine größere Datenbankdateigröße an. Verkleinern Sie dann ggf. die Datenbank mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder der DBCC SHRINKDATABASE-Anweisung.  
  
