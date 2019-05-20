---
title: Servereigenschaften (Seite „Allgemein“) | Microsoft-Dokumentation
ms.date: 06/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 71c0d3d28de1a9c63770b37f2bb6013768aaee78
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65576170"
---
# <a name="report-server-properties-general-page"></a>Eigenschaften des Berichtsservers (Seite „Allgemein“)
  Verwenden Sie diese Seite, um den im Berichts-Manager verwendeten Titel anzuzeigen oder zu ändern, um den Ordner Meine Berichte zu aktivieren oder zu deaktivieren, um eine Rollendefinition für die Sicherheit des Ordners Meine Berichte auszuwählen und um das Client-Drucksteuerelement zu aktivieren oder zu deaktivieren.  
  
 **So öffnen Sie diese Seite:**
 1) Start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Stellen Sie eine Verbindung mit einer Berichtsserverinstanz her.
 3) Klicken Sie mit der rechten Maustaste auf den Berichtsservernamen, und wählen Sie die Option **Eigenschaften**aus.  
  
 Der Servermodus bestimmt, welche Servereigenschaften Sie festlegen können. Wenn Sie einen Berichtsserver verwalten, der so konfiguriert ist, dass er im integrierten SharePoint-Modus ausgeführt wird, können Sie „Meine Berichte“ nicht aktivieren und auch den Titel für das Webportal nicht festlegen.  
  
## <a name="options"></a>enthalten  
 **Name**  
 Geben Sie einen Namen ein, der ganz oben im Webportal angezeigt wird. Der Standardwert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Der von Ihnen angegebene Name wird nur im Berichts-Manager angezeigt.  
  
 **Version**  
 Diese Eigenschaft ist schreibgeschützt. Gibt die von Ihnen verwendete Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] an.  
  
 **Edition**  
 Diese Eigenschaft ist schreibgeschützt. Gibt die aktuelle Berichtsserverinstanz an. Der Berichts-Manager ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Editionen und unterstütze Funktionen von SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  
  
 **Authentifizierungsmodus**  
 Diese Eigenschaft ist schreibgeschützt. Sie identifiziert die Typen der von der Berichtsserverinstanz akzeptierten Authentifizierungsanforderungen. Möchten Sie den Authentifizierungsmodus ändern, müssen Sie die Datei **RSReportServer.config** ändern. Weitere Informationen finden Sie unter [Authentication with the Report Server](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 **URL**  
 Diese Eigenschaft ist schreibgeschützt. Sie gibt die URL zum Report Server-Webdienst an. Dieser Wert wird im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool angegeben. Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Für jeden Benutzer den Ordner 'Meine Berichte' aktivieren**  
 Den Ordner **Meine Berichte** für Benutzer verfügbar machen. Diese Option ist nur für Berichtsserver im einheitlichen Modus verfügbar.  
  
 **Wählen Sie die Rolle für jeden Ordner 'Meine Berichte' aus**  
 Geben Sie eine für die Sicherheit des Ordners Meine Berichte zu verwendende Rollendefinition an. Die Rollendefinition identifiziert die Aufgaben, die im jeweiligen Ordner Meine Berichte unterstützt werden.  

  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Aktivieren und Deaktivieren von "Meine Berichte"](../../reporting-services/report-server/enable-and-disable-my-reports.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Sichern von Meine Berichte](../../reporting-services/security/secure-my-reports.md)  
  
  

