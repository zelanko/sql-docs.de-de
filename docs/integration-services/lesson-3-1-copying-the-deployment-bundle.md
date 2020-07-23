---
title: 'Schritt 1: Kopieren des Bereitstellungspakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eac15d46e1530d0a742a3161e0622233c05ac3da
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918150"
---
# <a name="lesson-3-1---copying-the-deployment-bundle"></a>Lektion 3-1: Kopieren des Bereitstellungspakets

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


In diesem Schritt kopieren Sie das Bereitstellungspaket auf den Zielcomputer.  
  
Die einfachste Methode zum Kopieren des Bereitstellungspakets auf den Zielcomputer besteht darin, zuerst eine öffentliche Freigabe auf dem Zielcomputer zu erstellen, diese einem Laufwerk zuzuordnen und dann das Bereitstellungspaket auf die Freigabe zu kopieren. Wenn Sie nicht wissen, wie Sie öffentliche Ordner erstellen und konfigurieren oder Laufwerke zuordnen, dann finden Sie weitere Informationen in der Windows-Dokumentation.  
  
### <a name="to-copy-the-deployment-bundle"></a>So kopieren Sie das Bereitstellungspaket  
  
1.  Suchen Sie das Bereitstellungspaket auf Ihrem Computer.  
  
    Wenn Sie den Standardspeicherort verwendet haben, befindet sich das Bereitstellungspaket im Bin\Deployment-Ordner innerhalb des Deployment Tutorial-Ordners.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner Deployment und anschließend auf **Kopieren**.  
  
3.  Suchen Sie die öffentliche Freigabe, auf die Sie den Ordner auf dem Zielcomputer kopieren möchten, und klicken Sie auf **Einfügen**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
[Schritt 2: Ausführen des Paketinstallations-Assistenten](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
  
  
