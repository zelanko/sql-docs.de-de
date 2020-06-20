---
title: MSSQLSERVER_1803 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969440"
---
# <a name="mssqlserver_1803"></a>MSSQLSERVER_1803
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1803|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NO_SPACE|  
|Meldungstext|Fehler bei CREATE DATABASE. Die primäre Datei muss mindestens %d MB haben, um eine Kopie der model-Datenbank aufnehmen zu können.|  
  
## <a name="explanation"></a>Erklärung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt eine Datenbank aus einer Kopie der Modelldatenbank. Die Kopie wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umbenannt, und die neue Datenbank wird auf die angeforderte Größe vergrößert. In diesem Fall versuchte der Benutzer, eine Datenbank zu erstellen, die kleiner als die Modelldatenbank war. Der Vorgang ist fehlgeschlagen, da die Kopie der Modelldatenbank nicht in die primäre Datendatei gepasst hat, da die Datei kleiner als die Modelldatenbank war.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erstellen Sie die Datenbank, und geben Sie eine größere Datenbankdateigröße an. Verkleinern Sie dann ggf. die Datenbank mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder der DBCC SHRINKDATABASE-Anweisung.  
  
  
