---
title: Ändern von Anmeldeinformationen-Assistenten (einheitlicher SSRS-Modus) | Microsoft Docs
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
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: c742a02d3accf2a51c2c31bac598064ca34f14c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148768"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Anmeldeinformationen (einheitlicher SSRS-Modus)
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager stellt einen Assistenten zum Ändern der Anmeldeinformationen bereit, der Sie durch alle Schritte der Neukonfiguration des Kontos führt, anhand dessen der Berichtsserver die Verbindung mit der Berichtsserverdatenbank herstellt. Wenn Sie die Anmeldeinformationen ändern, aktualisiert der Konfigurations-Manager alle Berechtigungen und Datenbank-Anmeldedaten auf dem Datenbankserver für die Berichtsserver-Datenbank, die vom Berichtsserver verwendet wird.  
  
 Um den Assistenten zu starten, klicken Sie auf **Ändern von Anmeldeinformationen** auf der Seite Datenbank in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Anweisungen zum Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Tastatur  
 **Datenbankserver**  
 Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz, die die Berichtsserver-Datenbank ausgeführt wird.  
  
 Für die Verbindung der [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz müssen Sie Anmeldeinformationen, die über die Berechtigung zum Anmelden der Server und zum Aktualisieren der Datenbankinformationen verwenden. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, aber wenn Sie nicht über einen Anmelde- oder Datenbankberechtigung verfügen, können Sie angeben einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung.  
  
 Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn eine Verbindung als anderer Windows-Benutzer, melden Sie sich als dieser Benutzer herstellen und dann neu gestartet werden soll die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültigen Werten gehören das Dienstkonto des Report Server-Webdienst eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Anmeldenamen, die definiert, auf die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz, die Sie zum Hosten der Berichtsserver oder ein Windowskonto verwenden. Wenn Sie ein Windows-Konto verwenden, können Sie ein lokales Konto angeben (*\<Computername >\\< Benutzername\>*), wenn der Berichtsserver und die Datenbank auf demselben Computer oder Benutzer als Domänenbenutzer sind Konto (*\<Domäne >\\< Benutzername\>*) Wenn sie sich auf verschiedenen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer in einer anderen oder nicht vertrauenswürdigen Domäne befindet, können Sie verwenden eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Weitere Informationen zur Auswahl eines Kontos finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Sie den Assistenten starten.  
  
 **Status und Fertig stellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Datenbank-Assistent zum Ändern der &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurationsmanager-F1-Hilfethemen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren Sie eine Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  