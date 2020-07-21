---
title: MSSQLSERVER_1461 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aaaa21c18a2bf7726b2b8df2e6f2886409cf7ab2
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553795"
---
# <a name="mssqlserver_1461"></a>MSSQLSERVER_1461
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1461|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_SAFETY_MISMATCH|  
|Meldungstext|Für die "%.*ls"-Datenbank wurden bei den Servern unterschiedliche Sicherheitsstufen für die Datenbankspiegelung gefunden. Die Sicherheitsstufe FULL wird verwendet.|  
  
## <a name="explanation"></a>Erklärung  
 Die Spiegelungsverbindungen wurden unterbrochen, als die Sicherheitsstufe der Transaktion geändert wurde, da die Sicherheitseinstellungen der Transaktion für die Prinzipal- und Spiegeldatenbank inkonsistent waren. Es wird die Standardsicherheitseinstellung der Sicherheit für vollständige Transaktionen verwendet. Die Sitzung wird im Modus für hohe Sicherheit ausgeführt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie die Transaktionssicherheit initiieren möchten, führen Sie die ALTER DATABASE *Datenbank_Name* SET PARTNER SAFETY OFF-Anweisung für die Prinzipaldatenbank erneut aus.  
  
  
