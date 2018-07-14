---
title: Ändern Sie die Assistenten der Anmeldeinformationen (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0163bff016043e31bf36a689220976b85e4ae097
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244292"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Anmeldeinformationen (einheitlicher SSRS-Modus)
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager stellt einen Assistenten zum Ändern der Anmeldeinformationen bereit, der Sie durch alle Schritte der Neukonfiguration des Kontos führt, anhand dessen der Berichtsserver die Verbindung mit der Berichtsserverdatenbank herstellt. Wenn Sie die Anmeldeinformationen ändern, aktualisiert der Konfigurations-Manager alle Berechtigungen und Datenbank-Anmeldedaten auf dem Datenbankserver für die Berichtsserver-Datenbank, die vom Berichtsserver verwendet wird.  
  
 Um den Assistenten zu starten, klicken Sie auf **Anmeldeinformationen ändern** auf der Seite "Datenbank" in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager. Anweisungen zum Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Tastatur  
 **Datenbank-Server**  
 Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz, die die Berichtsserver-Datenbank ausgeführt wird.  
  
 Zum Herstellen einer Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz müssen Sie Anmeldeinformationen, die über die Berechtigung zum Anmelden der Server und Datenbank-Informationen verwenden. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, aber wenn Sie nicht über einen Anmelde- oder Datenbankberechtigung verfügen, können Sie angeben einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung.  
  
 Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn Sie verwenden möchten, Herstellen einer Verbindung als anderer Windows-Benutzer melden Sie sich als dieser Benutzer aus, und starten Sie dann die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültige Werte sind das Dienstkonto des Report Server-Webdienst, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung für definiert die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz, die Sie verwenden, um den Berichtsserver oder einem Windows-Konto gehostet werden soll. Wenn Sie ein Windows-Konto verwenden, können Sie angeben, dass ein lokales Konto (*\<Computername >\\< Benutzername\>*), wenn der Berichtsserver und die Datenbank auf demselben Computer oder Benutzer einer Domäne sind Konto (*\<Domäne >\\< Benutzername\>*) Wenn sie sich auf verschiedenen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer in einer anderen oder nicht vertrauenswürdigen Domäne ist, sollten Sie verwenden eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Weitere Informationen zum Auswählen eines Kontos finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Sie den Assistenten starten.  
  
 **Fortsetzen und Fertigstellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Datenbank-Assistent zum Ändern der &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren eine Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
