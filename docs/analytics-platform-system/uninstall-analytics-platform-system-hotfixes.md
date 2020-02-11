---
title: Deinstallieren von Hotfixes
description: Deinstallieren Sie die-Hotfixes für Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ef6929aeb06c9472eb3ff210de016117a9636ded
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74399765"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Deinstallieren von Analytics Platform System-Hotfixes 
In den folgenden Schritten wird beschrieben, wie ein zuvor installierter-Hotfix für das Analytics Platform System deinstalliert wird  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Voraussetzungen  
Um diese Schritte ausführen zu können, benötigen Sie Folgendes:  
  
-   Eine Analytics Platform System-Anmeldung mit Berechtigungen für den Zugriff auf die Verwaltungskonsole zum Überwachen des Geräts.  
  
-   Das Domänen Administrator Konto, um sich beim <em><appliance_domain Knoten></em> **-HST01** anzumelden.  
  
-   Die Nummer des Knowledge Base-Artikels für den zu deinstallierenden Hotfix.  
  
## <a name="HowToUninstallPDW"></a>So deinstallieren Sie einen SQL Server PDW Hotfix  
  
1.  Melden Sie sich beim <em><appliance_domain </em> **-Knoten>-HST01** als Fabric-Domänen Administrator an.  
  
2.  Verwenden Sie die Option als Administrator ausführen, um eine Eingabeaufforderung zu öffnen.  
  
3.  Wechseln Sie in `C:\PDWINST\Patches\<kbarticle>\media` das *<kbarticle>* Verzeichnis, wobei die Nummer des Knowledge Base-Artikels für das zu deinstallierende Hotfix ist.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Führen Sie den folgenden Befehl aus, um den Hotfix zu entfernen.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
[Herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Deinstallieren von Microsoft Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Anwenden von Analytics-Plattformsystem-Hotfixes &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Software Wartung &#40;Analytics-Platt Form System&#41;](software-servicing.md)  
  
