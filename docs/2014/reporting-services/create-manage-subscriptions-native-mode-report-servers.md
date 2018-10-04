---
title: Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], managing
ms.assetid: 7f46cbdb-5102-4941-bca2-5e0ff9012c6b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e531467e69271eacd535fbfd59e127d73513cf2f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48115132"
---
# <a name="create-and-manage-subscriptions-for-native-mode-report-servers"></a>Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus
  In diesem Abschnitt werden Themen zum Verarbeiten, Überwachen und Steuern von Abonnements behandelt. Die Abonnementverwaltung unterscheidet sich für Standardabonnements und datengesteuerte Abonnements. Standardabonnements befinden sich in der Regel im Besitz des Benutzers und werden von diesem verwaltet. Im Gegensatz dazu werden datengesteuerte Abonnements normalerweise von einem Berichtsserveradministrator erstellt und verwaltet.  
  
 Abonnement- und Übermittlungsfunktionen sind standardmäßig aktiviert (für die E-Mail-Übermittlung sind zuvor Konfigurationsschritte erforderlich). Zu den standardmäßigen Übermittlungserweiterungen gehören die E-Mail-Übermittlung per Berichtsserver und Dateifreigabe. Dies sind die einzigen Verteilungsmethoden, die für Abonnements auf einem Berichtsserver im einheitlichen Modus zur Verfügung stehen, außer Sie erstellen oder installieren benutzerdefinierte Übermittlungserweiterungen.  
  
## <a name="permissions-for-subscribing-to-reports-on-a-native-mode-report-server"></a>Berechtigungen zum Abonnieren von Berichten auf einem Berichtsserver im einheitlichen Modus  
 Je nach Verwendungsweise der Rollen können Sie bestimmten Benutzergruppen Abonnementfunktionen zur Verfügung stellen, indem Sie Abonnementaufgaben für verschiedene Rollen aktivieren oder deaktivieren. Abonnementfunktionen sind für Benutzer über die folgenden beiden Tasks verfügbar:  
  
-   Mit dem Task "Einzelne Abonnements verwalten" können Benutzer für einen bestimmten Bericht Abonnements erstellen, ändern und löschen. In den vordefinierten Rollen ist dieser Task Teil der Browser- und Berichts-Generator-Rollen. Mit Rollenzuweisungen, die diesen Task enthalten, können Benutzer nur die Abonnements verwalten, die sie oder er erstellt hat.  
  
-   Mit dem Task "Alle Abonnements verwalten" kann der Benutzer auf alle Abonnements zugreifen und diese ändern. Dieser Task ist für das Erstellen eines datengesteuerten Abonnements erforderlich. In vordefinierten Rollen enthält nur die Inhalts-Manager-Rolle diesen Task.  
  
## <a name="disabling-subscriptions"></a>Deaktivieren von Abonnements  
 Entfernen Sie den Task "Einzelne Abonnements verwalten" aus der Rolle, um zu verhindern, dass Benutzer Abonnements erstellen. Wenn Sie diesen Task entfernen, sind die Abonnementseiten nicht verfügbar. Im Berichts-Manager scheint die Seite Meine Abonnements leer zu sein (kann nicht gelöscht werden), selbst wenn zuvor Abonnements enthalten waren. Das Entfernen von Tasks im Zusammenhang mit Abonnements verhindert, dass Benutzer Abonnements erstellen und ändern. Vorhandene Abonnements werden dadurch jedoch nicht gelöscht. Vorhandene Abonnements werden so lange weiter ausgeführt, bis Sie sie löschen. Weitere Informationen zum Löschen von Abonnements finden Sie unter [erstellen, ändern und Löschen von Standardabonnements &#40;Reporting Services im einheitlichen Modus&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
 Um die abonnementverarbeitung auf einem Berichtsserver zu deaktivieren, Sie können festlegen, die `ScheduleEventsAndReportDeliveryEnabled` Eigenschaft `False` in die **Oberflächenkonfiguration für Reporting Services** Facet [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Richtlinie der richtlinienbasierten Verwaltung. Dadurch wird die Ausführung aller geplanten Vorgänge verhindert. Sie können nicht nur die Abonnementverarbeitung auf dem Berichtsserver deaktivieren.  
  
 Anweisungen zum Abbrechen von Abonnements, die auf dem Berichtsserver verarbeitet wird, finden Sie unter [Verwalten eines ausgeführten Prozesses](subscriptions/manage-a-running-process.md).  
  
## <a name="disabling-delivery-extensions"></a>Deaktivieren von Übermittlungserweiterungen  
 Alle auf einem Berichtsserver installierten Übermittlungserweiterungen sind für jeden Benutzer verfügbar, der Berechtigungen zum Erstellen eines Abonnements für einen vorhandenen Bericht hat. Die folgenden Übermittlungserweiterungen sind verfügbar und werden automatisch konfiguriert:  
  
-   Windows-Dateifreigabe  
  
-   SharePoint-Bibliothek (nur über eine SharePoint-Website verfügbar, die in einem Berichtsserver mit integriertem SharePoint-Modus integriert ist)  
  
 Die E-Mail-Übermittlung muss konfiguriert werden, bevor sie verwendet werden kann. Wenn Sie sie nicht konfigurieren, ist sie nicht verfügbar. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Wenn Sie bestimmte Erweiterungen deaktivieren möchten, können Sie die Erweiterungseinträge in der Datei RSReportServer.config entfernen. Weitere Informationen finden Sie unter [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md) und [Konfigurieren eines Berichtsservers für die e-Mail-Übermittlung &#40;SSRS-Konfigurations-Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Eine entfernte Übermittlungserweiterung ist im Berichts-Manager oder auf einer SharePoint-Website nicht mehr verfügbar. Das Entfernen einer Übermittlungserweiterung kann inaktive Abonnements zur Folge haben. Stellen Sie vor dem Entfernen einer Erweiterung sicher, dass Sie die Abonnements löschen oder sie so konfigurieren, dass sie eine andere Übermittlungserweiterung verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden von „Meine Abonnements“](subscriptions/use-my-subscriptions-native-mode-report-server.md)  
 Erläutert die Verwendung der Seite Meine Abonnements zum Verwalten der eigenen Abonnements.  
  
 [Anhalten der Berichts- und Abonnementverarbeitung](subscriptions/disable-or-pause-report-and-subscription-processing.md)  
 Beschreibt die verschiedenen Möglichkeiten, die Berichtsverarbeitung anzuhalten, z. B. mithilfe von Rollenzuweisungen oder durch Deaktivieren von Berichtsserverressourcen.  
  
 [Steuern der Berichtsverteilung](../../2014/reporting-services/control-report-distribution.md)  
 Beschreibt Konfigurationseinstellungen und Übermittlungsoptionen, mit denen Sie die Verteilung von Berichten steuern können.  
  
 [Überwachen von Reporting Services-Abonnements](subscriptions/monitor-reporting-services-subscriptions.md)  
 Beschreibt, wie Sie ermitteln, ob ein Abonnement erfolgreich ausgeführt wurde oder fehlgeschlagen ist, sowie die Auswirkungen von Änderungen an Berichten auf vorhandene Abonnements.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen, ändern und Löschen von Standardabonnements &#40;Reporting Services im einheitlichen Modus&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
