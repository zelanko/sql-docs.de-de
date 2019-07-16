---
title: Deinstallieren Sie Microsoft Updates – Analytics Platform System | Microsoft-Dokumentation"
description: Deinstallieren Sie Microsoft-Updates in Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f910eeb7f3b38d29f7ae7b084de981c22a6f3f4a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959831"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Deinstallieren von Microsoft-Updates in Analytics Platform System
Dieser Artikel beschreibt die Vorgehensweise beim Deinstallieren eines zuvor installierten Microsoft-Updates auf das Analytics Platform System Appliance.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Vorraussetzungen  
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
  
