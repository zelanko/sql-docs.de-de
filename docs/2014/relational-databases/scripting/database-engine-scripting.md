---
title: Datenbank-Engine-Skripterstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15ead723c73da69d9dd8e6f41b1bf5533eb3c313
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284796"
---
# <a name="database-engine-scripting"></a>Datenbank-Engine-Skripterstellung
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] unterstützt die [!INCLUDE[msCoName](../../includes/msconame-md.md)] -PowerShell-Skriptumgebung zum Verwalten der Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] und der Objekte in den Instanzen. Sie können zudem [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)] und XQuery in Umgebungen erstellen und ausführen, die mit Skriptumgebungen vergleichbar sind.  
  
## <a name="sql-server-powershell"></a>SQL Server-PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält zwei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Snap-Ins, die Folgendes implementieren:  
  
-   Einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Anbieter, der die Hierarchien von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltungsobjektmodellen als PowerShell-Pfade verfügbar macht, die den Dateisystempfaden ähneln. Sie können mithilfe der Klassen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltungsobjektmodells die Objekte verwalten, die an jedem Knoten des Pfads dargestellt werden.  
  
-   Einen Satz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cmdlets, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Befehle implementieren. Eines der Cmdlets ist **Invoke-Sqlcmd**. Wird verwendet, um die Ausführung [!INCLUDE[ssDE](../../includes/ssde-md.md)] -abfrageskripts für die Ausführung mit der `sqlcmd` Hilfsprogramm.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Funktionen zum Ausführen von PowerShell bereit:  
  
-   Das **sqlps** -PowerShell-Modul, das in eine PowerShell-Sitzung importiert werden kann; das Modul lädt dann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Snap-Ins. Sie können PowerShell-Befehle interaktiv ad hoc ausführen. Sie können Skriptdateien mit einem Befehl wie .\MyFolder\MyScript.ps1 ausführen.  
  
-   PowerShell-Skriptdateien können als Eingabe in die PowerShell-Auftragsschritte des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verwendet werden, mit denen die Skripts entweder in Zeitabständen nach einem Zeitplan oder als Reaktion auf Systemereignisse ausgeführt werden.  
  
-   Das **sqlps** -Hilfsprogramm, das PowerShell startet und das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Modul importiert. Sie können dann alle vom Modul unterstützten Aktionen ausführen. Sie können das **sqlps** -Hilfsprogramm an einer Eingabeaufforderung starten oder indem Sie mit der rechten Maustaste auf die Knoten in der Struktur des Objekt-Explorers von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio klicken und **PowerShell starten**auswählen.  
  
## <a name="database-engine-queries"></a>Datenbank-Engine-Abfragen  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrageskripts enthalten drei Typen von Elementen:  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] -Sprachanweisungen  
  
-   XQuery-Sprachanweisungen  
  
-   Befehle und Variablen aus der `sqlcmd` Hilfsprogramm.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt drei Umgebungen zum Erstellen und Ausführen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfragen:  
  
-   Sie können [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfragen im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]interaktiv ausführen und debuggen. Sie können eine Reihe von Anweisungen in einer Sitzung codieren und debuggen und anschließend alle Anweisungen in einer Skriptdatei speichern.  
  
-   Die `sqlcmd` eingabeaufforderungs-Hilfsprogramm können Sie die interaktive Ausführung [!INCLUDE[ssDE](../../includes/ssde-md.md)] Abfragen und auch vorhandene [!INCLUDE[ssDE](../../includes/ssde-md.md)] Skriptdateien Abfragen.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrageskriptdateien werden i. d. R. mit dem [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor in [!INCLUDE[ssDE](../../includes/ssde-md.md)] interaktiv codiert. Die Datei kann später in einer dieser Umgebungen geöffnet werden:  
  
-   Verwenden Sie das [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei**/**Öffnen** , um die Datei in einem neuen [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editorfenster zu öffnen.  
  
-   Verwenden der **-i *** Input_file* Parameter, um die Datei mit den `sqlcmd` Hilfsprogramm.  
  
-   Verwenden Sie den **-QueryFromFile** -Parameter, um die Datei mit dem **Invoke-Sqlcmd** -Cmdlet in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Skripts auszuführen.  
  
-   Führen Sie die Skripts mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Auftragsschritten des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Agents entweder in Zeitabständen nach einem Zeitplan oder als Reaktion auf Systemereignisse aus.  
  
 Außerdem können Sie mithilfe des Assistenten zum Generieren von Skripts in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts generieren. Sie können mit der rechten Maustaste im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Objekt-Explorer auf Objekte klicken und anschließend das Menüelement **Skript generieren** auswählen. Mit**Skript generieren** wird der Assistent gestartet, der Sie durch den Vorgang der Skripterstellung führt.  
  
## <a name="database-engine-scripting-tasks"></a>Tasks der Datenbank-Engine-Skripterstellung  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie die Code- und Text-Editoren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] zum interaktiven Entwickeln, Debuggen und Ausführen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts verwendet werden.|[Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Beschreibt, wie die `sqlcmd` -Hilfsprogramm ausführen [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts über die Eingabeaufforderung, einschließlich der Möglichkeit zum interaktiven Entwickeln von Skripts.|[Themen zur Vorgehensweise für sqlcmd](../../database-engine/sqlcmd-how-to-topics.md)|  
|Beschreibt, wie die SQL Server-Komponenten in eine Windows PowerShell 2.0-Umgebung integriert und anschließend PowerShell-Skripts für die Verwaltung von SQL Server-Instanzen und -Objekten erstellt werden.|[SQL Server-PowerShell](../../powershell/sql-server-powershell.md)|  
|Beschreibt, wie mit dem **Assistenten zum Generieren und Veröffentlichen von Skripts** [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts erstellt werden, mit denen Objekte aus einer Datenbank erneut erstellt werden.|[Erstellen von Skripts &#40;SQL Server Management Studio&#41;](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [Lernprogramm: Schreiben von Transact-SQL-Anweisungen](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
