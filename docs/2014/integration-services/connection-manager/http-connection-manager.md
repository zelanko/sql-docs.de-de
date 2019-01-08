---
title: HTTP-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5d41fab7e891fd8393600224902ee36e2f6dad20
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764062"
---
# <a name="http-connection-manager"></a>HTTP-Verbindungs-Manager
  Eine HTTP-Verbindung ermöglicht Paketen den Zugriff auf einen Webserver, indem zum Senden und Empfangen von Dateien HTTP verwendet wird. Der Task Webdienst von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet diesen Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen HTTP-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine HTTP-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der `Connections`-Auflistung im Paket den Verbindungs-Manager hinzufügt.  
  
 Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist festgelegt auf `HTTP.`  
  
 Es gibt folgende Möglichkeiten, um den HTTP-Verbindungs-Manager zu konfigurieren:  
  
-   Verwenden Sie Anmeldeinformationen. Falls der Verbindungs-Manager Anmeldeinformationen verwendet, enthalten die Eigenschaften den Benutzernamen, ein Kennwort und eine Domäne.  
  
    > [!IMPORTANT]  
    >  Der HTTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Standardauthentifizierung. Er unterstützt keine Windows-Authentifizierung.  
  
-   Verwenden Sie ein Clientzertifikat. Falls der Verbindungs-Manager ein Clientzertifikat verwendet, enthalten die Eigenschaften den Zertifikatnamen.  
  
-   Stellen Sie ein Timeout für Verbindungen mit dem Server und eine Segmentgröße zum Schreiben von Daten bereit.  
  
-   Verwenden Sie einen Proxyserver. Für den Proxyserver können Sie auch konfigurieren, dass Anmeldeinformationen verwendet werden und der Proxyserver umgangen wird und stattdessen lokale Adressen verwendet werden.  
  
## <a name="configuration-of-the-http-connection-manager"></a>Konfiguration des HTTP-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [HTTP-Verbindungs-Manager-Editor &#40;Seite „Server“&#41;](../http-connection-manager-editor-server-page.md)  
  
-   [HTTP-Verbindungs-Manager-Editor &#40;Seite „Proxy“&#41;](../http-connection-manager-editor-proxy-page.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.  
  
## <a name="see-also"></a>Siehe auch  
 [Webdienst (Task)](../control-flow/web-service-task.md)   
 [Integration Services-Verbindungen &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
