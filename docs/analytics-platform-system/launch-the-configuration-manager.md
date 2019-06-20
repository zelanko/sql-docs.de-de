---
title: Starten der Konfigurations-Manager - Analytics Platform System | Microsoft-Dokumentation
description: Anweisungen zum Starten des Konfigurations-Manager-Tools für die Analytics Platform System Appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 087360981a7c31de6980755cfee4f98f88f48a15
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63183415"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Starten Sie den Konfigurations-Manager in Analytics Platform System
Dieses Thema enthält Anweisungen zum Starten der **Configuration Manager** für die Analytics Platform System Appliance.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Das Analytics Platform System**Configuration Manager** kann nur vom Domänenadministrator Appliance ausgeführt werden. Um dieses Tool ausführen zu können, benötigen Sie das Kennwort für den Domänenadministrator Appliance an. Um zusätzliche APS-Administratoren zu erstellen, finden Sie unter [erstellen Sie einen Domänenadministrator APS &#40;APS&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Starten des Konfigurations-Manager  
Um den Konfigurations-Manager auszuführen, verwenden Sie Remotedesktop für die Verbindung mit dem Steuerungsknoten mit PDW ( **_PDW_region_-CTL01**) Knoten, und melden Sie sich als _Appliance_domain_ **\Administrator**. Beim Starten der **Configuration Manager** programmieren, verwenden Sie die **als Administrator ausführen** Option, um sicherzustellen, dass Ihre Administratoranmeldeinformationen verwendet werden.  
  
#### <a name="to-launch-from-a-browser-window"></a>Starten Sie in einem Browserfenster öffnen  
  
1.  Öffnen Sie einen Browser, und navigieren Sie zu dem Verzeichnis `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
2.  Mit der rechten Maustaste `dwconfig.exe` , und klicken Sie dann auf **als Administrator ausführen**.  
  
#### <a name="to-launch-from-a-command-prompt"></a>Um an einer Eingabeaufforderung zu starten.  
  
1.  Öffnen Sie auf dem Desktop die **starten** Menü klicken Sie auf **Programme**, klicken Sie auf **Zubehör**, mit der rechten Maustaste **Eingabeaufforderung** , und klicken Sie dann auf  **Als Administrator ausführen**.  
  
2.  Geben Sie an der Eingabeaufforderung den folgenden Befehl aus, um Verzeichnisse zu ändern: `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`.  
  
3.  Geben Sie an der Eingabeaufforderung den Befehl `dwconfig.exe`.  
  
Nach der **Configuration Manager** wird gestartet, sehen Sie alle verfügbaren Funktionen, die im linken Bereich aufgeführt. Der übrige Teil dieses Abschnitts wird erläutert, wie jede Aktion in das Tool ausgeführt.  
  
Schließen und beenden Sie **Configuration Manager**, klicken Sie auf **beenden** in der unteren rechten Ecke von einem beliebigen Bildschirm.  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>Siehe auch  
[Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
