---
title: Vollständigen Pfad zum Registrieren von DLL-Namen für erweiterte gespeicherte Prozeduren verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ec4ef3fc2e0f2c4834ffa7479a00562ae15d07f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058824"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>Verwenden Sie beim Registrieren von DLL-Namen für erweiterte gespeicherte Prozeduren den vollständigen Pfad
  Erweiterte gespeicherte Prozeduren, die zuvor ohne den vollständigen Pfad für den DLL-Namen registriert wurden, sind in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] möglicherweise nicht funktionsfähig.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Erweiterte gespeicherte Prozeduren, die vorher ohne den vollständigen Pfad für den DLL-Namen registriert wurden, sind möglicherweise nach einem Upgrade nicht funktionsfähig. Dies liegt daran, dass dem neuen Pfad während des Upgradevorgangs nicht das alte BINN-Verzeichnis hinzugefügt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die erweiterten gespeicherten Prozeduren möglicherweise nicht lokalisieren.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Führen Sie vor dem Upgrade die folgenden Schritte für jede erweiterte gespeicherte Prozedur aus, die nicht mit einem vollständigen Pfadnamen registriert wurde:  
  
1.  Führen Sie zum Entfernen der erweiterten gespeicherten Prozedur sp_dropextendedproc aus.  
  
2.  Führen Sie zum Registrieren der erweiterten gespeicherten Prozedur mit dem vollständigen Pfadnamen sp_addextendedproc aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
