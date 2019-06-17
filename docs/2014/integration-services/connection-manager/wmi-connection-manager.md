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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5d57a0783c8af0121169f09622b8e5bd8547d1ad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62833085"
---
# <a name="wmi-connection-manager"></a>WMI-Verbindungs-Manager
  Mit einem WMI-Verbindungs-Manager kann ein Paket mithilfe der Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) Informationen in einer Unternehmensumgebung verwalten. Der Task Webdienst von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet einen WMI-Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen WMI-Verbindungs-Manager hinzufügen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, die in einer WMI-Verbindung zur Laufzeit aufgelöst wird, die Verbindungs-Manager-Eigenschaften festlegt und fügt den Verbindungs-Manager erstellt die `Connections` -Sammlung im Paket . Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `WMI` festgelegt.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Konfiguration des WMI-Verbindungs-Managers  
 Es gibt folgende Möglichkeiten, um einen WMI-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie den Namen eines Servers an.  
  
-   Geben Sie einen Namespace auf dem Server an.  
  
-   Wählen Sie den Authentifizierungsmodus zum Herstellen einer Verbindung mit dem Server aus.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [WMI-Verbindungs-Manager-Editor](../wmi-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [Webdienst (Task)](../control-flow/web-service-task.md)   
 [Integration Services-Verbindungen &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
