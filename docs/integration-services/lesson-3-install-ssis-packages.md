---
title: 'Lektion 3: Installieren von SSIS-Paketen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b6d5e59c07874ead6eeba97cc2aeaaa240464c21
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055923"
---
# <a name="lesson-3-install-ssis-packages"></a>Lektion 3: Installieren von SSIS-Paketen

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


In [Lektion 2: Erstellen des Bereitstellungspakets in SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md) haben Sie ein Bereitstellungsprogramm und das Bereitstellungspaket erstellt, das die Elemente enthält, die für die Installation der Pakete auf einem anderen Computer erforderlich sind. Sie haben außerdem die Dateiliste im Bereitstellungspaket überprüft und den Inhalt der Manifestdatei untersucht, die beim Erstellen des Bereitstellungshilfsprogramms erstellt wurde.  
  
In dieser Lektion kopieren Sie das Bereitstellungspaket auf den Zielcomputer und führen anschließend den Paketinstallations-Assistenten aus, um die Pakete, Paketabhängigkeiten und Hilfsdateien auf diesem Computer zu installieren. Die Pakete werden in der **msdb**-Datenbank von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installiert, während die anderen Elemente im Dateisystem installiert werden. Nach Abschluss der Paketinstallation testen Sie die Bereitstellung, indem Sie die Pakete mithilfe des Paketausführungshilfsprogramms in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ausführen.  
  
**Geschätzte Zeit zum Bearbeiten dieser Lektion:** 30 Minuten  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Bereitstellungspakets](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Schritt 2: Ausführen des Paketinstallations-Assistenten](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Schritt 3: Testen der bereitgestellten Pakete](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Kopieren des Bereitstellungspakets](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
  
  
