---
title: Durchführen eines Upgrades für Integration Services-Pakete mit dem SSIS-Paketupgrade-Assistenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e44b755748dcbda6af30e0570b667f9ba3ee75a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62767887"
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a>Aktualisieren von Integration Services-Paketen mit dem SSIS-Paketupgrade-Assistenten
  Sie können Pakete, die in früheren Versionen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt wurden, auf das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Format aktualisieren, das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt zu diesem Zweck den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketupgrade-Assistenten bereit. Da Sie den Assistenten so konfigurieren können, dass er die ursprünglichen Pakete sichert, können Sie die ursprünglichen Pakete weiter verwenden, falls Probleme beim Upgrade auftreten.  
  
 Der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketupgrade-Assistent ist installiert, wenn [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installiert ist.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketaktualisierungs-Assistent ist in den Editionen Standard, Enterprise und Developer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar.  
  
 Weitere Informationen zum Aktualisieren von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen finden Sie unter [Aktualisieren von Integration Services-Paketen](upgrade-integration-services-packages.md).  
  
 Im weiteren Verlauf dieses Themas wird beschrieben, wie Sie den Assistenten ausführen und die ursprünglichen Pakete sichern.  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a>Ausführen des SSIS Paketupgrade-Assistenten  
 Sie können den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketupgrade-Assistenten in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]oder an der Eingabeaufforderung ausführen.  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a>So führen Sie den Assistenten in SQL Server-Datentools aus  
  
1.  Erstellen oder öffnen Sie ein [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]-Projekt in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **SSIS-Pakete** , und klicken Sie dann auf **Alle Pakete aktualisieren** , um alle Pakete unter diesem Knoten zu aktualisieren.  
  
    > [!NOTE]  
    >  Wenn Sie ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket öffnen, das [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]- oder [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]-Pakete enthält, öffnet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] automatisch den [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Paketaktualisierungs-Assistenten.  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a>So führen Sie den Assistenten in SQL Server Management Studio aus  
  
-   Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]her, erweitern Sie den Knoten **Gespeicherte Pakete** , klicken Sie mit der rechten Maustaste auf den Knoten **Dateisystem** oder **MSDB** , und klicken Sie dann auf **Pakete aktualisieren**.  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a>So führen Sie den Assistenten an der Eingabeaufforderung aus  
  
-   Führen Sie an der Eingabeaufforderung die Datei SSISUpgrade.exe aus dem **C:\Program Files\Microsoft SQL Server\120\DTS\Binn** Ordner.  
  
## <a name="backing-up-the-original-packages"></a>Sichern der ursprünglichen Pakete  
 Um die ursprünglichen Pakete zu sichern, müssen sowohl die ursprünglichen Pakete als auch die aktualisierten Pakete in demselben Ordner im Dateisystem gespeichert sein. Abhängig davon, wie Sie den Assistenten ausführen, kann dieser Speicherort automatisch ausgewählt werden.  
  
-   Wenn Sie den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketaktualisierungs-Assistenten in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ausführen, speichert der Assistent automatisch sowohl die ursprünglichen Pakete als auch die aktualisierten Pakete in demselben Ordner im Dateisystem.  
  
-   Wenn Sie den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketaktualisierungs-Assistenten in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder an der Eingabeaufforderung ausführen, können Sie unterschiedliche Speicherorte für die ursprünglichen und die aktualisierten Pakete angeben. Um die ursprünglichen Pakete zu sichern, geben Sie unbedingt an, dass sowohl die ursprünglichen als auch die aktualisierten Pakete in demselben Ordner im Dateisystem gespeichert werden. Wenn Sie andere Speicheroptionen angeben, ist der Assistent nicht in der Lage, die ursprünglichen Pakete zu sichern.  
  
 Wenn der Assistent die ursprünglichen Pakete sichert, speichert er eine Kopie der ursprünglichen Pakete in einem **SSISBackupFolder** -Ordner. Der Assistent erstellt diesen **SSISBackupFolder** -Ordner als Unterordner des Ordners, der die ursprünglichen Pakete und die aktualisierten Pakete enthält.  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a>So sichern Sie die ursprünglichen Pakete in SQL Server Management Studio oder an der Eingabeaufforderung  
  
1.  Speichern Sie die ursprünglichen Pakete an einem Speicherort im Dateisystem.  
  
    > [!NOTE]  
    >  Die Sicherungsoption im Assistenten funktioniert nur mit Paketen, die im Dateisystem gespeichert worden sind.  
  
2.  Führen Sie den [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Paketupgrade-Assistenten in [!INCLUDE[ssIS](../../includes/ssis-md.md)] oder an der Eingabeaufforderung aus.  
  
3.  Legen Sie auf der Seite **Quellspeicherort auswählen** des Assistenten die Eigenschaft **Paketquelle** auf **Dateisystem**fest.  
  
4.  Wählen Sie auf der Seite **Zielspeicherort auswählen** die Option **An Quellspeicherort speichern** aus, um die aktualisierten Pakete an demselben Speicherort wie die ursprünglichen Pakete zu speichern.  
  
    > [!NOTE]  
    >  Die Sicherungsoption im Assistenten ist nur verfügbar, wenn die aktualisierten Pakete in demselben Ordner gespeichert werden wie die ursprünglichen Pakete.  
  
5.  Wählen Sie auf der Seite **Paketverwaltungsoptionen auswählen** des Assistenten die Option **Originalpakete sichern** aus.  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a>So sichern Sie die Originalpakete in SQL Server-Datentools  
  
1.  Speichern Sie die ursprünglichen Pakete an einem Speicherort im Dateisystem.  
  
2.  Wählen Sie auf der Seite **Paketverwaltungsoptionen auswählen** des Assistenten die Option **Originalpakete sichern** aus.  
  
    > [!WARNING]  
    >  Die **Originalpakete Sichern** Option wird nicht angezeigt, wenn Sie öffnen ein [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] oder [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] Projekt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], der der Assistent automatisch gestartet wird.  
  
3.  Führen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketaktualisierungs-Assistenten aus.  
  
  
