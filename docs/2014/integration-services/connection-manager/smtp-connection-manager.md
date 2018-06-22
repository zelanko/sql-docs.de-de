---
title: SMTP-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a00a8295904d8fdc5a1ad87c6ac60dbf70ce6fa9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060088"
---
# <a name="smtp-connection-manager"></a>SMTP-Verbindungs-Manager
  Mit einem SMTP-Verbindungs-Manager kann ein Paket eine Verbindung mit einem SMTP-Server (Simple Mail Transfer Protocol) herstellen. Der Task Mail senden von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet einen SMTP-Verbindungs-Manager.  
  
 Wenn Sie Microsoft Exchange als SMTP-Server verwenden, müssen Sie den SMTP-Verbindungs-Manager u. U. für die Verwendung der Windows-Authentifizierung konfigurieren. Exchange-Server können so konfiguriert werden, dass keine nicht authentifizierten SMTP-Verbindungen zugelassen werden.  
  
## <a name="configuration-the-smtp-connection-manager"></a>Konfiguration des SMTP-Verbindungs-Managers  
 Wenn Sie einen SMTP-Verbindungs-Manager einem Paket hinzufügen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt einen Verbindungs-Manager, der in eine SMTP-Verbindung zur Laufzeit aufgelöst wird, die Verbindungs-Manager-Eigenschaften festlegt und fügt den Verbindungs-Manager die `Connections` -Auflistung in der das Paket. Die `ConnectionManagerType` des Verbindungs-Managers ist-Eigenschaftensatz auf `SMTP`.  
  
 Es gibt folgende Möglichkeiten, um einen SMTP-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie eine Verbindungszeichenfolge an.  
  
-   Geben Sie den Namen eines SMTP-Servers an.  
  
-   Geben Sie die zu verwendende Authentifizierungsmethode an.  
  
    > [!IMPORTANT]  
    >  Der SMTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Windows-Authentifizierung. Er unterstützt keine Standardauthentifizierung.  
  
-   Geben Sie an, ob beim Senden von E-Mail-Nachrichten SSL (Secure Sockets Layer) zur Verschlüsselung der Kommunikation verwendet werden soll.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [SMTP-Verbindungs-Manager-Editor](../smtp-connection-manager-editor.md).  
  
 Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Verbindungen programmgesteuert hinzufügen](../building-packages-programmatically/adding-connections-programmatically.md).  
  
  