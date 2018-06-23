---
title: Ändern von Datenbank-Assistenten (einheitlicher SSRS-Modus) | Microsoft Docs
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
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 256d91789d4bc1413580fde6f5c40ff8151f309a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059944"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Assistent zum Ändern der Datenbank (einheitlicher SSRS-Modus)
  Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager bietet der Assistent zum Ändern einer Datenbank um Sie schrittweise durch die Schritte zum Erstellen einer neuen Berichtsserver-Datenbank, oder wählen Sie eine vorhandene Berichtsserver-Datenbank für die Verwendung mit der aktuellen Berichtsserverinstanz her.  
  
 Wenn Sie eine Berichtsserver-Datenbank einer früheren Version auswählen, wird diese auf die Version der verbundenen Berichtsserverinstanz aktualisiert. Wenn der Dienst startet, überprüft er die Datenbankversion und aktualisiert sie automatisch auf das aktuelle Schema.  
  
 Um den Assistenten zu starten, klicken Sie auf **Änderungsdatenbank** auf der Seite Datenbank in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Anweisungen zum Starten der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
## <a name="options"></a>Tastatur  
 **Aktion**  
 Wählen Sie den Task aus, den Sie ausführen möchten. Sie können eine neue Datenbank im einheitlichen Modus oder im integrierten SharePoint-Modus erstellen. Oder Sie können eine vorhandene Berichtsserver-Datenbank auswählen, die mit der aktuellen Berichtsserverinstanz verwendet werden soll.  
  
 **Datenbankserver**  
 Geben Sie den Namen des der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, die die Berichtsserver-Datenbank hostet. Sie können eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder einem Remotecomputer verwenden. Wenn Sie eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Servernamen im folgenden Format: \< *Server*>\\<*Instanz*>.  
  
 Für die Verbindung der [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz müssen Sie Anmeldeinformationen, die über die Berechtigung zum Anmelden der Server und zum Aktualisieren der Datenbankinformationen verwenden. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager verwendet Ihre aktuellen Windows-Anmeldeinformationen, aber wenn Sie nicht über einen Anmelde- oder Datenbankberechtigung verfügen, müssen Sie angeben einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Sie können keine anderen Windows-Anmeldeinformationen angeben. Wenn eine Verbindung als anderer Windows-Benutzer, melden Sie sich als dieser Benutzer herstellen und dann neu gestartet werden soll die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 Um eine Verbindung mit einer Remoteinstanz herzustellen, müssen Sie diese Instanz zunächst für Remoteverbindungen aktivieren. Einige Versionen und Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lassen Remoteverbindungen standardmäßig nicht zu. Um zu überprüfen, ob Remoteverbindungen zugelassen werden, verwenden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager und vergewissern Sie sich, dass die Protokolle TCP/IP und Named Pipes aktiviert sind. Wenn die Remoteinstanz zudem eine benannte Instanz ist, müssen Sie sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst auf dem Zielserver aktiviert ist und ausgeführt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser stellt die Portnummer, die von der benannten Instanz um dient der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 **Datenbank**  
 Gibt den Namen der Berichtsserver-Datenbank an, die die Serverdaten speichert. Sie können eine vorhandene Datenbank angeben oder eine neue Datenbank erstellen.  
  
 Die Eigenschaften, die zum Erstellen einer neuen Datenbank verwendet werden, werden im Assistenten angezeigt, wenn Sie auf der Seite Aktionen die Option **Neue Datenbank erstellen** wählen. Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager erstellt zwei Datenbanken, die durch den Namen gebunden sind: eine Datenbank statischen Daten sowie eine temporäre Datenbank zum Speichern von Sitzungs-und Arbeitsdaten enthalten. Weitere Informationen finden Sie unter [Berichtsserverdatenbank &#40;SSRS im einheitlichen Modus&#41; ](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
 Sie können auch eine vorhandene Berichtsserver-Datenbank auswählen. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager filtert keine ungültigen Datenbanken aus. Gültige Datenbanken basieren auf dem Berichtsserver-Datenbankschema (Sie können keine Datenbank auswählen, bei der die erforderlichen Tabellen, Sichten oder gespeicherten Prozeduren fehlen). Wenn Sie eine Datenbank auswählen, die für eine frühere Version von erstellt wurde [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], die Datenbank auf das aktuelle Format aktualisiert werden.  
  
 **Sprache**  
 Dieser Wert wird nur beim Erstellen einer neuen Berichtsserver-Datenbank festgelegt.  
  
 Mit diesem Wert geben Sie die Sprache an, in der Rollendefinitionen und Beschreibungen erstellt werden. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet ein rollenbasiertes Autorisierungsmodell, das eine Reihe von vordefinierten Rollen enthält. Diese Rollen werden einmal in der Sprache erstellt, die Sie angeben. Rollennamen und Beschreibungen werden nie in einer anderen Sprache angezeigt, auch wenn Sie eine Verbindung zum Berichtsserver über einen Browser mit Kultur- oder Spracheinstellungen herstellen, die vom Server unterstützt werden. Mit der angegebenen Sprache wird außerdem die Sprache bestimmt, mit der der Name des Ordners Meine Berichte sowie die Benutzerordner erstellt werden, die Bestandteile der Funktion Meine Berichte sind.  
  
 **Modus "Server"**  
 Eine Berichtsserver-Datenbank unterstützt entweder den einheitlichen Modus oder den integrierten SharePoint-Modus. Die Modi schließen sich gegenseitig aus.  
  
 Wenn Sie eine neue Berichtsserver-Datenbank erstellen, müssen Sie einen Modus angeben. Der ausgewählte Modus bestimmt die Struktur der Berichtsserver-Datenbank und legt die `SharePointIntegrated` Berichtsserver-Systemeigenschaft auf `true` oder `false`.  
  
 Bei Auswahl einer anderen Berichtsserver-Datenbank wird der Modus der aktuellen Datenbank angezeigt, sodass Sie wissen, wie die aktuelle Datenbank verwendet wird.  
  
 **Anmeldeinformationen**  
 Gibt das Benutzerkonto an, mit dem der Berichtsserver eine Verbindung mit der Berichtsserver-Datenbank herstellt. Gültigen Werten gehören das Dienstkonto des Report Server-Webdienst eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Anmeldenamen, die definiert, auf die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Instanz, die Sie zum Hosten der Berichtsserver oder ein Windowskonto verwenden. Wenn Sie ein Windows-Konto verwenden, können Sie ein lokales Konto angeben (*\<Computername >\\< Benutzername\>*), wenn der Berichtsserver und die Datenbank auf demselben Computer oder Benutzer als Domänenbenutzer sind Konto (*\<Domäne >\\< Benutzername\>*) Wenn sie sich auf verschiedenen Computern in derselben Domäne befinden.  
  
 Der Berichtsserver erstellt eine Datenbankanmeldung und weist die Datenbankberechtigungen dem Konto zu, das Sie angeben.  
  
 Der Berichtsserver erstellt das Konto nicht selbst. Das Konto, das Sie angeben, muss bereits vorhanden sein, und es muss für Ihre Bereitstellungskonfiguration gültig sein. Besonders dann, wenn sich die Datenbank auf einem Remote-Computer befindet und Sie ein Windows-Konto verwenden möchten, müssen Sie ein Konto angeben, das zur Anmeldung auf diesem Computer berechtigt ist.  
  
 Wenn der Computer in einer anderen oder nicht vertrauenswürdigen Domäne befindet, können Sie verwenden eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Weitere Informationen zur Auswahl eines Kontos finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Zusammenfassung**  
 Überprüfen Sie die Einstellungen, bevor Setup die Verbindung konfiguriert.  
  
 **Status und Fertig stellen**  
 Überwachen Sie den Status aller Tasks.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Anmeldeinformationen-Assistent zum Ändern der &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurationsmanager-F1-Hilfethemen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Konfigurieren Sie eine Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  