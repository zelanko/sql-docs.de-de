---
title: Überprüfen Sie die Datenträger-Eingabe-a-Subsystems lesewiederholungsprobleme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 68c8cdb91f4c850618d19b26f0125205bfd045b9
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59242318"
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
  
 [SQL Server I/O Basics, Chapter 2 (in Englisch)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))  
  
  
