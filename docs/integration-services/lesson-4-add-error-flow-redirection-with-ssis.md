---
title: 'Lektion 4: Hinzufügen der Fehlerflussumleitung mit SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 3ad643a65eb83b1593b21782ad9784d5062c3899
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055762"
---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>Lektion 4: Hinzufügen der Fehlerflussumleitung mit SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Um mögliche Fehler im Transformationsprozess zu behandeln, können Sie mithilfe von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] auf der Grundlage von Komponenten oder Spalten entscheiden, wie Daten zu handhaben sind, die von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] nicht transformiert werden können. Sie können einen Fehler in bestimmten Spalten ignorieren, die ganze fehlerverursachende Zeile umleiten oder die Komponente als fehlerhaft behandeln. Standardmäßig sind Komponenten in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] so konfiguriert, dass sie bei Fehlern fehlschlagen. Die fehlerhafte Komponente verursacht wiederum einen Paketausführungsfehler, wodurch die Verarbeitung beendet wird.  
  
Dies können Sie vermeiden, indem Sie potenzielle Verarbeitungsfehler erst bei ihrem Auftreten konfigurieren und behandeln. Eine Option besteht darin, alle Fehler zu ignorieren, damit das Paket immer erfolgreich ausgeführt wird. Sie haben auch die Möglichkeit, die fehlerverursachende Zeile zu einem anderen Verarbeitungspfad umzuleiten, wo die Daten und Fehler gespeichert, untersucht und nochmals verarbeitet werden können.  
  
In dieser Lektion erstellen Sie eine Kopie des Pakets, das Sie in [Lektion 3: Hinzufügen der Protokollierung mit SSIS](../integration-services/lesson-3-add-logging-with-ssis.md) entwickelt haben. Beim Arbeiten mit diesem neuen Paket erstellen Sie eine beschädigte Version von einer der Beispieldatendateien. Durch die beschädigte Datei wird beim Ausführen des Pakets ein Verarbeitungsfehler ausgelöst.  
  
Zur Behandlung der Fehlerdaten fügen Sie ein Flatfileziel hinzu und konfigurieren es. Dieses schreibt dann die fehlerverursachenden Zeilen in eine Fehlerdatei. 
  
Bevor [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Fehlerdaten in die Datei schreibt, binden Sie eine Skriptkomponente ein, die Fehlerbeschreibungen abruft. Anschließend konfigurieren Sie die Lookup Currency Key-Transformation neu, um alle Daten, die nicht verarbeitet werden konnten, zur Skripttransformation umzuleiten.  
  
## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Machen Sie sich, falls noch nicht geschehen, mit den [Anforderungen für Lektion 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites) vertraut.
 
## <a name="lesson-task"></a>Aufgaben in dieser Lektion
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Schritt 2: Erstellen einer beschädigten Datei](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Schritt 3: Hinzufügen der Fehlerflussumleitung](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Schritt 4: Hinzufügen eines Flatfileziels](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Schritt 5: Testen des Tutorialpakets aus Lektion 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Kopieren des Pakets aus Lektion 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
