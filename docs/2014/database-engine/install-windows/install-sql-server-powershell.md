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
ms.openlocfilehash: dd603a59a1ddb2ede3d3c779d31f13424342edc2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932551"
---
# <a name="install-sql-server-powershell"></a>Installieren von SQL Server PowerShell
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup wird beendet, wenn es erkennt, dass Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen ausgewählt haben, die PowerShell-Komponenten einschließen, Windows PowerShell 2.0 jedoch nicht installiert ist. Sie müssen PowerShell mit Windows Management Framework installieren und Setup dann erneut ausführen.  
  
## <a name="installing-ssnoversion-powershell-support"></a>Installieren der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Unterstützung  
 Die Software, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Unterstützung für Windows PowerShell bietet, installieren Sie mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen auswählen, die PowerShell-Unterstützung erfordern, überprüft Setup, ob Windows PowerShell 2.0 installiert ist. Wenn PowerShell 2.0 vorhanden ist, installiert Setup die folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Komponenten:  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Snap-Ins. Die Snap-Ins sind dll-Dateien, die zwei Arten der Windows PowerShell-Unterstützung für implementieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    -   Ein Satz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cmdlets. Cmdlets sind Befehle, die eine bestimmte Aktion implementieren. Beispielsweise führt **Invoke-Sqlcmd** ein [!INCLUDE[tsql](../../includes/tsql-md.md)] - oder XQuery-Skript aus, das auch vom **sqlcmd** -Hilfsprogramm ausgeführt werden kann. **Invoke-PolicyEvaluation** meldet, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte den richtlinienbasierten Verwaltungsrichtlinien entsprechen.  
  
    -   Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anbieter. Mit dem Anbieter können Sie in der Hierarchie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte mithilfe eines Pfads navigieren, der einem Dateisystempfad ähnelt. Jedes Objekt ist einer Klasse der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object-Modelle zugeordnet. Sie können die Methoden und die Eigenschaften der Klasse zur Arbeit mit den Objekten verwenden. Wenn Sie z. B. cd zu einem Datenbankobjekt in einem Pfad ausführen, können Sie die Methoden und Eigenschaften der Microsoft.SqlServer.Management.SMO.Database-Klasse verwenden, um die Datenbank zu verwalten.  
  
-   Das **sqlps** -Modul, das in Windows PowerShell 2,0-Sitzungen importiert wird, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Snap-Ins zu laden.  
  
-   Das veraltete **sqlps** -Hilfsprogramm, das eine Windows PowerShell 2,0-Sitzung startet und das **sqlps** -Modul importiert.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unterstützt das Starten von Windows PowerShell-Sitzungen aus der Struktur des Objekt-Explorers. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent unterstützt Windows PowerShell-Auftragsschritte.  
  
 Wenn Windows PowerShell 2,0 nicht installiert ist oder deinstalliert wurde, müssen Sie Sie installieren, indem Sie die Anweisungen auf der Seite [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) befolgen.  
  
 Wenn Windows PowerShell nach der Beendigung des Setups deinstalliert wird, sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen für Windows PowerShell nicht funktionsfähig. Windows PowerShell kann von Windows-Benutzern deinstalliert werden. Die Deinstallation von Windows PowerShell ist unter Umständen bei einigen Upgrades von Windows-Betriebssystemen erforderlich. Um die PowerShell-Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu verwenden, müssen Sie PowerShell 2.0 mit Windows Management Framework erneut installieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-PowerShell](../../powershell/sql-server-powershell.md)  
  
  
