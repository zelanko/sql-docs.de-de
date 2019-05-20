---
title: 'Lektion 6: Verwenden von Parametern mit dem Projektbereitstellungsmodell in SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 54fb96d23fb02be01068ce5c2206913a0e6716f0
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65721053"
---
# <a name="lesson-6-use-parameters-with-the-project-deployment-model-in-ssis"></a>Lektion 6: Verwenden von Parametern mit dem Projektbereitstellungsmodell in SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In SQL Server 2012 wurde ein neues Bereitstellungsmodell eingeführt, mit dem Sie Projekte auf dem Integration Services-Server bereitstellen können. Der Integration Services-Server ermöglicht es Ihnen, Pakete zu verwalten und auszuführen sowie Laufzeitwerte für Pakete zu konfigurieren.  
  
In dieser Lektion ändern Sie das Paket, das Sie in [Lektion 5: Hinzufügen von SSIS-Paketkonfigurationen für das Paketbereitstellungsmodell](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) erstellt haben, sodass es das Paketbereitstellungsmodell verwendet. Sie ersetzen den Konfigurationswert durch einen Parameter, um den Speicherort der Beispieldaten anzugeben. Sie können auch das abgeschlossene Paket aus Lektion 5 kopieren, das im Lieferumfang der Lernprogramme enthalten ist.  
  
Konvertieren Sie das Projekt mithilfe des Konfigurations-Assistenten für Integration Services-Projekte in das Projektbereitstellungsmodell. Bei diesem Modell wird die Directory-Eigenschaft mithilfe eines Parameters statt mit einem Konfigurationswert festgelegt. Diese Lektion enthält einen Teil der Schritte, die Sie ausführen müssen, um vorhandene SSIS-Pakete in das neue Projektbereitstellungsmodell zu konvertieren.  
  
Wenn Sie das Paket erneut ausführen, verwendet der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server den Parameter, um den Wert der Variablen aufzufüllen. Mit der Variablen wiederum wird die Directory-Eigenschaft aktualisiert. Das Paket durchläuft die Dateien im Datenordner, der durch den neuen Parameter angegeben wird.  
  
> [!NOTE]
> Machen Sie sich, falls noch nicht geschehen, mit den [Anforderungen für Lektion 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites) vertraut.
    
## <a name="lesson-tasks"></a>Aufgaben der Lektion  
Diese Lektion enthält die folgenden Aufgaben:  
  
1.  [Schritt 1: Kopieren des Pakets aus Lektion 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Schritt 3: Testen des Pakets aus Lektion 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Schritt 4: Bereitstellen des Pakets aus Lektion 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Kopieren des Pakets aus Lektion 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
