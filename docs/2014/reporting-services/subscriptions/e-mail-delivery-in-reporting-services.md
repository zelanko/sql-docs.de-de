---
title: E-Mail-Übermittlung in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], e-mail
- e-mail [Reporting Services]
- mail [Reporting Services]
ms.assetid: fda2f130-97b9-4258-9dbb-e93a70f4d08a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 68024e36dd5f8188097ebcc673056c1b6d11e59b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66100887"
---
# <a name="e-mail-delivery-in-reporting-services"></a>E-Mail-Übermittlung in Reporting Services
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält eine E-Mail-Übermittlungserweiterung, mit der Sie einen Bericht per E-Mail an einzelne Benutzer oder Gruppen senden können. Die E-Mail-Übermittlungserweiterung wird mit dem Reporting Services-Konfigurations-Manager und durch Bearbeiten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationsdateien konfiguriert.  
  
 Um einen Bericht per E-Mail zu verteilen oder zu empfangen, definieren Sie entweder ein Standardabonnement oder ein datengesteuertes Abonnement. Es kann jeweils immer nur ein Bericht abonniert und verteilt werden. Es ist nicht möglich, ein Abonnement zu erstellen, das mehrere Berichte in einer einzigen E-Mail-Nachricht übermittelt. Weitere Informationen zu Abonnements finden Sie unter [erstellen, ändern und Löschen von Standardabonnements &#40;Reporting Services im einheitlichen Modus&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus &#124; SharePoint 2010 und SharePoint 2013<br /><br /> **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus|  
  
## <a name="e-mail-delivery-options"></a>Optionen für die E-Mail-Übermittlung  
 Die Berichtsserver-E-Mail-Übermittlung kann Berichte wie folgt übermitteln:  
  
-   Senden einer Benachrichtigung und eines Links zu dem generierten Bericht.  
  
-   Senden einer Benachrichtigung in der Betreffzeile einer E-Mail-Nachricht. Standardmäßig enthält die Betreffzeile in der Abonnementdefinition die folgenden Variablen, die bei der Verarbeitung des Abonnements durch berichtsspezifische Informationen ersetzt werden:  
  
     **@ReportName** gibt den Namen des Berichts an.  
  
     **@ExecutionTime** gibt an, wann der Bericht ausgeführt wurde.  
  
     Diese Variablen können Sie mit statischem Text kombinieren, und den Text in der Betreffzeile können Sie für jedes Abonnement ändern.  
  
-   Senden eines eingebetteten oder angefügten Berichts. Durch das Renderingformat und den Browser wird festgelegt, ob der Bericht eingebettet oder angefügt wird.  
  
     Falls Ihr Browser HTML 4.0 und MHTML unterstützt und Sie das Webarchiv-Renderingformat auswählen, wird der Bericht in die Nachricht eingebettet. Bei allen anderen Renderingformaten (CSV, PDF usw.) werden Berichte als Anlagen übermittelt. Diese Funktion können Sie in der Konfigurationsdatei RSReportServer deaktivieren.  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] führt keine Überprüfung der Größe der Anlage oder Nachricht vor dem Senden des Berichts durch. Überschreitet die Anlage oder Nachricht den von Ihrem Mailserver zugelassenen Höchstwert, wird der Bericht nicht übermittelt. Wählen Sie bei großen Berichten eine andere Übermittlungsoption aus (z.B. URL oder Benachrichtigung).  
  
 Die Übermittlungsoptionen, die bestimmen, wie ein Bericht übermittelt wird, werden beim Erstellen des Abonnements festgelegt. Wenn Sie im Abonnement z.B. **Link einschließen** auswählen, enthält die E-Mail-Nachricht einen Link zum Bericht.  
  
## <a name="role-based-e-mail-settings"></a>Rollenbasierte E-Mail-Einstellungen  
 Wenn Sie einen Bericht abonnieren, stehen je nachdem, ob Ihre Rolle die Aufgabe "Einzelne Abonnements verwalten" oder "Alle Abonnements verwalten" enthält, unterschiedliche E-Mail-Übermittlungseinstellungen zur Verfügung.  
  
