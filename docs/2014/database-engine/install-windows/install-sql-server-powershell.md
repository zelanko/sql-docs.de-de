---
title: Installieren von SQL Server PowerShell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a90a30a0ae7fe09d49b1d42b577b13370c48c0de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62775440"
---
# <a name="install-sql-server-powershell"></a>Installieren von SQL Server PowerShell
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup wird beendet, wenn es erkennt, dass Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen ausgewählt haben, die PowerShell-Komponenten einschließen, Windows PowerShell 2.0 jedoch nicht installiert ist. Sie müssen PowerShell mit Windows Management Framework installieren und Setup dann erneut ausführen.  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>Installieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Unterstützung  
 Die Software, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Unterstützung für Windows PowerShell bietet, installieren Sie mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen auswählen, die PowerShell-Unterstützung erfordern, überprüft Setup, ob Windows PowerShell 2.0 installiert ist. Wenn PowerShell 2.0 vorhanden ist, installiert Setup die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Komponenten:  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Snap-Ins. Die Snap-Ins sind DLL-Dateien, die zwei Arten der Windows PowerShell-Unterstützung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]implementieren:  
  
    -   Ein Satz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cmdlets. Cmdlets sind Befehle, die eine bestimmte Aktion implementieren. Beispielsweise führt **Invoke-Sqlcmd** ein [!INCLUDE[tsql](../../includes/tsql-md.md)] - oder XQuery-Skript aus, das auch vom **sqlcmd** -Hilfsprogramm ausgeführt werden kann. **Invoke-PolicyEvaluation** meldet, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte den richtlinienbasierten Verwaltungsrichtlinien entsprechen.  
  
    -   Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anbieter. Mit dem Anbieter können Sie in der Hierarchie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte mithilfe eines Pfads navigieren, der einem Dateisystempfad ähnelt. Jedes Objekt ist einer Klasse der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object-Modelle zugeordnet. Sie können die Methoden und die Eigenschaften der Klasse zur Arbeit mit den Objekten verwenden. Wenn Sie z. B. cd zu einem Datenbankobjekt in einem Pfad ausführen, können Sie die Methoden und Eigenschaften der Microsoft.SqlServer.Management.SMO.Database-Klasse verwenden, um die Datenbank zu verwalten.  
  
-   Die **Sqlps** -Modul, das in Windows PowerShell 2.0-Sitzungen laden importiert wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Snap-ins.  
  
-   Die veraltete **Sqlps** -Dienstprogramm, das eine Windows PowerShell 2.0-Sitzung startet und importiert die **Sqlps** Modul.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unterstützt das Starten von Windows PowerShell-Sitzungen aus der Struktur des Objekt-Explorers. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent unterstützt Windows PowerShell-Auftragsschritte.  
  
 Wenn Windows PowerShell 2.0 nicht installiert oder deinstalliert wurde, müssen Sie es installieren, mithilfe der Anweisungen auf der [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) Seite.  
  
 Wenn Windows PowerShell nach der Beendigung des Setups deinstalliert wird, sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen für Windows PowerShell nicht funktionsfähig. Windows PowerShell kann von Windows-Benutzern deinstalliert werden. Die Deinstallation von Windows PowerShell ist unter Umständen bei einigen Upgrades von Windows-Betriebssystemen erforderlich. Um die PowerShell-Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu verwenden, müssen Sie PowerShell 2.0 mit Windows Management Framework erneut installieren.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-PowerShell](../../powershell/sql-server-powershell.md)  
  
  
