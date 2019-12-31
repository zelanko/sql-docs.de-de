---
title: Datenbank-Engine-Skripterstellung
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b092c85ea678ce05c3b9c8bbff4f78d47589bdb
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244962"
---
# <a name="database-engine-scripting"></a>Datenbank-Engine-Skripterstellung
  
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] unterstützt die [!INCLUDE[msCoName](../../includes/msconame-md.md)] -PowerShell-Skriptumgebung zum Verwalten der Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] und der Objekte in den Instanzen. Sie können zudem [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfragen mit [!INCLUDE[tsql](../../includes/tsql-md.md)] und XQuery in Umgebungen erstellen und ausführen, die mit Skriptumgebungen vergleichbar sind.  
  
## <a name="sql-server-powershell"></a>SQL Server PowerShell  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält zwei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Snap-Ins, die Folgendes implementieren:  
  
-   Einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Anbieter, der die Hierarchien von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltungsobjektmodellen als PowerShell-Pfade verfügbar macht, die den Dateisystempfaden ähneln. Sie können mithilfe der Klassen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltungsobjektmodells die Objekte verwalten, die an jedem Knoten des Pfads dargestellt werden.  
  
-   Einen Satz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Cmdlets, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Befehle implementieren. Eines der Cmdlets ist **Invoke-Sqlcmd**. Dies wird zum Ausführen [!INCLUDE[ssDE](../../includes/ssde-md.md)] von Abfrage Skripts verwendet, die mit `sqlcmd` dem Hilfsprogramm ausgeführt werden.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Funktionen zum Ausführen von PowerShell bereit:  
  
-   Das **sqlps** -PowerShell-Modul, das in eine PowerShell-Sitzung importiert werden kann, lädt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das-Modul. Sie können Ad-hoc-PowerShell-Befehle interaktiv ausführen. Sie können Skriptdateien mit einem Befehl wie .\MyFolder\MyScript.ps1 ausführen.  
  
-   PowerShell-Skriptdateien können als Eingabe in die PowerShell-Auftragsschritte des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verwendet werden, mit denen die Skripts entweder in Zeitabständen nach einem Zeitplan oder als Reaktion auf Systemereignisse ausgeführt werden.  
  
-   Das **sqlps** -Hilfsprogramm, das PowerShell startet und das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Modul importiert. Sie können dann alle vom Modul unterstützten Aktionen ausführen. Sie können das **sqlps** -Hilfsprogramm an einer Eingabeaufforderung starten oder indem Sie mit der rechten Maustaste auf die Knoten in der Struktur des Objekt-Explorers von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio klicken und **PowerShell starten**auswählen.  
  
## <a name="database-engine-queries"></a>Datenbank-Engine-Abfragen  
 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrageskripts enthalten drei Typen von Elementen:  
  
-   
  [!INCLUDE[tsql](../../includes/tsql-md.md)] -Sprachanweisungen  
  
-   XQuery-Sprachanweisungen  
  
-   Befehle und Variablen aus dem `sqlcmd` -Hilfsprogramm.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt drei Umgebungen zum Erstellen und Ausführen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfragen:  
  
-   Sie können [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfragen im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]interaktiv ausführen und debuggen. Sie können eine Reihe von Anweisungen in einer Sitzung codieren und debuggen und anschließend alle Anweisungen in einer Skriptdatei speichern.  
  
-   Mit `sqlcmd` dem Eingabeaufforderungs- [!INCLUDE[ssDE](../../includes/ssde-md.md)] Hilfsprogramm können Sie Abfragen interaktiv [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausführen und vorhandene Abfrage Skriptdateien ausführen.  
  
 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrageskriptdateien werden i. d. R. mit dem [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Abfrage-Editor in [!INCLUDE[ssDE](../../includes/ssde-md.md)] interaktiv codiert. Die Datei kann später in einer dieser Umgebungen geöffnet werden:  
  
-   Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] das Menü **Datei**/**Öffnen** , um die Datei in einem [!INCLUDE[ssDE](../../includes/ssde-md.md)] neuen Abfrage-Editor-Fenster zu öffnen.  
  
-   Verwenden Sie den Parameter **-i**_input_file_ , um die Datei mit `sqlcmd` dem Hilfsprogramm auszuführen.  
  
-   Verwenden Sie den **-QueryFromFile** -Parameter, um die Datei mit dem **Invoke-Sqlcmd** -Cmdlet in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Skripts auszuführen.  
  
-   Führen Sie die Skripts mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Auftragsschritten des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Agents entweder in Zeitabständen nach einem Zeitplan oder als Reaktion auf Systemereignisse aus.  
  
 Außerdem können Sie mithilfe des Assistenten zum Generieren von Skripts in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts generieren. Sie können mit der rechten Maustaste im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Objekt-Explorer auf Objekte klicken und anschließend das Menüelement **Skript generieren** auswählen. **Skript generieren** : Hiermit wird der Assistent gestartet, der Sie durch den Prozess der Skripterstellung führt.  
  
## <a name="database-engine-scripting-tasks"></a>Tasks der Datenbank-Engine-Skripterstellung  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie die Code- und Text-Editoren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] zum interaktiven Entwickeln, Debuggen und Ausführen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts verwendet werden.|[Abfrage-und Text-Editoren &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Beschreibt, wie das Hilfsprogramm `sqlcmd` zum Ausführen von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skripts über die Eingabeaufforderung verwendet wird, einschließlich der Möglichkeit zum interaktiven Entwickeln von Skripts.|[Gewusst-wie-Themen zu sqlcmd](../../database-engine/sqlcmd-how-to-topics.md)|  
|Beschreibt, wie die SQL Server-Komponenten in eine Windows PowerShell 2.0-Umgebung integriert und anschließend PowerShell-Skripts für die Verwaltung von SQL Server-Instanzen und -Objekten erstellt werden.|[SQL Server PowerShell](../../powershell/sql-server-powershell.md)|  
|Beschreibt, wie mit dem **Assistenten zum Generieren und Veröffentlichen von Skripts**[!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts erstellt werden, mit denen Objekte aus einer Datenbank erneut erstellt werden.|[Skripts &#40;SQL Server Management Studio generieren&#41;](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sqlcmd-Hilfsprogramm](../../tools/sqlcmd-utility.md)   
 [Tutorial: Schreiben von Transact-SQL-Anweisungen](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