|Aufgabe|Verfügbare Einstellungen|  
|----------|------------------------|  
|Einzelne Abonnements verwalten|Zeigt Felder an, mit denen ein Benutzer einen Bericht automatisieren und an sich übermitteln kann. In diesem Modus sind keine Felder vorhanden, die E-Mail-Aliasnamen akzeptieren.|  
|Alle Abonnements verwalten|Zeigt Felder an, die eine breiter angelegte Verteilung unterstützen, einschließlich der Felder An, Cc, Bcc und Antwort an. Auf diese Weise stehen zusätzliche Möglichkeiten zur Verfügung, um einen Bericht an mehrere Abonnenten weiterzuleiten. Die Verfügbarkeit von E-Mail-Aliasfeldern wird durch Einstellungen in der Konfigurationsdatei RSReportServer definiert.|  
  
## <a name="specifying-e-mail-addresses-in-a-subscription"></a>Angeben von E-Mail-Adressen in einem Abonnement  
 Wenn Sie Berichte innerhalb eines Intranets übermitteln und ein SMTP-Gateway zu einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange-Server verwenden, geben Sie den E-Mail-Alias ein (so als ob Sie eine E-Mail an einen Mitarbeiter senden würden). Bei der Übermittlung an ein externes E-Mail-Konto geben Sie die vollständige E-Mail-Adresse ein. Falls Sie zusätzliche E-Mail-Adressen angeben, um Ihrem Abonnement weitere Benutzer hinzuzufügen, erhalten die Abonnenten eine exakte Kopie des Berichts, der anhand dieses Abonnements erstellt wird.  
  
 Der Berichtsserver führt keine Überprüfung von E-Mail-Adressen durch und ruft keine E-Mail-Adressen von einem E-Mail-Server ab. Sie müssen die E-Mail-Adressen bereits kennen, die Sie verwenden möchten. Standardmäßig können Sie Berichte per E-Mail an jedes gültige E-Mail-Konto innerhalb oder außerhalb Ihrer Organisation senden. Mithilfe von Konfigurationseinstellungen kann allerdings die E-Mail-Übermittlung auf namentlich angegebene Hosts des Mailservers beschränkt werden. Sie können zusätzliche Hosts angeben, um die E-Mail-Übermittlung an Personen zu ermöglichen, die nicht zu Ihrer Organisation gehören.  
  
 Die E-Mail-Nachricht, mit der der Bericht übermittelt wird, muss von einem auf dem E-Mail-Server definierten E-Mail-Konto gesendet werden. Das E-Mail-Konto wird durch eine Konfigurationseinstellung angegeben. Das E-Mail-Konto wird für alle Berichte verwendet, die von der E-Mail-Übermittlungserweiterung gesendet werden. Es ist nicht möglich, mehrere Konten anzugeben oder für jeden Bericht ein anderes Konto zu verwenden.  
  
## <a name="e-mail-server-configuration"></a>E-Mail-Server-Konfiguration  
 Der Berichtsserver stellt über eine Standardverbindung eine Verbindung mit einem E-Mail-Server her. Mit Secure Sockets Layer (SSL) verschlüsselte Kommunikation wird nicht verwendet. Der E-Mail-Server muss ein Remoteserver oder lokaler SMTP-Server (Simple Mail Transport Protocol) im selben Netzwerk wie der Berichtsserver sein.  
  
 Informationen zum Konfigurieren eines Berichtsservers im einheitlichen Modus finden Sie im folgenden Thema:  
  
-   [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
-   [E-Mail-Einstellungen – Konfigurations-Manager &#40;einheitlicher SSRS-Modus&#41;](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)  
  
 Informationen zum Konfigurieren eines Berichtsservers im SharePoint-Modus finden Sie im folgenden Thema:  
  
-   [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2010 und SharePoint 2013&#41;](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Datengesteuerte Abonnements](data-driven-subscriptions.md)   
 [Rollenzuweisungen](../security/role-assignments.md)  
  
  
