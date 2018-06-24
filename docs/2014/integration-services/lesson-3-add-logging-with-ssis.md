---
title: 'Lektion 3: Hinzufügen der Protokollierung | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 24
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: be6cb6bb8edfa30ee33ed0431dbf33f11470cd0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059174"
---
# <a name="lesson-3-adding-logging"></a>Lektion 3: Hinzufügen der Protokollierung
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] umfasst Protokollierungsfunktionen für die Problembehandlung und das Überwachen der Paketausführung mithilfe einer Reihe von Task- und Containerereignissen. Die Protokollierungsfunktionen sind flexibel und können auf der Ebene des Pakets oder für einzelne Tasks und Container innerhalb des Pakets aktiviert werden. Sie können dann auswählen, welche Ereignisse protokolliert werden sollen, und mehrere Protokolle für ein einzelnes Paket erstellen.  
  
 Die Protokollierung wird von einem Protokollanbieter zur Verfügung gestellt. Jeder Protokollanbieter ist in der Lage, Protokollierungsinformationen in verschiedenen Formaten und Zieltypen zu schreiben. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt die folgenden Protokollanbieter bereit:  
  
-   Textdatei  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows-Ereignisprotokoll:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-Datei:  
  
 In dieser Lektion erstellen Sie eine Kopie des Pakets, das Sie erstellt haben [Lektion 2: Hinzufügen von Schleifen](lesson-2-adding-looping-with-ssis.md). Beim Arbeiten mit diesem neuen Paket fügen Sie dann die Protokollierung hinzu und konfigurieren sie, um bestimmte Ereignisse während der Paketausführung zu überwachen. Wenn Sie keine der vorherigen Lektionen abgeschlossen haben, können Sie auch das abgeschlossene Paket aus Lektion 2, das im Lernprogramm enthalten ist, kopieren.  
  
> [!IMPORTANT]  
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**, [Reporting Services Product Samples auf CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=52691).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren der Protokollierung](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Schritt 3: Testen des Lektion 3-Tutorialpakets](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Kopieren des Pakets aus Lektion 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
  