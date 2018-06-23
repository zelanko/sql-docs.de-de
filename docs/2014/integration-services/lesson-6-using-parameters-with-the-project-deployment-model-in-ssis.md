---
title: 'Lektion 6: Verwenden von Parametern mit dem Projektbereitstellungsmodell | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f202c6b24d8f6b4ff0cfde431502b4b4cc3ed769
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048757"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a>Lektion 6: Verwenden von Parametern mit dem Projektbereitstellungsmodell
  In SQL Server 2012 wird ein neues Bereitstellungsmodell eingeführt, mit dem Sie Projekte auf dem Integration Services-Server bereitstellen können. Der Integration Services-Server ermöglicht es Ihnen, Pakete zu verwalten und auszuführen sowie Laufzeitwerte für Pakete zu konfigurieren.  
  
 In dieser Lektion ändern Sie das Paket, das Sie erstellt haben [Lektion 5: Hinzufügen von Paketkonfigurationen für das Paketbereitstellungsmodell](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) das Projektbereitstellungsmodell verwenden. Sie ersetzen den Konfigurationswert durch einen Parameter, um den Speicherort der Beispieldaten anzugeben. Sie können auch das abgeschlossene Paket aus Lektion 5 kopieren, das im Lieferumfang der Lernprogramme enthalten ist.  
  
 Mithilfe des Assistenten zum Konvertieren von Integration Services-Projekten konvertieren Sie das Projekt in das Projektbereitstellungsmodell und verwenden einen Parameter anstelle eines Konfigurationswerts, um die Directory-Eigenschaft festzulegen. Diese Lektion enthält einen Teil der Schritte, die Sie ausführen müssen, um vorhandene SSIS-Pakete in das neue Projektbereitstellungsmodell zu konvertieren.  
  
 Wenn Sie das Paket erneut ausführen, verwendet der Integration Services-Dienst den Parameter, um den Wert der Variablen aufzufüllen, und die Variable aktualisiert wiederum die Directory-Eigenschaft. Deshalb durchläuft das Paket die Dateien im neuen, durch den Parameterwert angegebenen Datenordner anstatt in dem Ordner, der in der Paketkonfigurationsdatei festgelegt wurde.  
  
> [!IMPORTANT]  
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zur Installation und Bereitstellung von **AdventureWorksDW2012**finden Sie unter [Überlegungen zum Installieren der SQL Server-Beispiele und -Beispieldatenbanken](http://technet.microsoft.com/library/ms161556%28v=sql.105%29).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
1.  [Schritt 1: Kopieren des Pakets aus Lektion 5](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Schritt 3: Testen des Pakets aus Lektion 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Schritt 4: Bereitstellen des Pakets aus Lektion 6](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Kopieren des Pakets aus Lektion 5](lesson-6-1-copying-the-lesson-5-package.md)  
  
  