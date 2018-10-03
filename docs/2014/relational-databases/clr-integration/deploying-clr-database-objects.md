---
title: Bereitstellen von CLR-Datenbankobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- deployment script [CLR integration]
- common language runtime [SQL Server], deploying
- deploying assemblies [CLR integration]
- deploying [CLR integration]
ms.assetid: 00752573-3367-41a7-af98-7b7a29e8e2f2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4e06dfced9b9800c0e5c0b7d0dca208bac67c900
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122780"
---
# <a name="deploying-clr-database-objects"></a>Bereitstellen von CLR-Datenbankobjekten
  Die Verteilung einer fertigen Anwendung oder eines Moduls zur Installation und Ausführung auf anderen Computern wird als Bereitstellung bezeichnet. Bei Verwendung von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio können Sie CLR-Datenbankobjekte (Common Language Runtime) entwickeln und auf einem Testserver bereitstellen. Stattdessen können verwaltete Datenbankobjekte auch mit den Redistributionsdateien von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework statt mit Visual Studio kompiliert werden. Die kompilierten Assemblys, die die CLR-Datenbankobjekte enthalten, können dann mit Visual Studio- oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen auf einem Testserver bereitgestellt werden. Beachten Sie, dass Visual Studio .NET 2003 nicht für CLR-Integrationsprogrammierung oder Bereitstellung verwendet werden kann. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] beinhaltet ein vorinstalliertes .NET Framework, und Visual Studio .NET 2003 kann nicht die .NET Framework 2.0-Assemblys verwenden.  
  
 Sobald die CLR-Methoden auf dem Testserver getestet und verifiziert wurden, können sie mit einem Bereitstellungsskript auf die Produktionsserver verteilt werden. Das Bereitstellungsskript kann manuell oder mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] generiert werden (siehe das Verfahren weiter unten in diesem Thema).  
  
 Die CLR-Integrationsfunktion ist in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Standardeinstellung deaktiviert und muss aktiviert werden, damit CLR-Assemblys verwendet werden können. Weitere Informationen finden Sie unter [Enabling CLR Integration](clr-integration-enabling.md).  
  
## <a name="deploying-the-assembly-to-the-test-server"></a>Bereitstellen der Assembly auf einem Testserver  
 Mithilfe von Visual Studio können Sie CLR-Funktionen, -Prozeduren, -Trigger, benutzerdefinierte Typen (UDTs) und benutzerdefinierte Aggregate entwickeln und diese auf einem Testserver bereitstellen. Diese verwalteten Datenbankobjekte können auch mit den Befehlszeilencompilern, z.  csc.exe und vbc.exe, die in den Redistributionsdateien von .NET Framework enthalten sind, kompiliert werden. Die integrierte Entwicklungsumgebung von Visual Studio ist nicht für die Entwicklung verwalteter Datenbankobjekte für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erforderlich.  
  
 Stellen Sie sicher, dass alle Compilerfehler und -warnungen aufgelöst werden. Die Assemblys, die die CLR-Routinen enthalten, können dann mit Visual Studio- oder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anweisungen in einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Datenbank registriert werden.  
  
> [!NOTE]  
>  Das TCP/IP-Netzwerkprotokoll muss in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz aktiviert werden, damit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio von einem Remotecomputer aus zum Entwickeln, Debuggen und Bereitstellen verwendet werden kann. Weitere Informationen zum Aktivieren des TCP/IP-Protokolls auf dem Server finden Sie unter [Konfigurieren von Clientprotokollen](../../database-engine/configure-windows/configure-client-protocols.md).  
  
#### <a name="to-deploy-the-assembly-using-visual-studio"></a>So stellen Sie eine Assembly mit Visual Studio bereit  
  
1.  Erstellen Sie das Projekt durch Auswahl **erstellen** \<Projektname > aus der **erstellen** Menü.  
  
2.  Lösen Sie alle Erstellungsfehler und -warnungen vor dem Bereitstellen der Assembly auf dem Testserver auf.  
  
3.  Wählen Sie **bereitstellen** aus der **erstellen** Menü. Die Assembly wird dann in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz und Datenbank registriert, die bei der Erstellung des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Projekts in Visual Studio angegeben wurden.  
  
#### <a name="to-deploy-the-assembly-using-transact-sql"></a>So stellen Sie die Assembly mit Transact-SQL bereit  
  
1.  Kompilieren Sie die Assembly mit den in .NET Framework enthaltenen Befehlszeilencompilern aus der Quelldatei.  
  
2.  Für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#-Quelldateien gilt:  
  
3.  `csc /target:library C:\helloworld.cs`  
  
4.  Für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic-Quelldateien gilt:  
  
 `vbc /target:library C:\helloworld.vb`  
  
 Mit diesen Befehlen wird der Visual C# - bzw. Visual Basic-Compiler unter Angabe der `/target`-Option aufgerufen, die festlegt, dass eine Bibliotheks-DLL erstellt werden soll.  
  
1.  Lösen Sie alle Erstellungsfehler und -warnungen vor dem Bereitstellen der Assembly auf dem Testserver auf.  
  
2.  Öffnen Sie [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] auf dem Testserver. Erstellen Sie eine neue Abfrage, die mit einer geeigneten Testdatenbank (z. B. AdventureWorks) verbunden ist.  
  
