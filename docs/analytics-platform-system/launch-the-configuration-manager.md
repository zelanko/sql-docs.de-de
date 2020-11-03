---
title: Start Configuration Manager
description: Anweisungen zum Starten des Configuration Manager Tools für die Analytics Platform System Appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: be69331ec9f9daa091035d6ef21142c4f40d6a84
ms.sourcegitcommit: 442fbe1655d629ecef273b02fae1beb2455a762e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235167"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Starten Sie den Configuration Manager in Analytics Platform System.
Dieses Thema enthält Anweisungen zum Starten des **Configuration Manager** für die Analytics Platform System Appliance.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Voraussetzungen  
Die **Configuration Manager** des Analytics-plattformsystems kann nur vom Anwendungs Domänen Administrator ausgeführt werden. Zum Ausführen dieses Tools benötigen Sie das Kennwort für den Anwendungs Domänen Administrator. Weitere Informationen zum Erstellen zusätzlicher APS-Administratoren finden Sie unter [Erstellen eines APS-Domänen Administrators &#40;APS&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="launch-the-configuration-manager-tool"></a><a name="Accessing"></a>Starten Sie das Configuration Manager Tool.  
Zum Ausführen des Configuration Manager verwenden Sie Remotedesktop, um eine Verbindung mit dem Knoten PDW-Steuerungs Knoten ( **_PDW_region_ -CTL01** ) herzustellen, und melden Sie sich als _appliance_domain_**\administrator** an. Wenn Sie das **Configuration Manager** Programm starten, verwenden Sie die Option **als Administrator ausführen** , um sicherzustellen, dass Ihre Administrator Anmelde Informationen verwendet werden.  
  
#### <a name="to-launch-from-a-browser-window"></a>So starten Sie in einem Browserfenster  
  
1.  Öffnen Sie einen Browser, und navigieren Sie zum Verzeichnis `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
2.  Klicken Sie mit der rechten Maustaste `dwconfig.exe` und dann auf **als Administrator ausführen** .  
  
#### <a name="to-launch-from-a-command-prompt"></a>So starten Sie über eine Eingabeaufforderung  
  
1.  Öffnen Sie auf dem Desktop das **Startmenü,** klicken Sie auf **Programme** und **Zubehör** , klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung** , und klicken Sie dann auf **als Administrator ausführen** .  
  
2.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Verzeichnisse zu ändern: `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"` .  
  
3.  Geben Sie an der Eingabeaufforderung `dwconfig.exe` ein.  
  
Nachdem der **Configuration Manager** gestartet wurde, werden alle verfügbaren Funktionen im linken Bereich angezeigt. Im restlichen Teil dieses Abschnitts wird erläutert, wie jede im Tool verfügbare Aktion ausgeführt wird.  
  
Um **Configuration Manager** zu schließen und zu beenden, klicken Sie in der rechten unteren Ecke eines beliebigen Bildschirms auf **Beenden** .  
  
![Screenshot des Dialog Felds "Microsoft Analytics Platform System Configuration Manager" mit der Geräte Topologie.](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>Weitere Informationen  
[Überwachen Sie die Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
