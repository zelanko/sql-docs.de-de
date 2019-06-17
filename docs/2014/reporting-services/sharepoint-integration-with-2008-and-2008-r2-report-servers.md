---
title: SharePoint-Integration in 2008 und 2008 R2-Berichtsservern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9f51c37-b071-45d0-baec-f82fa6db366f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d29d41069d5daca25d53477326e864720aa87ca1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66101194"
---
# <a name="sharepoint-integration-with-2008-and-2008-r2--report-servers"></a>SharePoint-Integration in Berichtsserver der Versionen 2008 und 2008 R2
  Mit der [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Version von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] wurde eine Architektur eingeführt, bei der der SharePoint-Modus jetzt auf einem gemeinsamen SharePoint-Dienst basiert. Verwaltung von der neuen Funktionen in der SharePoint-Zentraladministration abgeschlossen ist, auf die **Dienste verwalten** und **Manager-Dienstanwendungen** Seiten. Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] vorherigen-Architektur für SharePoint-Integration wird weiterhin unterstützt, mit der [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in für SharePoint 2010-Produkte, sodass Sie SharePoint 2010 mit früheren Versionen eines Berichtsservers integrieren können.  
  
 Die Seiten der SharePoint-Zentraladministration, auf denen sich die ältere Architektur verwalten lässt, werden wie folgt aufgerufen:  
  
1.  Klicken Sie auf SharePoint-Zentraladministration auf **allgemeine Anwendungseinstellungen**.  
  
2.  Die Gruppe **SQL Server Reporting Services (2008 und 2008 R2)** enthält die Links und Verwaltungsseiten für die ältere Architektur  
  
## <a name="server-integration-architecture"></a>Serverintegrationsarchitektur  
 Wenn Sie einen Berichtsserver in eine Instanz eines SharePoint-Produkts integrieren, werden Elemente und Eigenschaften in der SharePoint-Inhaltsdatenbank gespeichert. Dies ermöglicht eine bessere Abstimmung der beiden Servertechnologien, was sich auf Speicherung, Schutz und Zugriff auf Inhalte auswirkt.  
  
 Das Speichern von Berichtselementen und Eigenschaften in SharePoint-Inhaltsdatenbanken ermöglicht Ihnen Folgendes: Durchsuchen von SharePoint-Bibliotheken nach Berichtsserver-Inhaltstypen, Schützen von Elementen mithilfe derselben Berechtigungsstufen und desselben Authentifizierungsanbieters, der den Zugriff auf andere Geschäftsdokumente steuert, die auf einer SharePoint-Website gehostet werden, Verwenden von Funktionen für Zusammenarbeit und Dokumentverwaltung, um Berichte zum Einarbeiten von Änderungen ein- und auszuchecken, Verwenden von Warnungen, um auf geänderte Dokumente hinzuweisen, und Einbetten oder Anpassen des Berichts-Viewer-Webparts in Seiten und Websites innerhalb der Anwendung. Wenn Sie die erforderlichen Berechtigungen für eine SharePoint-Website verfügen, können Sie auch auf der Grundlage freigegebener Datenquellen Berichtsmodelle generieren und mit dem Berichts-Generator Berichte erstellen.  
  
 Der Berichtsserver stellt weiterhin alle Datenverarbeitungs-, Rendering- und Übermittlungsfunktionen bereit. Er unterstützt darüber hinaus die geplante Berichtsverarbeitung für Momentaufnahmen und Berichtsverläufe. Wenn Sie einen Bericht über eine SharePoint-Website öffnen, stellt der ReportServer-Endpunkt eine Verbindung mit einem Berichtsserver her, erstellt eine Sitzung, bereitet den Bericht für die Verarbeitung vor, ruft Daten ab, überführt den Bericht in das Berichtslayout und zeigt ihn im Berichts-Viewer-Webpart an. Während der Bericht geöffnet ist, können Sie ihn in verschiedene Anwendungsformate exportieren oder den Bericht interaktiv verwenden, indem Sie einen Drilldown zu tiefer liegenden Zahlen ausführen oder sich zu einem verwandten Bericht durchklicken. Export- und Berichtsinteraktionsvorgänge werden auf dem Berichtsserver durchgeführt.  
  
 Der Berichtsserver synchronisiert Vorgänge und Daten mit SharePoint und verfolgt Informationen zu den verarbeiteten Dateien. Wenn Sie Eigenschaften oder Einstellungen für ein beliebiges Berichtsserverelement ändern, wird die Änderung in einer SharePoint-Datenbank gespeichert und dann in eine Berichtsserver-Datenbank kopiert, die als interner Speicher für einen Berichtsserver dient.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
 Beschreibt die Aktivierung der Berichtsserverfunktion, die für die Integration in Berichtsserver aus vorherigen Versionen erforderlich ist.  
  
  
