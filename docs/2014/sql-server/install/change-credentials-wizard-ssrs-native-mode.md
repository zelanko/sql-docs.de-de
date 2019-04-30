---
title: Ändern Sie die Assistenten der Anmeldeinformationen (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 632cfe6f1ea61612f59225f38a665ef73da0d898
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63215122"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Anmeldeinformationen (einheitlicher SSRS-Modus)
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager stellt einen Assistenten zum Ändern der Anmeldeinformationen bereit, der Sie durch alle Schritte der Neukonfiguration des Kontos führt, anhand dessen der Berichtsserver die Verbindung mit der Berichtsserverdatenbank herstellt. Wenn Sie die Anmeldeinformationen ändern, aktualisiert der Konfigurations-Manager alle Berechtigungen und Datenbank-Anmeldedaten auf dem Datenbankserver für die Berichtsserver-Datenbank, die vom Berichtsserver verwendet wird.  
  
 Um den Assistenten zu starten, klicken Sie auf der Datenbankseite im **-Konfigurationsmanager auf** Anmeldeinformationen ändern [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Anweisungen zum Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Optionen  
 **Datenbank-Server**  
 Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz an, auf der die Berichtsserver-Datenbank ausgeführt wird.  
  
 Um eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz herzustellen, müssen Sie Anmeldeinformationen verwenden, die zum Anmelden auf dem Server und zum Aktualisieren der Datenbankdaten berechtigen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, wenn Sie jedoch über keine Anmelde- oder Datenbankberechtigung verfügen, können Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung angeben.  
  
 Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn Sie eine Verbindung als anderer Windows-Benutzer herstellen möchten, melden Sie sich als dieser Benutzer an, und starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültige Werte sind u. a. das Dienstkonto des Report Server-Webdiensts, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung, die in der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz definiert ist, auf der Sie den Berichtsserver hosten, oder ein Windows-Konto. Wenn Sie ein Windows-Konto verwenden, können Sie angeben, dass ein lokales Konto (*\<Computername >\\< Benutzername\>*), wenn der Berichtsserver und die Datenbank auf demselben Computer oder Benutzer einer Domäne sind Konto (*\<Domäne >\\< Benutzername\>*) Wenn sie sich auf verschiedenen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer sich in einer anderen oder nicht vertrauenswürdigen Domäne befindet, sollten Sie überlegen, besser eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung zu verwenden. Weitere Informationen zum Auswählen eines Kontos finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Sie den Assistenten starten.  
  
 **Fortsetzen und Fertigstellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Datenbank-Assistent zum Ändern der &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
