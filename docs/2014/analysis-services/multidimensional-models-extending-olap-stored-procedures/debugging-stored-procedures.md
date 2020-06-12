---
title: Debugging gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545392"
---
# <a name="debugging-stored-procedures"></a>Debuggen gespeicherter Prozeduren
  Gespeicherte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Prozeduren sind eigentlich CLR- oder COM-Bibliotheken (normalerweise DLLs), die in C# (oder in einer anderen CLR- oder COM-Sprache) geschrieben sind. Das Debuggen einer gespeicherten Prozedur entspricht also im Wesentlichen dem Debuggen jeder anderen Anwendung in der Debugumgebung von Visual Studio. Sie debuggen gespeicherte Prozeduren in der Visual Studio-Entwicklungsumgebung mithilfe integrierter Debugfunktionen. Mit diesen können Sie an Prozedurspeicherorten stoppen, Speicher inspizieren und Werte registrieren, Variablen ändern, den Nachrichtenverkehr beobachten und einen genauen Blick auf das Funktionieren des Codes werfen.  
  
### <a name="to-debug-a-stored-procedure"></a>So debuggen Sie eine gespeicherte Prozedur  
  
1.  Öffnen Sie das zum Erstellen der DLL verwendete Projekt in Visual Studio.  
  
2.  Erstellen Sie Breakpoints in der Methode oder Funktion entsprechend der zu debuggenden Prozedur.  
  
3.  Verwenden Sie Visual Studio, um einen Debugbuild einer DLL für gespeicherte Prozeduren zu erstellen.  
  
4.  Stellen Sie die DLL auf dem Server bereit. Weitere Informationen zum Bereitstellen der dll auf dem Server finden Sie unter [Erstellen von gespeicherten Prozeduren](creating-stored-procedures.md).  
  
5.  Sie benötigen eine Anwendung, um die zu testende gespeicherte Prozedur aufzurufen. Wenn Sie keine solche zur Verfügung haben, können Sie mit dem MDX-Abfrage-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine MDX-Abfrage erstellen, um die zu testende gespeicherte Prozedur aufzurufen.  
  
6.  Hängen Sie in Visual Studio den Debugger an den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Prozess (Msmdsrv.exe) an.  
  
    1.  Wählen Sie im Menü **Debuggen** die Option **attatch toprocess**.  
  
    2.  Wählen Sie im Dialogfeld " **attatch toprocess** " die Option **Prozesse aller Benutzer anzeigen aus**.  
  
    3.  Klicken Sie in der Liste **Verfügbare Prozesse** in der Spalte **verarbeiten** auf **Msmdsrv.exe**. Werden auf dem Server mehrere Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ausgeführt, müssen Sie den Prozess mithilfe der ID der Instanz, die Sie verwenden wollen, identifizieren.  
  
    4.  Stellen Sie sicher, dass im Textfeld **Anfügen an** der entsprechende Programmtyp ausgewählt ist. Klicken Sie für eine CLR-DLL auf **auswählen**, klicken Sie dann auf **Diese Codetypen debuggen**, klicken Sie auf **verwaltet**und dann auf **OK**. Klicken Sie für eine com-dll auf **auswählen**, klicken Sie dann auf **Diese Codetypen debuggen** **, klicken Sie auf System**eigen und dann auf **OK**.  
  
    5.  Klicken Sie auf **Anfügen**aus.  
  
7.  Rufen Sie in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] das Programm oder MDX-Skript zum Aufrufen der gespeicherten Prozedur auf. Der Debugger bricht um, wenn er eine Zeile mit einem Breakpoint erreicht. Sie können Variablen im Überwachungsfenster auswerten, Lokale anzeigen und den Code schrittweise durchlaufen.  
  
 Wenn Sie beim Debuggen einer Bibliothek Probleme haben, stellen Sie sicher, dass die entsprechende Programmdatenbankdatei (PDB-Datei) an den Bereitstellungsspeicherort auf dem Server kopiert wurde. Wurde diese Datei bei der Registrierung oder Bereitstellung nicht kopiert, müssen Sie sie manuell an denselben Speicherort wie die DLL kopieren. Bei systemeigenem Code (COM-DLL) ist die PDB-Datei im Unterverzeichnis \Debug gespeichert. Bei verwaltetem Code (CLR-DLL) ist sie im Unterverzeichnis \WINDEBUG gespeichert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellen](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren von gespeicherten Prozeduren](defining-stored-procedures.md)  
  
  
