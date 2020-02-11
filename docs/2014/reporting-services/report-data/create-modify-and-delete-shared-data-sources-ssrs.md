---
title: Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- modifying data source properties
- shared data sources [Reporting Services]
- removing shared data sources
- roles [Reporting Services], shared data sources
- data sources [Reporting Services], shared
- data sources [Reporting Services], modifying properties
- deleting shared data sources
ms.assetid: 1e58c1c2-5ecf-4ce6-9d04-0a8acfba17be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a2239e07cc24842c5cbdf44c8743ea2d79ea7cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107401"
---
# <a name="create-modify-and-delete-shared-data-sources-ssrs"></a>Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)
  Eine freigegebene Datenquelle besteht aus einem Satz von Datenquellen-Verbindungseigenschaften, auf die von mehreren auf einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver ausgeführten Berichten, Modellen und datengesteuerten Abonnements verwiesen werden kann. Freigegebene Datenquellen bieten eine einfache Möglichkeit, Datenquelleneigenschaften zu verwalten, die sich im Laufe der Zeit häufig ändern. Wenn sich ein Benutzerkonto oder Kennwort ändert oder Sie die Datenbank auf einen anderen Server verschieben, können Sie die Verbindungsinformationen zentral aktualisieren.  
  
 Freigegebene Datenquellen sind für Berichte und datengesteuerte Abonnements optional, für Berichtsmodelle jedoch erforderlich. Wenn Sie Berichtsmodelle für die Ad-hoc-Berichterstellung verwenden möchten, müssen Sie ein freigegebenes Datenquellenelement erstellen und verwalten, um Verbindungsinformationen für das Modell bereitzustellen.  
  
 Eine freigegebene Datenquelle setzt sich aus folgenden Komponenten zusammen:  
  
|Teil|BESCHREIBUNG|  
|----------|-----------------|  
|Name|Ein Name, der das Element innerhalb der Ordnerhierarchie des Berichtsservers identifiziert.|  
|BESCHREIBUNG|Eine Beschreibung, die mit dem Element im Berichts-Manager angezeigt wird, wenn Sie den Inhalt des Ordners anzeigen.|  
|Verbindungstyp|Die für die Datenquelle verwendete Datenverarbeitungserweiterung. Sie können nur Datenverarbeitungserweiterungen verwenden, die auf dem Berichtsserver bereitgestellt werden. Weitere Informationen zu in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthaltenen Datenverarbeitungserweiterungen finden Sie unter [Von Reporting Services unterstützte Datenquellen (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md).|  
|Verbindungszeichenfolge|Die Verbindungszeichenfolge für die Datenbank. Weitere Informationen und Beispiele für Verbindungs Zeichenfolgen zu häufig verwendeten Datenquellen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)Zeichenfolgen in Reporting Services.|  
|Anmeldeinformationstyp|Gibt an, wie Anmeldeinformationen für die Verbindung abgerufen werden und ob sie nach dem Herstellen der Verbindung verwendet werden sollen. Weitere Informationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../integration-services/connection-manager/data-sources.md).|  
  
 Eine freigegebene Datenquelle enthält keine Abfrageinformationen für das Abrufen von Daten. Die Abfrage ist stets Bestandteil einer Berichtsdefinition.  
  
## <a name="creating-and-modifying-a-shared-data-source"></a>Erstellen und Ändern einer freigegebenen Datenquelle  
 Zum Erstellen einer freigegebenen Datenquelle oder zum Bearbeiten ihrer Eigenschaften ist die Berechtigung **Datenquellen verwalten** für den Berichtsserver erforderlich. Wenn der Berichtsserver im einheitlichen Modus ausgeführt wird, können Sie die freigegebene Datenquelle mit dem Berichts-Manager erstellen und konfigurieren. Wird der Berichtsserver im integrierten SharePoint-Modus ausgeführt, können Sie die Anwendungsseiten einer SharePoint-Website verwenden. Unabhängig vom jeweiligen Modus können Sie für jeden Berichtsserver eine freigegebene Datenquelle im Berichts-Designer erstellen und sie anschließend auf einem Zielserver veröffentlichen.  
  
 Weitere Informationen zum Erstellen einer freigegebenen Datenquelle finden Sie unter:  
  
