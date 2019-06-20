---
title: Anwenden von Hotfixes für Analytics Platform System | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie die Hotfixes für Analytics Platform System-Software gelten.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b4b72017bb23ae44da9c5884f0ebf2a8b099fd3e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63019045"
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Anwenden von Hotfixes für Analytics Platform System
Dieser Artikel beschreibt, wie Sie die Hotfixes für Analytics Platform System-Software gelten.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
> [!WARNING]  
> Versuchen Sie nicht, einen Hotfix für Analytics Platform System anwenden, ist dem Gerät oder eine appliancekomponente heruntergefahren oder in einem fehlerhaften Zustand. In diesem Fall erhalten Sie Support um Unterstützung zu erhalten.  
  
> [!WARNING]  
> Einen Hotfix für Analytics Platform System werden nicht angewendet werden, während das Gerät verwendet wird. Anwendung eines Hotfixes kann dazu führen, dass applianceknoten neu starten. Der Hotfix sollte während eines Wartungsfensters übernommen werden, wenn das Gerät nicht verwendet wird.  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Diese Schritte ausführen zu können, benötigen Sie:  
  
-   Eine Analytics Platform System Anmeldenamen mit Berechtigungen für die Verwaltungskonsole zum Überwachen des Status des Geräts zugreifen. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Kenntnisse über die Fabric-Domänenadministratorkonto für die Verbindung der _< Domänenname >_ **-HST01** Knoten.  
  
## <a name="HowToInstallPDW"></a>Zum Installieren eines Hotfixes für Analytics Platform System  
Im Gegensatz zu den Microsoft-Updates werden die Hotfixes für Analytics Platform System-Software nicht über WSUS behandelt. Ein anderer Workflow, und durch Ausführen eines Hotfixpakets installiert sind.  
  
1.  **Überprüfen Sie die Appliance Statusindikatoren.**  
  
    1.  Öffnen Sie die Admin-Konsole, und navigieren Sie zu der Seite "Status der Appliance". Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  Alle rote oder gelbe Indikatoren müssen aufgelöst werden, bevor Sie mit dem nächsten Schritt fortfahren. Einige Ausnahmen sind:  
  
        -   Wenn Datenträgerfehler sind, verwenden Sie der Seite "Admin-Konsole Warnungen", um sicherstellen, dass derzeit nicht mehr als ein Fehler auf dem Datenträger in jedem Server oder die SAN-Array. Ist nicht mehr als einen Datenträgerfehler in jedem Server oder die SAN-Array, können Sie vor dem Korrigieren der Fehler(n) Datenträger mit dem nächsten Schritt fortfahren. Achten Sie darauf, dass Sie den Microsoft-Support, um die Fehler(n) Datenträger so bald wie möglich zu beheben.  
  
        -   Ist ein nicht kritische (gelb) Volume Datenträgerfehler, der nicht auf dem Laufwerk C:\ ist, können Sie vor dem Beheben des Fehlers der Datenträger-Volume mit dem nächsten Schritt fortfahren.  
  
2.  **Installieren Sie den Hotfix für Analytics Platform System**  
  
    1.  Melden Sie sich die <*Appliance_domain*>-HST01 Knoten als Domänenadministrator an.  
  
    2.  Verwenden der **als Administrator ausführen** Option, um eine Eingabeaufforderung zu öffnen.  
  
    3.  Führen Sie den folgenden Befehl aus, und Ersetzen Sie dabei *<HotfixPackageName>* durch den Namen der ausführbaren Datei Hotfix-Paket, und Ersetzen Sie die anderen Elemente der Platzhalter *< >* durch die entsprechenden Informationen.  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  Führen Sie die Schritte aus, wie durch das Hotfix-Paket angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
[Microsoft-Updates herunterzuladen und anzuwenden &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Deinstallieren von Microsoft-Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Deinstallieren von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Softwarewartung &#40;Analytics Platform System&#41;](software-servicing.md)  
  
