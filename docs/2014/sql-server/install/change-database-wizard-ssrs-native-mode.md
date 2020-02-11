---
title: Assistent zum Ändern der Datenbank (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
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
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: cd81004765b1ba5d15c5929dc661ce1dea04b371
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952661"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Datenbank (einheitlicher SSRS-Modus)
  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager enthält einen Assistenten zum Ändern der Datenbank, der Sie durch alle Schritte der Erstellung einer neuen Berichtsserver-Datenbank oder der Auswahl einer vorhandenen Berichtsserver-Datenbank führt, die mit der aktuellen Berichtsserverinstanz verwendet werden soll.  
  
 Wenn Sie eine Berichtsserver-Datenbank einer früheren Version auswählen, wird diese auf die Version der verbundenen Berichtsserverinstanz aktualisiert. Wenn der Dienst startet, überprüft er die Datenbankversion und aktualisiert sie automatisch auf das aktuelle Schema.  
  
 Um den Assistenten zu starten, klicken Sie auf der Seite Datenbank im **-Konfigurations-Manager auf** Datenbank ändern [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Anweisungen zum Starten des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.  
  
## <a name="options"></a>Tastatur  
 **Aktion**  
 Wählen Sie den Task aus, den Sie ausführen möchten. Sie können eine neue Datenbank im einheitlichen Modus oder im integrierten SharePoint-Modus erstellen. Oder Sie können eine vorhandene Berichtsserver-Datenbank auswählen, die mit der aktuellen Berichtsserverinstanz verwendet werden soll.  
  
 **Daten Bank Server**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz an, die die Berichts Server-Datenbank hostet. Sie können eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder einem Remotecomputer verwenden. Wenn Sie eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Servernamen im folgenden \<Format ein: *Server*>\\<*Instanz*>.  
  
 Um eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz herzustellen, müssen Sie Anmeldeinformationen verwenden, die zum Anmelden auf dem Server und zum Aktualisieren der Datenbankdaten berechtigen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, wenn Sie jedoch über keine Anmelde- oder Datenbankberechtigung verfügen, müssen Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung angeben. Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn Sie eine Verbindung als anderer Windows-Benutzer herstellen möchten, melden Sie sich als dieser Benutzer an, und starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager.  
  
 Um eine Verbindung mit einer Remoteinstanz herzustellen, müssen Sie diese Instanz zunächst für Remoteverbindungen aktivieren. Einige Versionen und Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lassen Remoteverbindungen standardmäßig nicht zu. Überprüfen Sie mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, ob die Protokolle TCP/IP und Named Pipes aktiviert sind, um festzustellen, ob Remoteverbindungen zugelassen werden. Wenn die Remoteinstanz zudem eine benannte Instanz ist, müssen Sie sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst auf dem Zielserver aktiviert ist und ausgeführt wird. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser stellt die Portnummer bereit, die von der benannten Instanz für den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager verwendet wird.  
  
 **Datenbank**  
 Gibt den Namen der Berichtsserver-Datenbank an, die die Serverdaten speichert. Sie können eine vorhandene Datenbank angeben oder eine neue Datenbank erstellen.  
  
 Die Eigenschaften, die zum Erstellen einer neuen Datenbank verwendet werden, werden im Assistenten angezeigt, wenn Sie auf der Seite Aktionen die Option **Neue Datenbank erstellen** wählen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erstellt zwei Datenbanken, die durch den Namen gebunden sind: eine Datenbank für die Aufnahme von statischen Daten sowie eine temporäre Datenbank zum Speichern von Sitzungs- und Arbeitsdaten. Weitere Informationen finden Sie unter [Report Server Database &#40;SSRS Native Mode&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Online Dokumentation.  
  
 Sie können auch eine vorhandene Berichtsserver-Datenbank auswählen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager filtert keine ungültigen Datenbanken aus. Gültige Datenbanken basieren auf dem Berichtsserver-Datenbankschema (Sie können keine Datenbank auswählen, bei der die erforderlichen Tabellen, Sichten oder gespeicherten Prozeduren fehlen). Wenn Sie eine Datenbank auswählen, die für eine frühere Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]erstellt wurde, wird die Datenbank auf das aktuelle Format aktualisiert.  
  
 **Sprache**  
 Dieser Wert wird nur beim Erstellen einer neuen Berichtsserver-Datenbank festgelegt.  
  
 Mit diesem Wert geben Sie die Sprache an, in der Rollendefinitionen und Beschreibungen erstellt werden. 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet ein rollenbasiertes Autorisierungsmodell, das eine Reihe von vordefinierten Rollen enthält. Diese Rollen werden einmal in der Sprache erstellt, die Sie angeben. Rollennamen und Beschreibungen werden nie in einer anderen Sprache angezeigt, auch wenn Sie eine Verbindung zum Berichtsserver über einen Browser mit Kultur- oder Spracheinstellungen herstellen, die vom Server unterstützt werden. Mit der angegebenen Sprache wird außerdem die Sprache bestimmt, mit der der Name des Ordners Meine Berichte sowie die Benutzerordner erstellt werden, die Bestandteile der Funktion Meine Berichte sind.  
  
 **Server Modus**  
 Eine Berichtsserver-Datenbank unterstützt entweder den einheitlichen Modus oder den integrierten SharePoint-Modus. Die Modi schließen sich gegenseitig aus.  
  
 Wenn Sie eine neue Berichtsserver-Datenbank erstellen, müssen Sie einen Modus angeben. Der ausgewählte Modus bestimmt die Struktur der Berichtsserver-Datenbank und legt die `SharePointIntegrated`-Systemeigenschaft des Berichtsservers auf `true` oder `false` fest.  
  
 Bei Auswahl einer anderen Berichtsserver-Datenbank wird der Modus der aktuellen Datenbank angezeigt, sodass Sie wissen, wie die aktuelle Datenbank verwendet wird.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültige Werte sind u. a. das Dienstkonto des Report Server-Webdiensts, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung, die in der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz definiert ist, auf der Sie den Berichtsserver hosten, oder ein Windows-Konto. Wenn Sie ein Windows-Konto verwenden, können Sie ein lokales Konto (*\<Computer \\ Name><username\>*) angeben, wenn sich der Berichts Server und die Datenbank auf demselben Computer befinden, oder ein Domänen Benutzerkonto (*\<Domänen>\\<username\>*), wenn Sie sich auf unterschiedlichen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer sich in einer anderen oder nicht vertrauenswürdigen Domäne befindet, sollten Sie überlegen, besser eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung zu verwenden. Weitere Informationen zum Auswählen eines Kontos finden Sie unter [Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Setup die Verbindung konfiguriert.  
  
 **Status und Fertig stellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Assistent zum Ändern von Anmelde Informationen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichts Server-Datenbank im einheitlichen Modus &#40;SSRS-Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Konfigurations-Manager für Reporting Services F1-Hilfe Themen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