-   [Erstellen einer eingebetteten oder freigegebenen Datenquelle &#40;SSRS-&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)  
  
-   [Erstellen und Verwalten von freigegebenen Datenquellen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)  
  
 Nachdem Sie eine freigegebene Datenquelle auf dem Berichtsserver erstellt haben, können Sie Rollenzuweisungen zur Steuerung des Zugriffs erstellen, die Datenquelle an einen anderen Speicherort verschieben, sie umbenennen sowie den Offlinemodus aktivieren, um die Berichtsverarbeitung zu verhindern, während Wartungsvorgänge für die externe Datenquelle ausgeführt werden. Falls Sie ein freigegebenes Datenquellenelement umbenennen oder in einen anderen Speicherort in der Ordnerhierarchie des Berichtsservers verschieben, werden die Pfadangaben in allen Berichten oder Abonnements, die auf die freigegebene Datenquelle verweisen, entsprechend aktualisiert. Wenn Sie die freigegebene Datenquelle offline schalten, werden alle Berichte, Modelle und Abonnements erst ausgeführt, wenn Sie die Datenquelle erneut aktivieren.  
  
 Weitere Informationen zum Steuern des Zugriffs auf freigegebene Datenquellen in der Ordnerhierarchie des Berichtsservers finden Sie unter [Sichern freigegebener Datenquellenelemente](../security/secure-shared-data-source-items.md).  
  
## <a name="deleting-a-shared-data-source"></a>Löschen einer freigegebenen Datenquelle  
 Sie können eine freigegebene Datenquelle auf die gleiche Weise löschen wie ein Element auf dem Berichtsserver. Öffnen Sie in Berichts-Manager den Ordner in der Detailansicht, wählen Sie das Element aus, und klicken Sie auf **Löschen**. Öffnen Sie auf einer Anwendungsseite auf einer SharePoint-Website die SharePoint-Bibliothek, wählen Sie das Element aus, und klicken Sie auf **Löschen**.  
  
 Das Löschen der freigegebenen Datenquelle deaktiviert alle Berichte, Modelle und datengesteuerten Abonnements, die sie verwenden. Ohne die Verbindungsinformationen für die Datenquelle werden die Elemente nicht mehr ausgeführt. Zum Aktivieren dieser Elemente müssen Sie jedes Element einzeln öffnen und wie folgt vorgehen:  
  
-   Für Berichte und datengesteuerte Abonnements, die auf die freigegebene Datenquelle verweisen, können Sie die Verbindungsinformationen für die Datenquelle in Berichtseigenschaften oder Abonnements angeben, oder Sie können eine neue freigegebene Datenquelle auswählen, die die Werte, die Sie verwenden möchten, enthält.  
  
-   Für Modelle und Berichts-Generator-Berichte, die dieses Modell verwenden, müssen Sie eine neue freigegebene Datenquelle angeben. Modelle erhalten Verbindungsinformationen für die Datenquelle nur über freigegebene Datenquellen.  
  
 Um eine Liste der Berichte und Modelle anzuzeigen, die die Datenquelle verwenden, öffnen Sie die Seite Abhängige Elemente für die freigegebene Datenquelle. Um auf diese Seite zuzugreifen, öffnen Sie die Datenquelle im Berichts-Manager oder auf einer SharePoint-Anwendungsseite. Beachten Sie, dass die Seite Abhängige Elemente keine datengesteuerten Abonnements anzeigt. Wenn eine freigegebene Datenquelle von einem Abonnement verwendet wird, wird das Abonnement nicht in der Liste der abhängigen Elemente aufgeführt.  
  
 Das Löschen einer freigegebenen Datenquelle lässt sich nicht rückgängig machen. Wenn Sie versehentlich eine freigegebene Datenquelle löschen, können Sie eine neue Datenquelle mit denselben Eigenschaftswerten erstellen. Sie müssen jeden einzelnen Bericht, jedes Modell und jedes datengesteuerte Abonnement öffnen, um die freigegebene Datenquelle erneut mit dem Element zu verbinden, das die Datenquelle verwendet. Solange die Datenquelleneigenschaften gleich bleiben, funktionieren die Berichte, Modelle und Abonnements jedoch weiterhin wie zuvor.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von freigegebenen Datenquellen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Verwalten von Berichtsdatenquellen](manage-report-data-sources.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Die Eigenschaften Seite "Datenquellen" &#40;Berichts-Manager&#41;](../data-sources-properties-page-report-manager.md)   
 [Erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Konfigurieren von Datenquellen Eigenschaften für einen Bericht &#40;Berichts-Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md)  
  
  
