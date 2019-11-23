---
title: Assistent zum Ändern von Anmelde Informationen (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 07ca904ab8f98dd4dcbdba3f18f4a6fc6469f26a
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952318"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Anmeldeinformationen (einheitlicher SSRS-Modus)
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager stellt einen Assistenten zum Ändern der Anmeldeinformationen bereit, der Sie durch alle Schritte der Neukonfiguration des Kontos führt, anhand dessen der Berichtsserver die Verbindung mit der Berichtsserverdatenbank herstellt. Wenn Sie die Anmeldeinformationen ändern, aktualisiert der Konfigurations-Manager alle Berechtigungen und Datenbank-Anmeldedaten auf dem Datenbankserver für die Berichtsserver-Datenbank, die vom Berichtsserver verwendet wird.  
  
 Um den Assistenten zu starten, klicken Sie auf der Datenbankseite im **-Konfigurationsmanager auf** Anmeldeinformationen ändern [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Anweisungen zum Starten des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Tastatur  
 **Daten Bank Server**  
 Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz an, auf der die Berichtsserver-Datenbank ausgeführt wird.  
  
 Um eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz herzustellen, müssen Sie Anmeldeinformationen verwenden, die zum Anmelden auf dem Server und zum Aktualisieren der Datenbankdaten berechtigen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, wenn Sie jedoch über keine Anmelde- oder Datenbankberechtigung verfügen, können Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung angeben.  
  
 Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn Sie eine Verbindung als anderer Windows-Benutzer herstellen möchten, melden Sie sich als dieser Benutzer an, und starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültige Werte sind u. a. das Dienstkonto des Report Server-Webdiensts, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung, die in der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz definiert ist, auf der Sie den Berichtsserver hosten, oder ein Windows-Konto. Wenn Sie ein Windows-Konto verwenden, können Sie ein lokales Konto angeben ( *\<Computername >\\< username\>* ), wenn sich der Berichts Server und die Datenbank auf demselben Computer befinden, oder ein Domänen Benutzerkonto ( *\<Domäne >\\< username\>* ), wenn Sie sich auf unterschiedlichen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer sich in einer anderen oder nicht vertrauenswürdigen Domäne befindet, sollten Sie überlegen, besser eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung zu verwenden. Weitere Informationen zum Auswählen eines Kontos finden Sie unter [Konfigurieren einer Verbindung mit der Berichts &#40;Server-Daten&#41;Bankverbindung (SSRS) Configuration Manager](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Sie den Assistenten starten.  
  
 **Fortschritt und Abschluss**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [SSRS-Datenbank &#40;im&#41; einheitlichen Modus](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Assistent &#40;zum Ändern der Datenbank mit SSRS&#41; ](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) im einheitlichen Modus   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Konfigurations-Manager für Reporting Services F1-Hilfe &#40;Themen SSRS im&#41; einheitlichen Modus](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