3.  Erstellen Sie die Assembly im Server, indem Sie der Abfrage den folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Code hinzufügen.  
  
 `CREATE ASSEMBLY HelloWorld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE;`  
  
1.  Die Prozedur, die Funktion, das Aggregat, der benutzerdefinierte Typ oder der Trigger müssen dann in der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erstellt werden. Wenn die `HelloWorld`-Assembly eine Methode namens `HelloWorld` in der `Procedures`-Klasse enthält, dann kann der folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Code der Abfrage hinzugefügt werden, um in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Prozedur namens `hello` zu erstellen.  
  
 `CREATE PROCEDURE hello`  
  
 `AS`  
  
 `EXTERNAL NAME HelloWorld.Procedures.HelloWorld`  
  
 Weitere Informationen zum Erstellen der verschiedenen Typen verwalteter Datenbankobjekte in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], finden Sie unter [benutzerdefinierte CLR-Funktionen](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md), [benutzerdefinierte CLR-Aggregate](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md), [CLR Benutzerdefinierte Typen](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), [CLR-gespeicherte Prozeduren](../../database-engine/dev-guide/clr-stored-procedures.md), und [CLR-Trigger](../../database-engine/dev-guide/clr-triggers.md).  
  
## <a name="deploying-the-assembly-to-production-servers"></a>Bereitstellen der Assembly auf einem Produktionsserver  
 Sobald die CLR-Datenbankobjekte auf dem Testserver getestet und verifiziert wurden, können sie mit einem Bereitstellungsskript auf die Produktionsserver verteilt werden. Weitere Informationen zum Debuggen verwalteter Datenbankobjekte finden Sie unter [Debuggen von CLR-Datenbankobjekten](debugging-clr-database-objects.md).  
  
 Die Bereitstellung verwalteter Datenbankobjekte ähnelt der Bereitstellung gewöhnlicher Datenbankobjekte (Tabellen, [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Routinen usw.). Die Assemblys, in denen die CLR-Datenbankobjekte enthalten sind, können mit einem Bereitstellungsskript auf anderen Servern bereitgestellt werden. Das Bereitstellungsskript kann mit der Funktion "Skripts generieren" von [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] erstellt werden. Das Bereitstellungsskript kann auch manuell erstellt oder mit "Skripts generieren" erzeugt und dann manuell abgeändert werden. Nachdem das Bereitstellungsskript erstellt wurde, kann es zur Bereitstellung der verwalteten Datenbankobjekte auf anderen Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt werden.  
  
#### <a name="to-generate-a-deployment-script-using-generate-scripts"></a>So generieren Sie ein Bereitstellungsskript mit 'Skript generieren'  
  
1.  Öffnen Sie [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], und stellen Sie eine Verbindung mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz her, in der die bereitzustellende verwaltete Assembly oder das bereitzustellende Datenbankobjekt registriert ist.  
  
2.  In der **Objekt-Explorer**, erweitern Sie die  **\<Servername >** und **Datenbanken** Strukturen. Mit der rechten Maustaste in der Datenbank, in dem das verwaltete Datenbankobjekt registriert, wählen ist **Aufgaben**, und wählen Sie dann **Skripts generieren**. Der Skript-Assistent wird geöffnet.  
  
3.  Wählen Sie die Datenbank aus dem Listenfeld aus, und klicken Sie auf **Weiter**.  
  
4.  In der **Skriptoptionen auswählen** Bereich, klicken Sie auf **Weiter**, oder ändern Sie die Optionen, und klicken Sie dann auf **Weiter**.  
  
5.  In der **Objekttypen auswählen** Bereich, wählen Sie den Typ des Datenbankobjekts bereitgestellt werden. Klicken Sie auf **Weiter**.  
  
6.  Für jeden Objekttyp, der im ausgewählten der **Objekttypen auswählen** Bereich eine **auswählen \<Typ >** Bereich angezeigt wird. In diesem Bereich stehen alle Instanzen des betreffenden Datenbankobjekttyps zur Auswahl, die in der angegebenen Datenbank registriert sind. Wählen Sie ein oder mehrere Objekte aus, und klicken Sie auf **Weiter**.  
  
7.  Die **Ausgabeoptionen** Bereich angezeigt wird, wenn alle gewünschten Datenbankobjekttypen ausgewählt wurden. Wählen Sie **Skript in Datei schreiben** , und geben Sie einen Dateipfad für das Skript. Wählen Sie **Weiter**aus. Überprüfen Sie Ihre Auswahl, und klicken Sie auf **Fertig stellen**. Das Bereitstellungsskript wird im angegebenen Dateipfad gespeichert.  
  
## <a name="post-deployment-scripts"></a>Skripts nach der Bereitstellung  
 Sie können ein Skript nach der Bereitstellung ausführen.  
  
 Fügen Sie eine Datei mit dem Namen postdeployscript.sql dem Visual Studio-Projektverzeichnis hinzu, um ein nach der Bereitstellung auszuführendes Skript hinzuzufügen. Z. B. mit der rechten Maustaste des Projekts im **Projektmappen-Explorer** , und wählen Sie **vorhandenes Element hinzufügen**. Fügen Sie die Datei in den Stammordner des Projekts und nicht in den Ordner Testskripts ein.  
  
 Wenn Sie das Projekt bereitstellen, führt Visual Studio nach der Bereitstellung des Projekts dieses Skript aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
