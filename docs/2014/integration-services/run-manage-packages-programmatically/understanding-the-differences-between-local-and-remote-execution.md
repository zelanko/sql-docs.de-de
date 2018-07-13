---
title: Grundlegendes zu den Unterschieden zwischen der lokalen und der Remoteausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 946419fddf2e66afc7b3182e06c6dfa5b35385fc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170941"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Grundlegendes zu den Unterschieden zwischen der lokalen und der Remoteausführung
  Paketentwickler und Administratoren sollten die Beschränkungen hinsichtlich des Ausführungsorts eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets beachten.  
  
-   **Ein Paket wird auf dem gleichen Computer ausgeführt wie das Programm, das es startet**. Auch wenn ein Progamm ein Paket lädt, das auf einem anderen Server remote gespeichert ist, wird das Paket auf dem lokalen Computer ausgeführt.  
  
-   **Sie können ein Paket außerhalb der Entwicklungsumgebung nur auf Computern ausführen, auf denen Integration Services installiert ist**. Sie können Pakete außerhalb von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nur auf Clientcomputern ausführen, auf denen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installiert ist, wobei die Bedingungen Ihrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Lizenz möglicherweise die Installation von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf weiteren Computern nicht zulassen. Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] handelt es sich um eine Serverkomponente, die nicht an Clientcomputer weitergegeben werden darf. Um Pakete von einem Clientcomputer aus auszuführen, müssen Sie diese so starten, dass die Ausführung auf dem Server sichergestellt ist.  
  
 Weitere Informationen zum Laden und Ausführen eines gespeicherten Pakets finden Sie unter:  
  
-   [Programmgesteuertes Laden und Ausführen eines lokalen Pakets](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Programmgesteuertes Laden und Ausführen eines Remotepakets](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Weitere Informationen zum Ausführen eines Pakets und Laden von dessen Ausgabe in ein benutzerdefiniertes Programm finden Sie unter:  
  
-   [Laden der Ausgabe eines lokalen Pakets](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Laden und Ausführen eines lokalen Pakets](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Programmgesteuertes Laden und Ausführen eines Remotepakets](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Laden der Ausgabe eines lokalen Pakets](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
