---
title: Anwenden von Hotfixes für Analytics Platform System
description: In diesem Artikel wird erläutert, wie Sie Hotfixes auf die Analytics-Platt Form System Software anwenden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: fd62413ec8542aba9f3973d0e8483cb9c5c9128a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401376"
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Anwenden von Hotfixes für Analytics Platform System
In diesem Artikel wird erläutert, wie Sie Hotfixes auf die Analytics-Platt Form System Software anwenden.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
> [!WARNING]  
> Versuchen Sie nicht, einen Analyse Platt Form System-Hotfix anzuwenden, wenn Ihr Gerät oder eine Appliance-Komponente ausgefallen ist oder sich in einem failoverzustand befindet. Wenden Sie sich in diesem Fall an den Support.  
  
> [!WARNING]  
> Wenden Sie keinen Analytics Platform System-Hotfix an, während das Gerät verwendet wird. Durch das Anwenden eines Hotfixes können Geräteknoten neu gestartet werden. Der Hotfix sollte bei einem Wartungsfenster angewendet werden, wenn das Gerät nicht verwendet wird.  
  
### <a name="prerequisites"></a>Voraussetzungen  
Um diese Schritte ausführen zu können, benötigen Sie Folgendes:  
  
-   Eine Analytics Platform System-Anmeldung mit Berechtigungen für den Zugriff auf die Verwaltungskonsole, um den Gerätestatus zu überwachen. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Kenntnis des Fabric-Domänen Administrator Kontos, um eine Verbindung mit dem _<domain_name Knoten ">_ **-HST01** " herzustellen.  
  
## <a name="to-apply-a-analytics-platform-system-hotfix"></a><a name="HowToInstallPDW"></a>So wenden Sie einen Analyse Platt Form System-Hotfix an  
Im Gegensatz zu den Microsoft-Updates werden die Hotfixes für die Analytics-Platt Form System Software nicht durch WSUS behandelt. Sie verfügen über einen anderen Workflow und werden durch Ausführen eines Hotfixpakets installiert.  
  
1.  **Überprüfen der Status Indikatoren des Geräts.**  
  
    1.  Öffnen Sie die Verwaltungskonsole, und navigieren Sie zur Seite Gerätestatus. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  Alle roten oder gelben Indikatoren müssen aufgelöst werden, bevor Sie mit dem nächsten Schritt fortfahren. Dies sind einige Ausnahmen:  
  
        -   Wenn Datenträger Fehler auftreten, überprüfen Sie mithilfe der Seite Warnungen der Verwaltungskonsole, ob innerhalb der einzelnen Server-oder SAN-Arrays nicht mehr als ein Datenträger Fehler aufgetreten ist. Wenn innerhalb der einzelnen Server oder SAN-Arrays nicht mehr als ein Datenträger Fehler auftritt, können Sie mit dem nächsten Schritt fortfahren, bevor Sie die Datenträger Fehler beheben. Stellen Sie sicher, dass Sie sich an den Microsoft Support wenden, um die Datenträger Fehler so schnell wie möglich zu beheben.  
  
        -   Wenn ein nicht kritischer (gelber) datenträgervolumefehler vorliegt, der nicht auf C:\ fest liegt. Laufwerk, Sie können mit dem nächsten Schritt fortfahren, bevor Sie den Datenträger Volume-Fehler beheben.  
  
2.  **Installieren des Hotfixes für den Analytics-Platt Form System**  
  
    1.  Melden Sie sich beim <*appliance_domain* Knoten ">-HST01" als Domänen Administrator an.  
  
    2.  Verwenden Sie die Option **als Administrator ausführen** , um eine Eingabeaufforderung zu öffnen.  
  
    3.  Führen Sie den folgenden Befehl aus *<HotfixPackageName>* , und ersetzen Sie durch den Namen des ausführbaren Hotfix-Pakets. ersetzen Sie dabei die anderen Platzhalter Elemente *<  >* durch die entsprechenden Informationen.  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  Führen Sie die Schritte aus, die vom Hotfixpaket angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Deinstallieren von Microsoft Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Deinstallieren Sie die Analytics Platform System-Hotfixes &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Software Wartung &#40;Analytics-Platt Form System&#41;](software-servicing.md)  
  
