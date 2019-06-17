---
title: Ändern von Datenbank-Assistenten (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc07e94db985ce156fdd5cd59620c2e7fddc2d73
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096670"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Datenbank (einheitlicher SSRS-Modus)
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager enthält einen Assistenten zum Ändern der Datenbank, der Sie durch alle Schritte der Erstellung einer neuen Berichtsserver-Datenbank oder der Auswahl einer vorhandenen Berichtsserver-Datenbank führt, die mit der aktuellen Berichtsserverinstanz verwendet werden soll.  
  
 Wenn Sie eine Berichtsserver-Datenbank einer früheren Version auswählen, wird diese auf die Version der verbundenen Berichtsserverinstanz aktualisiert. Wenn der Dienst startet, überprüft er die Datenbankversion und aktualisiert sie automatisch auf das aktuelle Schema.  
  
 Um den Assistenten zu starten, klicken Sie auf der Seite Datenbank im **-Konfigurations-Manager auf** Datenbank ändern [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Anweisungen zum Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Optionen  
 **Aktion**  
 Wählen Sie den Task aus, den Sie ausführen möchten. Sie können eine neue Datenbank im einheitlichen Modus oder im integrierten SharePoint-Modus erstellen. Oder Sie können eine vorhandene Berichtsserver-Datenbank auswählen, die mit der aktuellen Berichtsserverinstanz verwendet werden soll.  
  
 **Datenbank-Server**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz an, die die Berichtsserver-Datenbank hostet. Sie können eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder einem Remotecomputer verwenden. Wenn Sie die zu einer benannten Instanz herstellen, geben Sie den Servernamen im folgenden Format: \< *Server*>\\<*Instanz*>.  
  
 Um eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz herzustellen, müssen Sie Anmeldeinformationen verwenden, die zum Anmelden auf dem Server und zum Aktualisieren der Datenbankdaten berechtigen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, wenn Sie jedoch über keine Anmelde- oder Datenbankberechtigung verfügen, müssen Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung angeben. Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn Sie eine Verbindung als anderer Windows-Benutzer herstellen möchten, melden Sie sich als dieser Benutzer an, und starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager.  
  
 Um eine Verbindung mit einer Remoteinstanz herzustellen, müssen Sie diese Instanz zunächst für Remoteverbindungen aktivieren. Einige Versionen und Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lassen Remoteverbindungen standardmäßig nicht zu. Überprüfen Sie mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, ob die Protokolle TCP/IP und Named Pipes aktiviert sind, um festzustellen, ob Remoteverbindungen zugelassen werden. Wenn die Remoteinstanz zudem eine benannte Instanz ist, müssen Sie sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst auf dem Zielserver aktiviert ist und ausgeführt wird. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser stellt die Portnummer bereit, die von der benannten Instanz für den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager verwendet wird.  
  
 **Datenbank**  
 Gibt den Namen der Berichtsserver-Datenbank an, die die Serverdaten speichert. Sie können eine vorhandene Datenbank angeben oder eine neue Datenbank erstellen.  
  
 Die Eigenschaften, die zum Erstellen einer neuen Datenbank verwendet werden, werden im Assistenten angezeigt, wenn Sie auf der Seite Aktionen die Option **Neue Datenbank erstellen** wählen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erstellt zwei Datenbanken, die durch den Namen gebunden sind: eine Datenbank für die Aufnahme von statischen Daten sowie eine temporäre Datenbank zum Speichern von Sitzungs- und Arbeitsdaten. Weitere Informationen finden Sie unter [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41; ](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 Sie können auch eine vorhandene Berichtsserver-Datenbank auswählen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager filtert keine ungültigen Datenbanken aus. Gültige Datenbanken basieren auf dem Berichtsserver-Datenbankschema (Sie können keine Datenbank auswählen, bei der die erforderlichen Tabellen, Sichten oder gespeicherten Prozeduren fehlen). Wenn Sie eine Datenbank auswählen, die für eine frühere Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]erstellt wurde, wird die Datenbank auf das aktuelle Format aktualisiert.  
  
 **Sprache**  
 Dieser Wert wird nur beim Erstellen einer neuen Berichtsserver-Datenbank festgelegt.  
  
 Mit diesem Wert geben Sie die Sprache an, in der Rollendefinitionen und Beschreibungen erstellt werden. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet ein rollenbasiertes Autorisierungsmodell, das eine Reihe von vordefinierten Rollen enthält. Diese Rollen werden einmal in der Sprache erstellt, die Sie angeben. Rollennamen und Beschreibungen werden nie in einer anderen Sprache angezeigt, auch wenn Sie eine Verbindung zum Berichtsserver über einen Browser mit Kultur- oder Spracheinstellungen herstellen, die vom Server unterstützt werden. Mit der angegebenen Sprache wird außerdem die Sprache bestimmt, mit der der Name des Ordners Meine Berichte sowie die Benutzerordner erstellt werden, die Bestandteile der Funktion Meine Berichte sind.  
  
 **Servermodus**  
 Eine Berichtsserver-Datenbank unterstützt entweder den einheitlichen Modus oder den integrierten SharePoint-Modus. Die Modi schließen sich gegenseitig aus.  
  
 Wenn Sie eine neue Berichtsserver-Datenbank erstellen, müssen Sie einen Modus angeben. Der ausgewählte Modus bestimmt die Struktur der Berichtsserver-Datenbank und legt die `SharePointIntegrated`-Systemeigenschaft des Berichtsservers auf `true` oder `false` fest.  
  
 Bei Auswahl einer anderen Berichtsserver-Datenbank wird der Modus der aktuellen Datenbank angezeigt, sodass Sie wissen, wie die aktuelle Datenbank verwendet wird.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültige Werte sind u. a. das Dienstkonto des Report Server-Webdiensts, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung, die in der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz definiert ist, auf der Sie den Berichtsserver hosten, oder ein Windows-Konto. Wenn Sie ein Windows-Konto verwenden, können Sie angeben, dass ein lokales Konto ( *\<Computername >\\< Benutzername\>* ), wenn der Berichtsserver und die Datenbank auf demselben Computer oder Benutzer einer Domäne sind Konto ( *\<Domäne >\\< Benutzername\>* ) Wenn sie sich auf verschiedenen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer sich in einer anderen oder nicht vertrauenswürdigen Domäne befindet, sollten Sie überlegen, besser eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung zu verwenden. Weitere Informationen zum Auswählen eines Kontos finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Setup die Verbindung konfiguriert.  
  
 **Fortsetzen und Fertigstellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Anmeldeinformationen-Assistent zum Ändern der &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
