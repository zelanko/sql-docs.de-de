---
title: FTP-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: caeba8ad0baa8104a3d56a3e8b4f95cb0d4f563f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438477"
---
# <a name="ftp-connection-manager"></a>FTP-Verbindungs-Manager
  Mit einem FTP-Verbindungs-Manager kann ein Paket eine Verbindung mit einem FTP-Server (File Transfer Protocol) herstellen. Der FTP-Task von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet diesen Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen FTP-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit als FTP-Verbindung aufgelöst werden kann, die Eigenschaften des Verbindungs-Managers festlegt und der `Connections`-Auflistung im Paket den Verbindungs-Manager hinzufügt.  
  
 Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `FTP` festgelegt.  
  
 Es gibt folgende Möglichkeiten, um den FTP-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie einen Servernamen und einen Serverport an.  
  
-   Geben Sie den anonymen Zugriff an, oder stellen Sie einen Benutzernamen und ein Kennwort für die Standardauthentifizierung bereit.  
  
    > [!IMPORTANT]  
    >  Der FTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Standardauthentifizierung. Er unterstützt keine Windows-Authentifizierung.  
  
-   Legen Sie das Timeout, die Wiederholungsversuche und die jeweils zu kopierende Datenmenge fest.  
  
-   Geben Sie an, ob der FTP-Verbindungs-Manager den passiven oder aktiven Modus verwendet.  
  
 Sie müssen u. U. die folgenden Standardwerte des Verbindungs-Managers ändern, je nach Konfiguration der FTP-Site, zu der der FTP-Verbindungs-Manager eine Verbindung herstellt:  
  
-   Der Serverport wird auf 21 festgelegt. Sie sollten den Port angeben, an dem von der FTP-Site gelauscht wird.  
  
-   Der Benutzername ist auf "anonym" festgelegt. Sie sollten die für die FTP-Site erforderlichen Anmeldeinformationen bereitstellen.  
  
## <a name="activepassive-modes"></a>Aktiver/passiver Modus  
 Ein FTP-Verbindungs-Manager kann Dateien mithilfe des aktiven oder passiven Modus senden und empfangen. Im aktiven Modus wird die Datenverbindung vom Server initiiert, im passiven Modus wird sie vom Client initiiert.  
  
## <a name="configuration-of-the-ftp-connection-manager"></a>Konfiguration des FTP-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [FTP-Verbindungs-Manager-Editor](../ftp-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [FTP-Task](../control-flow/ftp-task.md)   
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](integration-services-ssis-connections.md)  
  
  
