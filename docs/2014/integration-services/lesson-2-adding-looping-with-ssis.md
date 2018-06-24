---
title: 'Lektion 2: Hinzufügen von Schleifen | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
caps.latest.revision: 31
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 46f67531366ef7ff91e3afcc4b8d55b7cc08635e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049000"
---
# <a name="lesson-2-adding-looping"></a>Lektion 2: Hinzufügen von Schleifen
  In [Lektion 1: Erstellen des Projekts und Basispakets](lesson-1-create-a-project-and-basic-package-with-ssis.md), Sie erstellt ein Paket, das Daten aus einer einzelnen Flatfilequelle extrahiert, mithilfe der Suchtransformationen transformiert und schließlich laden die Daten in der  **FactCurrency** der Faktentabelle der **AdventureWorksDW2012** -Beispieldatenbank.  
  
 Das Verwenden einer einzelnen flachen Datei ist allerdings bei einem ETL-Vorgang (Extract, Transform and Load, Extrahieren, Transformieren und Laden) selten. Von einem typischen ETL-Vorgang würden Daten aus mehreren flachen Dateiquellen extrahiert. Das Extrahieren von Daten aus mehreren Quellen erfordert eine iterative (wiederholende) Ablaufsteuerung. Mit [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist es auf einfache Weise möglich, Iterationen oder Schleifen zu Paketen hinzuzufügen.  
  
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
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**finden Sie unter [Reporting Services Produktbeispiel-Projekt auf CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 1](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainers](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Schritt 3: Ändern des Flatfile-Verbindungs-Managers](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Schritt 4: Testen des Tutorialpakets aus Lektion 2](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Kopieren des Pakets aus Lektion 1](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Siehe auch  
 [For-Schleifencontainer](control-flow/for-loop-container.md)  
  
  