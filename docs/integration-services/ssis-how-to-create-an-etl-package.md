---
title: 'SSIS: Erstellen eines einfachen ETL-Pakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: quickstart
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9a36d403867699a02adfec0d04c9db4efa803514
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71281882"
---
# <a name="ssis-how-to-create-an-etl-package"></a>SSIS-Tutorials: Erstellen eines einfachen ETL-Pakets

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In diesem Tutorial lernen Sie, wie Sie mit dem [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer ein einfaches [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Paket erstellen. Das von Ihnen erstellte Paket übernimmt Daten aus einer Flatfile, formatiert die Daten und fügt die neu formatierten Daten in eine Faktentabelle ein. In den folgenden Lektionen wird das Paket erweitert, um Schleifen, Paketkonfigurationen, Protokollierung und Fehlerfluss zu veranschaulichen.  
  
Beim Installieren der im Tutorial verwendeten Beispieldaten werden auch die abgeschlossenen Versionen der Pakete, die Sie in der jeweiligen Lektion des Tutorials erstellen werden, installiert. Mithilfe der abgeschlossenen Pakete können Sie Lektionen überspringen und nach Belieben mit einer späteren Lektion in das Lernprogramm einsteigen. Wenn dieses Tutorial Ihre erste Erfahrung mit Paketen oder mit der neuen Entwicklungsumgebung ist, empfehlen wir Ihnen, mit Lektion 1 zu beginnen.  

## <a name="what-is-sql-server-integration-services-ssis"></a>Was ist SQL Server Integration Services (SSIS)?

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) ist eine Plattform zum Erstellen von leistungsstarken Datenintegrationslösungen, z. B. für das Extrahieren, Transformieren und Laden (ETL) von Paketen für das Data Warehousing. SSIS enthält grafische Tools und Assistenten zum Erstellen und Debuggen von Paketen; Tasks zum Ausführen von Workflowfunktionen wie FTP-Vorgänge, Ausführen von SQL-Anweisungen und Senden von E-Mails; Datenquellen und Ziele zum Extrahieren und Laden von Daten; Transformationen zum Bereinigen, Aggregieren, Zusammenführen und Kopieren von Daten; eine Verwaltungsdatenbank (`SSISDB`) zum Verwalten der Paketausführung und -speicherung; und Anwendungsprogrammierschnittstellen (APIs) zum Programmieren des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Objektmodells.  

## <a name="what-you-learn"></a>Ihre Lernziele  
Die beste Möglichkeit, die neuen Tools, Steuerfunktionen und Features von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] kennenzulernen, ist, sie einzusetzen. Dieses Tutorial leitet Sie Schritt für Schritt durch den [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer, um ein einfaches ETL-Paket einschließlich Schleifen, Konfigurationen, Fehlerflusslogik und Protokollierung zu erstellen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
Dieses Tutorial wendet sich an Benutzer, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die neuen Features von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] verfügen.  

Folgende Komponenten müssen installiert sein, damit Sie dieses Tutorial ausführen können:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]: Weitere Informationen zu SQL Server und SSIS finden Sie unter [Installieren von Integration Services](install-windows/install-integration-services.md).

-   Die **AdventureWorksDW2012**-Beispieldatenbank. Laden Sie `AdventureWorksDW2012.bak` von der [AdventureWorks-Beispieldatenbank](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) herunter, und stellen Sie die Sicherung wieder her, um die Datenbank **AdventureWorksDW2012** herunterzuladen.  

-   Die Dateien der **Beispieldaten**. Die Beispieldaten sind in den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Lektionspaketen enthalten. Informationen zum Download der Beispieldaten sowie der Lektionspakete als ZIP-Datei finden Sie unter [Tutorial für SQL Server Integration Services: Erstellen eines einfachen ETL-Pakets](https://www.microsoft.com/download/details.aspx?id=56827).

    - Die meisten Dateien in der ZIP-Datei sind schreibgeschützt, um unbeabsichtigte Änderungen zu verhindern. Um die Ausgabe in eine Datei zu schreiben oder zu ändern, müssen Sie unter Umständen das Nur-Lese-Attribut in den Dateieigenschaften deaktivieren.
    - Die Beispielpakete gehen davon aus, dass sich die Datendateien im Ordner `C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Creating a Simple ETL Package` befinden. Wenn Sie den Download in einem anderen Speicherort entzippen, müssen Sie den Dateipfad möglicherweise an mehreren Stellen in den Beispielpaketen aktualisieren.

## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
[Lesson 1: Create a Project and Basic Package with SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)  
In dieser Lektion erstellen Sie ein einfaches ETL-Paket, das Daten aus einer einzelnen Flatfile extrahiert, die Daten mithilfe von Transformationen zum Suchen transformiert und die Ergebnisse schließlich in ein Faktentabellenziel lädt.  
  
[Lesson 2: Adding Looping with SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
In dieser Lektion erweitern Sie das Paket, das Sie in Lektion 1 erstellt haben, um die Vorteile der neuen Schleifenfunktionen zum Extrahieren von mehreren Flatfiles in einen einzigen Datenflussprozess zu nutzen.  
  
[Lektion 3: Hinzufügen der Protokollierung mit SSIS](../integration-services/lesson-3-add-logging-with-ssis.md)  
In dieser Lektion erweitern Sie das von Ihnen in Lektion 2 erstellte Paket, um die Vorteile der neuen Protokollierungsfunktionen zu nutzen.  
  
[Lektion 4: Hinzufügen der Fehlerflussumleitung mit SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
In dieser Lektion erweitern Sie das von Ihnen in Lektion 3 erstellte Paket, um die Vorteile der neuen Fehlerausgabekonfigurationen zu nutzen.  
  
[Lesson 5: Add SSIS Package Configurations for the Package Deployment Model](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
In dieser Lektion erweitern Sie das von Ihnen in Lektion 4 erstellte Paket, um die Vorteile der neuen Paketkonfigurationsoptionen zu nutzen.  
  
[Lesson 6: Using Parameters with the Project Deployment Model in SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
In dieser Lektion erweitern Sie das Paket, das Sie in Lektion 5 erstellt haben, um von der Verwendung der neuen Parameter für das Projektbereitstellungsmodell zu profitieren.  
  
  
  
