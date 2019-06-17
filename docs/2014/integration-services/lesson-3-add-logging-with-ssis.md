---
title: 'Lektion 3: Hinzufügen der Protokollierung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e716b808d5d9ada8aeaf50d92006cc6453c6e47d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67046765"
---
# <a name="lesson-3-adding-logging"></a>Lektion 3: Hinzufügen der Protokollierung
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] umfasst Protokollierungsfunktionen für die Problembehandlung und das Überwachen der Paketausführung mithilfe einer Reihe von Task- und Containerereignissen. Die Protokollierungsfunktionen sind flexibel und können auf der Ebene des Pakets oder für einzelne Tasks und Container innerhalb des Pakets aktiviert werden. Sie können dann auswählen, welche Ereignisse protokolliert werden sollen, und mehrere Protokolle für ein einzelnes Paket erstellen.  
  
 Die Protokollierung wird von einem Protokollanbieter zur Verfügung gestellt. Jeder Protokollanbieter ist in der Lage, Protokollierungsinformationen in verschiedenen Formaten und Zieltypen zu schreiben. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt die folgenden Protokollanbieter bereit:  
  
-   Textdatei  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows-Ereignisprotokoll:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-Datei:  
  
 In dieser Lektion erstellen Sie eine Kopie des Pakets, das Sie in erstellt [Lektion 2: Hinzufügen von Schleifen](lesson-2-adding-looping-with-ssis.md). Beim Arbeiten mit diesem neuen Paket fügen Sie dann die Protokollierung hinzu und konfigurieren sie, um bestimmte Ereignisse während der Paketausführung zu überwachen. Wenn Sie keine der vorherigen Lektionen abgeschlossen haben, können Sie auch das abgeschlossene Paket aus Lektion 2, das im Lernprogramm enthalten ist, kopieren.  
  
> [!IMPORTANT]  
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zur Installation und Bereitstellung **AdventureWorksDW2012**, [Reporting Services Product Samples auf GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren der Protokollierung](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Schritt 3: Testen des Lektion 3-Tutorialpakets](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Kopieren des Pakets aus Lektion 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
