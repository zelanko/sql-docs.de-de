---
title: 'Lektion 3: Hinzufügen der Protokollierung mit SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 981c573c05b299a1022ac6615dae5de0036c3571
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51638157"
---
# <a name="lesson-3-add-logging-with-ssis"></a>Lektion 3: Hinzufügen der Protokollierung mit SSIS
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] umfasst Protokollierungsfunktionen für die Problembehandlung und das Überwachen der Paketausführung mithilfe einer Reihe von Task- und Containerereignissen. Die Protokollierungsfunktionen sind flexibel und können auf der Ebene des Pakets oder für einzelne Tasks und Container innerhalb des Pakets aktiviert werden. Sie können dann auswählen, welche Ereignisse protokolliert werden sollen, und mehrere Protokolle für ein einzelnes Paket erstellen.  
  
Die Protokollierung wird von einem Protokollanbieter zur Verfügung gestellt. Jeder Protokollanbieter ist in der Lage, Protokollierungsinformationen in verschiedenen Formaten und Zieltypen zu schreiben. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt die folgenden Protokollanbieter bereit:  
  
-   Textdatei  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows-Ereignisprotokoll:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-Datei:  
  
In dieser Lektion erstellen Sie eine Kopie des Pakets, das Sie in [Lesson 2: Adding Looping with SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)(Lektion 2: Hinzufügen von Schleifen mit SSIS) erstellt haben. Beim Arbeiten mit diesem neuen Paket fügen Sie dann die Protokollierung hinzu und konfigurieren sie, um bestimmte Ereignisse während der Paketausführung zu überwachen. Wenn Sie keine der vorherigen Lektionen abgeschlossen haben, können Sie auch das abgeschlossene Paket aus Lektion 2, das im Lernprogramm enthalten ist, kopieren.  
  
> [!IMPORTANT]  
> Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**finden Sie unter [Reporting Services Product Samples ](https://go.microsoft.com/fwlink/p/?LinkID=526910) (Reporting Services-Produktbeispiele) auf CodePlex  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren der Protokollierung](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Schritt 3: Testen des Lektion 3-Tutorialpakets](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Kopieren des Pakets aus Lektion 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
  
  
