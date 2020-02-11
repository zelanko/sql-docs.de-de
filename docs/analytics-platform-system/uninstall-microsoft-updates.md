---
title: Deinstallieren von Microsoft-Updates
description: Deinstallieren Sie Microsoft-Updates in Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: a5ebe1ee911f7500505cdbd1962d28c35461a635
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74399466"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Deinstallieren von Microsoft-Updates in Analytics Platform System
In diesem Artikel wird beschrieben, wie Sie ein zuvor installiertes Microsoft Update auf der Analytics Platform System Appliance deinstallieren.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Voraussetzungen  
Um diese Schritte ausführen zu können, benötigen Sie Folgendes:  
  
-   Eine Analytics Platform System-Anmeldung mit Berechtigungen für den Zugriff auf die Verwaltungskonsole zum Überwachen des Geräts.  
  
-   Kenntnis des Fabric-Domänen Administrator Kontos <em> <Fabric Domain> </em>, um sich beim **-HST01-** Knoten anzumelden.  
  
## <a name="HowToUninstallMSFT"></a>So deinstallieren Sie Microsoft-Updates  
  
1.  Melden Sie sich beim <em> <Fabric Domain> </em> **-HST01-** Knoten als Fabric-Domänen Administrator an.  
  
2.  Öffnen Sie ein Eingabe Aufforderungs Fenster, und geben Sie den folgenden Befehl ein, um alle Updates zu deinstallieren, die für die Deinstallation der WSUS- Ersetzen Sie die Platzhalter Elemente *<  >* durch die entsprechenden Informationen.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie unter
- [Herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Anwenden von Analytics-Plattformsystem-Hotfixes &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Deinstallieren Sie die Analytics Platform System-Hotfixes &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Software Wartung &#40;Analytics-Platt Form System&#41;](software-servicing.md)  
  
