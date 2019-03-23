---
title: Erneutes Bereitstellen von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 15d41b9c0e31fe4bfd86349888071721b7493661
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378949"
---
# <a name="redeployment-of-packages"></a>Erneutes Bereitstellen von Paketen
  Nachdem ein Projekt bereitgestellt wurde, kann es erforderlich werden, die Paketfunktionalität zu aktualisieren oder zu erweitern und anschließend das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, das die aktualisierten Pakete enthält, erneut bereitzustellen. Im Zusammenhang mit dem erneuten Bereitstellen von Paketen sollten Sie die zum Bereitstellungshilfsprogramm gehörenden Konfigurationseigenschaften überprüfen. Beispielsweise können Sie festlegen, dass nach dem erneuten Bereitstellen des Pakets keine Konfigurationsänderungen zulässig sein sollen.  
  
## <a name="process-for-redeployment"></a>Prozess für die erneute Bereitstellung  
 Nachdem Sie die Pakete aktualisiert haben, erstellen Sie das Projekt neu. Kopieren Sie dann den Bereitstellungsordner zum Zielcomputer, und führen Sie dann den Paketinstallations-Assistenten erneut aus.  
  
 Wenn Sie nur wenige Pakete aus dem Projekt aktualisieren, muss eventuell nicht das gesamte Projekt erneut bereitgestellt werden. Um nur wenige Pakete bereitzustellen, können Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt erstellen, diesem neuen Projekt die aktualisierten Pakete hinzufügen und dann das Projekt erstellen und bereitstellen. Die Paketkonfigurationen werden automatisch zusammen mit dem Paket kopiert, wenn Sie das Paket einem anderen Projekt hinzufügen.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Bereitstellen von Paketen mithilfe des Bereitstellungshilfsprogramms](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
