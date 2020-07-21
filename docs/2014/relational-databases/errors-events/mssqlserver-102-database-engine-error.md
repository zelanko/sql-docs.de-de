---
title: MSSQLSERVER_102 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa6c196eb323497817753abda7cdccb0492cd286
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554195"
---
# <a name="mssqlserver_102"></a>MSSQLSERVER_102
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|102|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|P_SYNTAXERR2|  
|Meldungstext|Falsche Syntax in der Nähe von '%.*ls'.|  
  
## <a name="explanation"></a>Erklärung  
 Gibt einen Syntaxfehler an. Weitere Informationen sind nicht verfügbar, da der Fehler verhindert, dass das [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Anweisung verarbeitet.  
  
 Eine mögliche Ursache ist, dass versucht wurde, mit der veralteten RC4- oder RC4_128-Verschlüsselung einen symmetrischen Schlüssel zu erstellen und der Kompatibilitätsmodus nicht auf 90 oder 100 festgelegt war.  
  
## <a name="user-action"></a>Benutzeraktion  
 Suchen Sie in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung nach Syntaxfehlern.  
  
 Wenn Sie mit RC4 oder RC4_128 einen symmetrischen Schlüssel erstellen, wählen Sie eine neuere Verschlüsselung aus, z. B. einen der AES-Algorithmen. (Empfohlen.) Wenn RC4 erforderlich ist, verwenden Sie die Anweisung ALTER DATABASE SET COMPATIBILITY_LEVEL, um den Kompatibilitätsgrad der Datenbank auf 90 oder 100 festzulegen. (Nicht empfohlen.)  
  
  
