---
title: E-Mail-Einstellungen – Konfigurations-Manager (einheitlicher SSRS-Modus) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 96e3318045d058a7d953684fa05bfd72aed9bd69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160595"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>E-Mail-Einstellungen – Konfigurations-Manager (einheitlicher SSRS-Modus)
  Verwenden Sie diese Seite, um die SMTP (Simple Mail Transport Protocol)-Einstellungen anzugeben, mit denen die E-Mail-Übermittlung des Berichtsservers aktiviert wird. Mit der E-Mail-Übermittlungserweiterung des Berichtsservers können Sie Berichte oder Benachrichtigungen über Berichtsverarbeitungen mithilfe von E-Mail-Abonnements verteilen. Für die Berichtsserver-E-Mail-Übermittlungserweiterung sind ein SMTP-Server und eine E-Mail-Adresse erforderlich, die im Feld "Von:" verwendet wird.  
  
 Es können zusätzliche Konfigurationseinstellungen verwendet werden, um die E-Mail-Abonnements weiter anzupassen, einschließlich Einstellungen, welche die Verfügbarkeit von Mailserverhosts und Renderingerweiterungen einschränken. Sie können nicht angeben, dass diese Einstellungen in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Zum Konfigurieren der zusätzlichen Einstellungen müssen Sie die Datei RSReportServer.config manuell bearbeiten. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41; ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bücher Online.  
  
 Um diese Seite zu öffnen, starten Sie den Reporting Services-Konfigurations-Manager, und klicken Sie auf **e-Mail-Einstellungen** im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Tastatur  
 **Adresse des Absenders**  
 Gibt die E-Mail-Adresse an, die im Feld Von: einer generierten E-Mail verwendet werden soll. Sie müssen ein Benutzerkonto angeben, das über die Berechtigung zum Senden von E-Mails vom SMTP-Server verfügt.  
  
 **Aktuelle SMTP-Übermittlungsmethode**  
 Gibt an, ob die Berichtsserver-E-Mail über einen SMTP-Server geleitet wird. Dies ist die einzige Übermittlungsmethode, die Sie im Reporting Services-Konfigurations-Manager angeben können.  
  
 Eine andere Übermittlungsmethode soll ein lokales Abholverzeichnis eines SMTP-Dienstes verwenden. Sie können diese Übermittlungsmethode verwenden, wenn kein SMTP-Netzwerkdienst zur Verfügung steht. Um ein lokales Abholverzeichnis für den SMTP-Dienst anzugeben, müssen Sie die RSReportServer.config-Datei bearbeiten. Das Bearbeiten der Konfigurationsdatei, um einen lokalen SMTP-Dienst pickup-Verzeichnis verwendet der Konfigurations-Manager für Reporting Services legt die **Übermittlungsmethode** option *benutzerdefinierte* gibt an, dass die Übermittlung -Methode wird in der Konfigurationsdatei angegeben.  
  
 In der Konfigurationsdatei die Übermittlungsmethode festgelegt ist, über die `SendUsing` -Konfigurationseinstellung. Weitere Informationen zum Angeben der `SendUsing` finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **SMTP-Server**  
 Geben Sie den zu verwendenden SMTP-Server oder -Gateway an. Sie können einen lokalen Server oder einen SMTP-Server in Ihrem Netzwerk verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Reporting Services-Konfigurationsmanager-F1-Hilfethemen &#40;SSRS im einheitlichen Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  