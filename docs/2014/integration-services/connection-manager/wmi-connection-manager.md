---
title: WMI-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 066af3d35f964040b09d8afd217017925a163eff
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438307"
---
# <a name="wmi-connection-manager"></a>WMI-Verbindungs-Manager
  Mit einem WMI-Verbindungs-Manager kann ein Paket mithilfe der Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) Informationen in einer Unternehmensumgebung verwalten. Der Task „Webdienst“ von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet einen WMI-Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen WMI-Verbindungs-Manager hinzufügen, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt einen Verbindungs-Manager, der zur Laufzeit in eine WMI-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der-Auflistung im Paket den Verbindungs-Manager hinzufügt `Connections` . Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `WMI` festgelegt.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Konfiguration des WMI-Verbindungs-Managers  
 Es gibt folgende Möglichkeiten, um einen WMI-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie den Namen eines Servers an.  
  
-   Geben Sie einen Namespace auf dem Server an.  
  
-   Wählen Sie den Authentifizierungsmodus zum Herstellen einer Verbindung mit dem Server aus.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [WMI-Verbindungs-Manager-Editor](../wmi-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Webdienst (Task)](../control-flow/web-service-task.md)   
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](integration-services-ssis-connections.md)  
  
  
