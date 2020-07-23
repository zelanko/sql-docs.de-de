---
title: 'Lektion 2: Hinzufügen von Schleifen mit SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f8a7cb05ea7768877ad15ba0d71c5f7636ac8d58
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920389"
---
# <a name="lesson-2-add-looping-with-ssis"></a>Lektion 2: Hinzufügen von Schleifen mit SSIS

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



In [Lektion 1: Erstellen eines Projekts und Basispakets mit SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md) haben Sie ein Paket erstellt, das Daten aus einer einzelnen Flatfilequelle extrahiert. Die Daten werden dann mithilfe von Suchtransformationen transformiert. Zuletzt lädt das Paket die Daten in einer Kopie der Faktentabelle **FactCurrencyRate** der Beispieldatenbank **AdventureWorksDW2012**.  
  
Bei einem ETL-Prozess (Extrahieren, Transformieren und Laden) werden in der Regel Daten aus mehreren Flatfilequellen extrahiert. Das Extrahieren von Daten aus mehreren Quellen erfordert eine iterative (wiederholende) Ablaufsteuerung. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] kann ganz einfach Iterationen und Schleifen zu Paketen hinzufügen.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bietet zwei Containertypen für Schleifenvorgänge durch Pakete an: den Foreach- und den For-Schleifencontainer. Der Foreach-Schleifencontainer verwendet einen Enumerator für die Ausführung der Schleife, während der For-Schleifencontainer in der Regel einen Variablenausdruck verwendet. In dieser Lektion wird der Foreach-Schleifencontainer verwendet.  
  
Durch den Foreach-Schleifencontainer wird es für ein Paket möglich, die Ablaufsteuerung für jedes Element eines angegebenen Enumerators zu wiederholen. Mithilfe des Foreach-Schleifencontainer können Sie die folgenden Elemente aufzählen:  
  
-   ADO-Recordsetzeilen  
  
-   ADO.NET-Schemainformationen  
  
-   Datei- und Verzeichnisstrukturen  
  
-   System-, Paket- und Benutzervariablen  
  
-   Aufzählbare Objekte in einer Variablen  
  
-   Elemente in einer Auflistung  
  
-   Knoten in einem XPath-Ausdruck (XML Path Language)  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO)  
  
In dieser Lektion erfahren Sie, wie Sie das ETL-Beispielpaket aus Lektion 1 für die Verwendung einer Foreach-Schleife verwenden und eine benutzerdefinierte Paketvariable für das Paket festlegen. Diese Variable wird dann verwendet, um übereinstimmende Dateien im Beispielordner durchzugehen.   
  
In dieser Lektion ändern Sie nur die Ablaufsteuerung, nicht den Datenfluss.  
  
> [!NOTE]  
> Machen Sie sich, falls noch nicht geschehen, mit den [Anforderungen für Lektion 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites) vertraut.

## <a name="lesson-tasks"></a>Aufgaben der Lektion  
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainers](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Schritt 3: Ändern des Verbindungs-Managers für Flatfiles](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Schritt 4: Testen des Tutorialpakets aus Lektion 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Kopieren des Pakets aus Lektion 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[For-Schleifencontainer](../integration-services/control-flow/for-loop-container.md)  
  
  
  
