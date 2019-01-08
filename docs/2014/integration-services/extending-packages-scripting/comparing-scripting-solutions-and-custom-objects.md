---
title: Vergleichen von Skriptlösungen und benutzerdefinierten Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9529c7949d17b402f8c83d44417d8c4588f71e70
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368932"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a>Vergleichen von Skriptlösungen und benutzerdefinierten Objekten
  In einem Skripttask oder einer Skriptkomponente in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] kann größtenteils die gleiche Funktionalität implementiert werden, die auch in einem benutzerdefinierten verwalteten Task oder einer Datenflusskomponente möglich ist. Nachfolgend finden Sie einige Überlegungen, die Ihnen bei der Auswahl des entsprechenden Typs des Tasks für Ihre Anforderungen helfen:  
  
-   Wenn die Konfiguration oder Funktionalität für ein einzelnes Paket spezifisch ist, sollten Sie den Skripttask oder die Skriptkomponente verwenden, anstatt ein benutzerdefiniertes Objekt zu entwickeln.  
  
-   Wenn die Funktionalität generisch ist und künftig auch für andere Pakete und von anderen Entwicklern verwendet werden kann, sollten Sie ein benutzerdefiniertes Objekt erstellen, anstatt eine Skriptlösung zu verwenden. Benutzerdefinierte Objekte können in beliebigen Paketen verwendet werden, wohingegen ein Skript nur in dem Paket verwendet werden kann, für das es erstellt wurde.  
  
-   Wenn der Code innerhalb des gleichen Pakets wiederverwendet wird, sollten Sie erwägen, ein benutzerdefiniertes Objekt zu erstellen. Das Kopieren von einem Skripttask bzw. einer Skriptkomponente zu einem bzw. einer anderen führt zu einer schlechteren Verwaltbarkeit, da es schwieriger ist, mehrere Kopien des Codes zu verwalten und zu aktualisieren.  
  
-   Wenn sich die Implementierung im Laufe der Zeit ändert, sollten Sie in Erwägung ziehen, ein benutzerdefiniertes Objekt zu verwenden. Benutzerdefinierte Objekte können getrennt vom übergeordneten Paket entwickelt und bereitgestellt werden. Bei einem Update der Skriptlösung muss jedoch das gesamte Paket erneut bereitgestellt werden.  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Paketen mit benutzerdefinierten Objekten](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
