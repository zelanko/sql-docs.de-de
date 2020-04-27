---
title: SMTP-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 948a7411c39191635245fdf0f6777538b1ef57fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62833088"
---
# <a name="smtp-connection-manager"></a>SMTP-Verbindungs-Manager
  Mit einem SMTP-Verbindungs-Manager kann ein Paket eine Verbindung mit einem SMTP-Server (Simple Mail Transfer Protocol) herstellen. Der Task „Mail senden“ von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet einen SMTP-Verbindungs-Manager.  
  
 Wenn Sie Microsoft Exchange als SMTP-Server verwenden, müssen Sie den SMTP-Verbindungs-Manager u. U. für die Verwendung der Windows-Authentifizierung konfigurieren. Exchange-Server können so konfiguriert werden, dass keine nicht authentifizierten SMTP-Verbindungen zugelassen werden.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Konfiguration des SMTP-Verbindungs-Managers  
 Wenn Sie einem Paket einen SMTP-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine SMTP-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der `Connections`-Auflistung im Paket den Verbindungs-Manager hinzufügt. Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `SMTP` festgelegt.  
  
 Es gibt folgende Möglichkeiten, um einen SMTP-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie eine Verbindungszeichenfolge an.  
  
-   Geben Sie den Namen eines SMTP-Servers an.  
  
-   Geben Sie die zu verwendende Authentifizierungsmethode an.  
  
    > [!IMPORTANT]  
    >  Der SMTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Windows-Authentifizierung. Er unterstützt keine Standardauthentifizierung.  
  
-   Geben Sie an, ob beim Senden von E-Mail-Nachrichten SSL (Secure Sockets Layer) zur Verschlüsselung der Kommunikation verwendet werden soll.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [SMTP-Verbindungs-Manager-Editor](../smtp-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
  
