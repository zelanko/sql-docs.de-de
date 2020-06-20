---
title: 'Lektion 2: Hinzufügen von Schleifen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ed2089257af4f82b0bbb863731a17d396dc8795c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968260"
---
# <a name="lesson-2-adding-looping"></a>Lektion 2: Hinzufügen von Schleifen
  In [Lektion 1: Erstellen des Projekts und des Basispakets](lesson-1-create-a-project-and-basic-package-with-ssis.md)haben Sie ein Paket erstellt, das Daten aus einer einzelnen Flatfilequelle extrahiert, die Daten mithilfe von Transformationen zum Suchen transformiert und schließlich die Daten in die **Fakten Tabelle factcurrency** der **AdventureWorksDW2012** -Beispieldatenbank geladen hat.  
  
 Das Verwenden einer einzelnen flachen Datei ist allerdings bei einem ETL-Vorgang (Extract, Transform and Load, Extrahieren, Transformieren und Laden) selten. Von einem typischen ETL-Vorgang würden Daten aus mehreren flachen Dateiquellen extrahiert. Das Extrahieren von Daten aus mehreren Quellen erfordert eine iterative (wiederholende) Ablaufsteuerung. Eine der am häufigsten erwarteten Features von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist die Fähigkeit, Paketen problemlos Iterationen oder Schleifen hinzuzufügen.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bietet zwei Containertypen für Schleifenvorgänge durch Pakete an: den Foreach- und den For-Schleifencontainer. Der Foreach-Schleifencontainer verwendet einen Enumerator für die Ausführung der Schleife, während der For-Schleifencontainer normalerweise einen Variablenausdruck verwendet. In dieser Lektion wird der Foreach-Schleifencontainer verwendet.  
  
 Durch den Foreach-Schleifencontainer wird es für ein Paket möglich, die Ablaufsteuerung für jedes Element eines angegebenen Enumerators zu wiederholen. Mithilfe des Foreach-Schleifencontainer können Sie die folgenden Elemente aufzählen:  
  
-   ADO-Recordsetzeilen  
  
-   ADO.NET-Schemainformationen  
  
-   Datei- und Verzeichnisstrukturen  
  
-   System-, Paket- und Benutzervariablen  
  
-   Aufzählbare Objekte in einer Variablen  
  
-   Elemente in einer Auflistung  
  
-   Knoten in einem XPath-Ausdruck (XML Path Language)  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO)  
  
 In dieser Lektion ändern Sie das in Lektion 1 erstellte einfache ETL-Paket, um die Vorteile des Foreach-Schleifencontainers nutzen zu können. Sie legen auch benutzerdefinierte Paketvariablen fest, um die Iteration durch alle flachen Dateien im Ordner für das Lernprogrammpaket zu ermöglichen. Wenn Sie die vorherige Lektion nicht abgeschlossen haben, können Sie auch das abgeschlossene Paket aus Lektion 1 kopieren, das im Lernprogramm enthalten ist.  
  
 In dieser Lektion ändern Sie nur die Ablaufsteuerung, nicht den Datenfluss.  
  
> [!IMPORTANT]  
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**finden Sie unter [Reporting Services Produktbeispiel-Projekt auf CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 1](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainers](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Schritt 3: Ändern des Flatfile-Verbindungs-Managers](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Schritt 4: Testen des Tutorialpakets aus Lektion 2](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Kopieren des Pakets aus Lektion 1](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [For-Schleifencontainer](control-flow/for-loop-container.md)  
  
  
