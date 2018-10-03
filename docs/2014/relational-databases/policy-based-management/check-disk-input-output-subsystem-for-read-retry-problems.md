---
title: Überprüfen Sie die Datenträger-Eingabe-a-Subsystems lesewiederholungsprobleme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9726b29ebdd47e447c14e402aa2c5fa345284216
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190650"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Überprüfen des Datenträger-E/A-Subsystems auf Lesewiederholungsprobleme
  Diese Regel überprüft das Ereignisprotokoll auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlermeldung 825. Mit dieser Meldung wird angegeben, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim ersten Versuch keine Daten vom Datenträger lesen konnte. Diese Meldung weist auf ein größeres Problem mit dem E/A-Subsystem des Datenträgers hin. Diese Meldung deutet aktuell nicht auf ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Problem hin. Durch das Datenträgerproblem werden jedoch möglicherweise Datenverluste oder Beschädigungen der Datenbank verursacht, wenn es nicht behoben wird.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Mit den folgenden Aktionen können Sie das zugrunde liegende Hardwareproblem möglicherweise ermitteln und lösen:  
  
-   Beachten Sie das Fehlerprotokoll und den jeweiligen Text in dieser Meldung, um Informationen zu den Ursachen für das Problem zu erfahren.  
  
-   Prüfen Sie das Datenträgersystem. Das Problem ist möglicherweise auf die Datenträger, Datenträgercontroller, Arraykarten oder Datenträgertreiber zurückzuführen.  
  
-   Die neuesten Hilfsprogramme zum Überprüfen des Status des Datenträgersystems erhalten Sie beim Hersteller des Datenträgers.  
  
-   Wenden Sie sich an den Hersteller des Datenträgers, um die neuesten Treiberupdates zu erhalten.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [MSSQLSERVER_825](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 [SQL Server I/O Basics, Chapter 2 (in Englisch)](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
