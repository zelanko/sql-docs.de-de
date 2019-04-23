---
title: Hochladen von Dokumenten in einer SharePoint-Bibliothek (Reporting Services im SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 83d04d6f8bb5b9c0701df3e6ba0d2c498cd2d5ea
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59960286"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a>Hochladen von Dokumenten in eine SharePoint-Bibliothek (Reporting Services im SharePoint-Modus)
  Sie können Berichtsdefinitionen und Berichtsmodelle in eine SharePoint-Bibliothek hochladen. Beim Hochladen eines Berichtsserverelements müssen Sie eine Bibliothek oder einen Ordner innerhalb der Bibliothek auswählen. Sie können ein Berichtsserverelement nicht in eine Liste oder auf eine Seite hochladen.  
  
 Sie können keine Datenquellendatei (.rds) hochladen. Sie können RDS-Dateien jedoch aus einem Designtool wie dem Berichts-Designer in eine SharePoint-Bibliothek hochladen. Während der Veröffentlichung wird aus der ursprünglichen RDS-Datei im Projekt eine neue RSDS-Datei erstellt. Sie können auch eine neue RSDS-Datei in einer SharePoint-Bibliothek erstellen und Datenquellen-Verbindungseigenschaften in den hochgeladenen Berichten und Modellen festlegen, um die neue Verbindung zu verwenden.  
  
> [!NOTE]  
>  Der Berichtsserver muss für den SharePoint-Modus konfiguriert sein, und die Instanz des SharePoint-Produkts muss über das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In verfügen, das Programmdateien zum Speichern und Aufrufen von Berichtsserverelementen über eine SharePoint-Website bereitstellt.  
  
 Sie müssen auf der Websiteebene über die Berechtigung zum Hinzufügen von Elementen verfügen, um ein Dokument in eine Bibliothek hochzuladen. Wenn Sie Standardsicherheitseinstellungen verwenden, wird diese Berechtigung Mitgliedern der Gruppe **Besitzer** erteilt, die über Berechtigungen für den Vollzugriff verfügen, und der Gruppe **Mitglieder** , die über Berechtigungen vom Typ Teilnahme verfügen.  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a>So fügen Sie einer Bibliothek eine Berichtsdefinition oder ein Berichtsmodell hinzu  
  
1.  Öffnen Sie die Bibliothek oder einen Ordner innerhalb einer Bibliothek. Wenn die Bibliothek nicht bereits geöffnet ist, klicken Sie auf ihren Namen auf der Schnellstartleiste. Wenn der Name der Bibliothek nicht angezeigt wird, klicken Sie auf **Alle Websiteinhalte einblenden**und anschließend auf den Namen der Bibliothek.  
  
2.  Klicken Sie im Menü **Upload** auf **Dokumentupload**.  
  
3.  Wählen Sie eine Berichtsdefinition (RDL-Datei) oder ein Berichtsmodell (SMDL-Datei) aus, und klicken Sie anschließend auf **OK**, um einen einzelnen Bericht oder eine einzelne Berichtsmodelldatei hochzuladen.  
  
     Wenn für die Berichtsdefinition eine freigegebene Datenquelldatei (RSDS-Datei) verwendet wird, um Verbindungsinformationen für eine externe Datenquelle zu speichern, können Sie die RDL- und die RSDS-Dateien gleichzeitig hochladen. Klicken Sie dazu auf **Mehrere Dokumente hochladen**, geben Sie beide Dateien an, und klicken Sie anschließend auf **OK**.  
  
 Wenn Sie einen Bericht hochladen, der Verweise auf freigegebene Datenquellen, Berichtsmodelle oder Unterberichte enthält, werden die Verweise im Bericht zerstört, wenn die Dateien hochgeladen werden. Weitere Informationen zum Zurücksetzen der Verweise finden Sie unter [Erstellen und Verwalten von freigegebenen Datenquellen (Reporting Services im integrierten SharePoint-Modus)](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
 Wenn Sie einen Bericht hochladen, wird er bei Bedarf während des Öffnens ausgeführt. Gleichzeitig werden Livedaten aus der Datenquelle abgerufen. Sie können den Bericht so konfigurieren, dass Daten nach einem Zeitplan abgerufen werden oder dass zwischengespeicherte Daten verwendet werden. Weitere Informationen finden Sie unter [Festlegen von Verarbeitungsoptionen (Reporting Services im integrierten SharePoint-Modus)](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
 Ein Bericht kann Parameter enthalten, sodass die Benutzer Daten filtern können. Sie können die Parameter so konfigurieren, dass bestimmte Werte verwendet werden. Zudem können Sie die Art der Darstellung der Parameter für die Benutzer ändern. Weitere Informationen finden Sie unter [Festlegen von Parametern für einen veröffentlichten Bericht (Reporting Services im integrierten SharePoint-Modus)](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen eines Berichts in einer SharePoint-Bibliothek](reports/publish-a-report-to-a-sharepoint-library.md)   
 [Veröffentlichen einer freigegebenen Datenquelle in einer SharePoint-Bibliothek](reports/publish-a-shared-data-source-to-a-sharepoint-library.md)   
 [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
