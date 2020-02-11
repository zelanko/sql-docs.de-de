---
title: 'Lektion 2: Erstellen des Bereitstellungs Pakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8ec7519a4ea203693e6520eee569639a3259215f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767512"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a>Lektion 2: Erstellen des Bereitstellungspakets
  In [Lektion 1: Vorbereiten der Erstellung des Bereitstellungspakets](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)haben Sie das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit Namen „Deployment Tutorial“ erstellt, diesem die Pakete und Unterstützungsdateien hinzugefügt und Konfigurationen in Paketen implementiert.  
  
 In dieser Lektion erstellen Sie das Bereitstellungspaket. Dabei handelt es sich um einen Ordner, der die Elemente enthält, die Sie benötigen, um Pakete auf einem anderen Computer zu installieren. Das Bereitstellungspaket enthält ein Bereitstellungsmanifest, Kopien der Pakete und Kopien der Unterstützungsdateien aus dem Deployment Tutorial-Projekt. Im Bereitstellungsmanifest werden die Pakete, verschiedene Dateien und Konfigurationen im Bereitstellungspaket aufgelistet.  
  
 Sie überprüfen auch die Dateiliste im Bereitstellungspaket und untersuchen den Inhalt des Manifests.  
  
 **Geschätzte Zeit zum Bearbeiten dieser Lektion:** 30 Minuten  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Erstellen des Bereitstellungshilfsprogramms](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [Schritt 2: Überprüfen des Bereitstellungspakets](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Erstellen des Bereitstellungshilfsprogramms](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
![Integration Services Symbol (klein)](media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
