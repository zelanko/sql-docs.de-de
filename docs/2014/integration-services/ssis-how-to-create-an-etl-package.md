---
title: 'SSIS-Tutorial: Erstellen eines einfachen ETL-Pakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e25c90b3baa4e718f40dc3a3f84b6dc221d54c33
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62878282"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a>SSIS-Tutorial: Erstellen eines einfachen ETL-Pakets
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) ist eine Plattform zum Erstellen leistungsfähiger datenintegrationslösungen, z. B. extrahieren, Transformieren und laden (ETL)-Paketen für Data Warehouses. SSIS enthält grafische Tools und Assistenten zum Erstellen und Debuggen von Paketen; Tasks zum Ausführen von Workflowfunktionen wie z. B. FTP-Vorgänge, Ausführen von SQL-Anweisungen und Senden von E-Mails; Datenquellen und Ziele zum Extrahieren und Laden von Daten; Transformationen zum Bereinigen, Aggregieren, Zusammenführen und Kopieren von Daten; einen Verwaltungsdienst, den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst zum Verwalten der Paketausführung und -speicherung; und Anwendungsprogrammierschnittstellen (APIs, Application Programming Interfaces) zum Programmieren des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objektmodells.  
  
 In diesem Tutorial lernen Sie die Verwendung des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers zum Erstellen eines einfachen Pakets in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Das von Ihnen erstellte Paket übernimmt Daten aus einer Flatfile, formatiert die Daten und fügt die neu formatierten Daten in eine Faktentabelle ein. In den folgenden Lektionen wird das Paket erweitert, um Schleifen, Paketkonfigurationen, Protokollierung und Fehlerfluss zu demonstrieren.  
  
 Beim Installieren der im Lernprogramm verwendeten Beispieldaten werden auch die abgeschlossenen Versionen der Pakete, die Sie in der jeweiligen Lektion des Lernprogramms erstellen werden, installiert. Mithilfe der abgeschlossenen Pakete können Sie Lektionen überspringen und nach Belieben mit einer späteren Lektion in das Lernprogramm einsteigen. Wenn dies Ihre erste Erfahrung mit Paketen oder mit der neuen Entwicklungsumgebung ist, empfehlen wir Ihnen, mit Lektion 1 zu beginnen.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 Die beste Möglichkeit, den Umgang mit den neuen Tools, Steuerelementen und Funktionen von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] zu üben, besteht in ihrer Verwendung. Dieses Lernprogramm leitet Sie Schritt für Schritt durch den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer, um ein einfaches ETL-Paket einschließlich Schleifen, Konfigurationen, Fehlerflusslogik und Protokollierung zu erstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Dieses Tutorial wendet sich an Benutzer, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]verfügen.  
  
 Ihr System muss die folgenden installierten Komponenten aufweisen, damit dieses Lernprogramm verwendet werden kann:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit der **AdventureWorksDW2012** -Datenbank. Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. Wie die **AdventureWorksDW2012** -Datenbank heruntergeladen wird, informieren Sie sich unter [Adventure Works für SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026).  
  
    > [!IMPORTANT]  
    >  Wenn Sie die Datenbank (\*.mdf-Datei) anfügen, sucht [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] standardmäßig nach einer LDF-Datei. Sie müssen die LDF-Datei manuell entfernen, bevor Sie im Dialogfeld **Datenbanken anfügen** auf OK klicken.  
    >   
    >  Weitere Informationen zum Anfügen von Datenbanken finden Sie unter [Anfügen einer Datenbank](../relational-databases/databases/attach-a-database.md).  
  
-   Beispieldaten. Die Beispieldaten sind in den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Lektionspaketen enthalten. Um die Beispieldaten und die Lektionspakete herunterzuladen, gehen Sie wie folgt vor.  
  
    1.  Klicken Sie [hier](https://go.microsoft.com/fwlink/?LinkId=275027), um zur Seite Integration Services Product Samples zu gelangen  
  
    2.  Klicken Sie auf die Registerkarte **DOWNLOADS** .  
  
    3.  Klicken Sie auf die Datei SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
 [Lektion 1: Erstellen des Projekts und Basispakets](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 In dieser Lektion erstellen Sie ein einfaches ETL-Paket, das Daten aus einer einzelnen Flatfile extrahiert, die Daten mithilfe von Transformationen zum Suchen transformiert und die Ergebnisse schließlich in ein Faktentabellenziel lädt.  
  
 [Lektion 2: Hinzufügen von Schleifen](lesson-2-adding-looping-with-ssis.md)  
 In dieser Lektion erweitern Sie das Paket, das Sie in Lektion 1 erstellt haben, um die Vorteile der neuen Schleifenfunktionen zum Extrahieren von mehreren Flatfiles in einen einzigen Datenflussprozess zu nutzen.  
  
 [Lektion 3: Hinzufügen der Protokollierung](lesson-3-add-logging-with-ssis.md)  
 In dieser Lektion erweitern Sie das von Ihnen in Lektion 2 erstellte Paket, um die Vorteile der neuen Protokollierungsfunktionen zu nutzen.  
  
 [Lektion 4: Hinzufügen von Fehlerflussumleitungen](lesson-4-add-error-flow-redirection-with-ssis.md)  
 In dieser Lektion erweitern Sie das von Ihnen in Lektion 3 erstellte Paket, um die Vorteile der neuen Fehlerausgabekonfigurationen zu nutzen.  
  
 [Lesson 5: Hinzufügen von Paketkonfigurationen für das Paketbereitstellungsmodell](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 In dieser Lektion erweitern Sie das von Ihnen in Lektion 4 erstellte Paket, um die Vorteile der neuen Paketkonfigurationsoptionen zu nutzen.  
  
 [Lektion 6: Verwenden von Parametern mit dem Projektbereitstellungsmodell](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 In dieser Lektion erweitern Sie das Paket, das Sie in Lektion 5 erstellt haben, um von der Verwendung der neuen Parameter für das Projektbereitstellungsmodell zu profitieren.  
  
  
