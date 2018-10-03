---
title: Ändern von Datenbank-Assistenten (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 50870072259f89af43fc14ee23465f282f4c3e9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066130"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Datenbank (einheitlicher SSRS-Modus)
  Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager bietet der Assistent zum Ändern einer Datenbank, der Sie durch die Schritte zum Erstellen einer neuen Berichtsserver-Datenbank, oder wählen eine vorhandene Berichtsserver-Datenbank mit der aktuellen Berichtsserverinstanz verwendet führt.  
  
 Wenn Sie eine Berichtsserver-Datenbank einer früheren Version auswählen, wird diese auf die Version der verbundenen Berichtsserverinstanz aktualisiert. Wenn der Dienst startet, überprüft er die Datenbankversion und aktualisiert sie automatisch auf das aktuelle Schema.  
  
 Um den Assistenten zu starten, klicken Sie auf **Änderungsdatenbank** auf der Seite "Datenbank" in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager. Anweisungen zum Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Tastatur  
 **Aktion**  
 Wählen Sie den Task aus, den Sie ausführen möchten. Sie können eine neue Datenbank im einheitlichen Modus oder im integrierten SharePoint-Modus erstellen. Oder Sie können eine vorhandene Berichtsserver-Datenbank auswählen, die mit der aktuellen Berichtsserverinstanz verwendet werden soll.  
  
 **Datenbank-Server**  
 Geben Sie den Namen des der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, die die Berichtsserver-Datenbank hostet. Sie können eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder einem Remotecomputer verwenden. Wenn Sie die zu einer benannten Instanz herstellen, geben Sie den Servernamen im folgenden Format: \< *Server*>\\<*Instanz*>.  
  
 Zum Herstellen einer Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz müssen Sie Anmeldeinformationen, die über die Berechtigung zum Anmelden der Server und Datenbank-Informationen verwenden. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, aber wenn Sie nicht über einen Anmelde- oder Datenbankberechtigung verfügen, geben Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn Sie verwenden möchten, Herstellen einer Verbindung als anderer Windows-Benutzer melden Sie sich als dieser Benutzer aus, und starten Sie dann die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager.  
  
 Um eine Verbindung mit einer Remoteinstanz herzustellen, müssen Sie diese Instanz zunächst für Remoteverbindungen aktivieren. Einige Versionen und Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lassen Remoteverbindungen standardmäßig nicht zu. Verwenden Sie zum Überprüfen, ob Remoteverbindungen zugelassen werden, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurations-Manager, und bestätigen Sie, dass die Protokolle TCP/IP und Named Pipes aktiviert sind. Wenn die Remoteinstanz zudem eine benannte Instanz ist, müssen Sie sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst auf dem Zielserver aktiviert ist und ausgeführt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser stellt die Nummer des Ports, mit dem der benannten Instanz für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager.  
  
 **Datenbank**  
 Gibt den Namen der Berichtsserver-Datenbank an, die die Serverdaten speichert. Sie können eine vorhandene Datenbank angeben oder eine neue Datenbank erstellen.  
  
 Die Eigenschaften, die zum Erstellen einer neuen Datenbank verwendet werden, werden im Assistenten angezeigt, wenn Sie auf der Seite Aktionen die Option **Neue Datenbank erstellen** wählen. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager erstellt zwei Datenbanken, die durch den Namen gebunden sind: eine Datenbank von statischen Daten sowie eine temporäre Datenbank zum Speichern von Sitzungs-und Arbeitsdaten. Weitere Informationen finden Sie unter [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41; ](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 Sie können auch eine vorhandene Berichtsserver-Datenbank auswählen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager filtert keine ungültigen Datenbanken aus. Gültige Datenbanken basieren auf dem Berichtsserver-Datenbankschema (Sie können keine Datenbank auswählen, bei der die erforderlichen Tabellen, Sichten oder gespeicherten Prozeduren fehlen). Wenn Sie eine Datenbank auswählen, die für eine frühere Version des erstellten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], die Datenbank wird in das aktuelle Format aktualisiert werden.  
  
 **Sprache**  
 Dieser Wert wird nur beim Erstellen einer neuen Berichtsserver-Datenbank festgelegt.  
  
 Mit diesem Wert geben Sie die Sprache an, in der Rollendefinitionen und Beschreibungen erstellt werden. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet ein rollenbasiertes Autorisierungsmodell, das eine Reihe von vordefinierten Rollen enthält. Diese Rollen werden einmal in der Sprache erstellt, die Sie angeben. Rollennamen und Beschreibungen werden nie in einer anderen Sprache angezeigt, auch wenn Sie eine Verbindung zum Berichtsserver über einen Browser mit Kultur- oder Spracheinstellungen herstellen, die vom Server unterstützt werden. Mit der angegebenen Sprache wird außerdem die Sprache bestimmt, mit der der Name des Ordners Meine Berichte sowie die Benutzerordner erstellt werden, die Bestandteile der Funktion Meine Berichte sind.  
  
 **Servermodus**  
 Eine Berichtsserver-Datenbank unterstützt entweder den einheitlichen Modus oder den integrierten SharePoint-Modus. Die Modi schließen sich gegenseitig aus.  
  
 Wenn Sie eine neue Berichtsserver-Datenbank erstellen, müssen Sie einen Modus angeben. Der ausgewählte Modus bestimmt die Struktur der Berichtsserver-Datenbank und legt die `SharePointIntegrated` Berichtsserver-Systemeigenschaft fest, `true` oder `false`.  
  
 Bei Auswahl einer anderen Berichtsserver-Datenbank wird der Modus der aktuellen Datenbank angezeigt, sodass Sie wissen, wie die aktuelle Datenbank verwendet wird.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültige Werte sind das Dienstkonto des Report Server-Webdienst, eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung für definiert die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz, die Sie verwenden, um den Berichtsserver oder einem Windows-Konto gehostet werden soll. Wenn Sie ein Windows-Konto verwenden, können Sie angeben, dass ein lokales Konto (*\<Computername >\\< Benutzername\>*), wenn der Berichtsserver und die Datenbank auf demselben Computer oder Benutzer einer Domäne sind Konto (*\<Domäne >\\< Benutzername\>*) Wenn sie sich auf verschiedenen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer in einer anderen oder nicht vertrauenswürdigen Domäne ist, sollten Sie verwenden eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Weitere Informationen zum Auswählen eines Kontos finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Setup die Verbindung konfiguriert.  
  
 **Fortsetzen und Fertigstellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Anmeldeinformationen-Assistent zum Ändern der &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurations-Manager-F1-Hilfethemen &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren eine Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
