---
title: Deinstallieren Sie Microsoft Updates – Analytics Platform System | Microsoft-Dokumentation"
description: Deinstallieren Sie Microsoft-Updates in Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4739d05b1878c8b7fc9f66f2e0b8145ff1044e54
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54254765"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Deinstallieren von Microsoft-Updates in Analytics Platform System
Dieser Artikel beschreibt die Vorgehensweise beim Deinstallieren eines zuvor installierten Microsoft-Updates auf das Analytics Platform System Appliance.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Diese Schritte ausführen zu können, benötigen Sie:  
  
-   Eine Analytics Platform System Anmeldenamen mit Berechtigungen zum Zugriff auf die Admin-Konsole zum Überwachen der Appliance.  
  
-   Kenntnisse über die Fabric-Domänenadministratorkonto Anmeldung an der <em> <Fabric Domain> </em> **-HST01** Knoten.  
  
## <a name="HowToUninstallMSFT"></a>So deinstallieren Sie Microsoft-updates  
  
1.  Melden Sie sich bei der <em> <Fabric Domain> </em> **-HST01** als Domänenadministrator Fabric-Knoten.  
  
2.  Um alle Updates zu deinstallieren, die für die WSUS, um die Deinstallation genehmigt ist, öffnen Sie ein Eingabeaufforderungsfenster, und geben Sie den folgenden Befehl aus. Ersetzen Sie die Platzhalterelemente *< >* durch die entsprechenden Informationen.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie in den folgenden Themen:
- [Microsoft-Updates herunterzuladen und anzuwenden &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Anwenden von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Deinstallieren von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Softwarewartung &#40;Analytics Platform System&#41;](software-servicing.md)  
  
