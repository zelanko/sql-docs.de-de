---
title: SMTP-Verbindungs-Manager-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 527c8f647c963c2c1c03171eeb154a790ab1994a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055562"
---
# <a name="smtp-connection-manager-editor"></a>SMTP-Verbindungs-Manager-Editor
  Mithilfe des Dialogfelds **SMTP-Verbindungs-Manager-Editor** können Sie einen SMTP-Server (Simple Mail Transfer Protocol) angeben.  
  
 Weitere Informationen zum SMTP-Verbindungs-Manager finden Sie unter [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Verbindungs-Manager an.  
  
 **Beschreibung**  
 Beschreiben Sie den Verbindungs-Manager. Die bewährte Methode ist hierbei, den Verbindungs-Manager zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **SMTP-Server**  
 Geben Sie den Namen des SMTP-Servers an.  
  
 **Windows-Authentifizierung verwenden**  
 Wählen Sie diese Option aus, um E-Mail über einen SMTP-Server zu senden, der zum Authentifizieren des Zugriffs auf den Server die Windows-Authentifizierung verwendet.  
  
> [!IMPORTANT]  
>  Der SMTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Windows-Authentifizierung. Er unterstützt keine Standardauthentifizierung.  
  
> [!NOTE]  
>  Wenn Sie Microsoft Exchange als SMTP-Server verwenden, müssen Sie möglicherweise die **Windows-Authentifizierung verwenden** auf `True`festlegen. Exchange-Server können so konfiguriert sein, dass keine nicht authentifizierten SMTP-Verbindungen zugelassen sind.  
  
 **Secure Sockets Layer (SSL) aktivieren**  
 Wählen Sie diese Option aus, um beim Senden von E-Mail-Nachrichten die Kommunikation mit SSL (Secure Sockets Layer) zu verschlüsseln.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
