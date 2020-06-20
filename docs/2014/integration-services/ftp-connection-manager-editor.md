---
title: FTP-Verbindungs-Manager-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 20d50565b9687f18af95e820be90d16ab643de28
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966360"
---
# <a name="ftp-connection-manager-editor"></a>FTP-Verbindungs-Manager-Editor
  Mithilfe des Dialogfelds **FTP-Verbindungs-Manager-Editor** können Sie Eigenschaften für Verbindungen mit einem FTP-Server angeben.  
  
> [!IMPORTANT]  
>  Der FTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Standardauthentifizierung. Er unterstützt keine Windows-Authentifizierung.  
  
 Weitere Informationen zum FTP-Verbindungs-Manager finden Sie unter [FTP Connection Manager](connection-manager/ftp-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Servername**  
 Geben Sie den Namen des FTP-Servers an.  
  
 **Serverport**  
 Geben Sie die Portnummer des FTP-Servers an, der für die Verbindung verwendet werden soll. Der Standardwert dieser Eigenschaft ist **21**.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für den Zugriff auf den FTP-Server an. Der Standardwert dieser Eigenschaft ist **anonymous**.  
  
 **Kennwort**  
 Geben Sie das Kennwort für den Zugriff auf den FTP-Server an.  
  
 **Timeout (in Sekunden)**  
 Geben Sie die Anzahl von Sekunden an, die der Task vor einem Timeout dauert. Der Wert **0** gibt einen unbegrenzten Zeitraum an. Der Standardwert dieser Eigenschaft ist **60**.  
  
 **Passivmodus verwenden**  
 Geben Sie an, ob die Verbindung durch den Server oder durch den Client initiiert wird. Die Initiierung der Verbindung durch den Server erfolgt im Aktivmodus; der Client aktiviert die Verbindung im Passivmodus. Der Standardwert dieser Eigenschaft ist der **Aktivmodus**.  
  
 **Wiederholungsversuche**  
 Geben Sie die Häufigkeit an, mit der der Task versucht, eine Verbindung herzustellen. Der Wert **0** gibt eine unbegrenzte Anzahl von Versuchen an.  
  
 **Segmentgröße (in KB)**  
 Geben Sie eine Segmentgröße in KB für das Übertragen von Daten an.  
  
 **Testen der Verbindung**  
 Nachdem die Konfiguration des FTP-Verbindungs-Managers abgeschlossen ist, bestätigen Sie die Gültigkeit der Verbindung, indem Sie auf **Verbindung testen**klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
