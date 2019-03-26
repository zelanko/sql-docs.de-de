---
title: Vergleichen von Skriptlösungen und benutzerdefinierten Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ec0b2486845e723feda79db87679a72a6ca4caf9
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58270654"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a>Vergleichen von Skriptlösungen und benutzerdefinierten Objekten
  In einem Skripttask oder einer Skriptkomponente in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] kann größtenteils die gleiche Funktionalität implementiert werden, die auch in einem benutzerdefinierten verwalteten Task oder einer Datenflusskomponente möglich ist. Nachfolgend finden Sie einige Überlegungen, die Ihnen bei der Auswahl des entsprechenden Typs des Tasks für Ihre Anforderungen helfen:  
  
-   Wenn die Konfiguration oder Funktionalität für ein einzelnes Paket spezifisch ist, sollten Sie den Skripttask oder die Skriptkomponente verwenden, anstatt ein benutzerdefiniertes Objekt zu entwickeln.  
  
-   Wenn die Funktionalität generisch ist und künftig auch für andere Pakete und von anderen Entwicklern verwendet werden kann, sollten Sie ein benutzerdefiniertes Objekt erstellen, anstatt eine Skriptlösung zu verwenden. Benutzerdefinierte Objekte können in beliebigen Paketen verwendet werden, wohingegen ein Skript nur in dem Paket verwendet werden kann, für das es erstellt wurde.  
  
-   Wenn der Code innerhalb des gleichen Pakets wiederverwendet wird, sollten Sie erwägen, ein benutzerdefiniertes Objekt zu erstellen. Das Kopieren von einem Skripttask bzw. einer Skriptkomponente zu einem bzw. einer anderen führt zu einer schlechteren Verwaltbarkeit, da es schwieriger ist, mehrere Kopien des Codes zu verwalten und zu aktualisieren.  
  
-   Wenn sich die Implementierung im Laufe der Zeit ändert, sollten Sie in Erwägung ziehen, ein benutzerdefiniertes Objekt zu verwenden. Benutzerdefinierte Objekte können getrennt vom übergeordneten Paket entwickelt und bereitgestellt werden. Bei einem Update der Skriptlösung muss jedoch das gesamte Paket erneut bereitgestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Paketen mit benutzerdefinierten Objekten](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
