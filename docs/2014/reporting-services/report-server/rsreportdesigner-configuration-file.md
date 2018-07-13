---
title: RSReportDesigner-Konfigurationsdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], configuration file
- RSReportDesigner configuration file
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
caps.latest.revision: 47
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9a19c05387c61e96573ec9525d8e0cab2eb7c8ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255552"
---
# <a name="rsreportdesigner-configuration-file"></a>RSReportDesigner-Konfigurationsdatei
  In der Datei RSReportDesigner.config werden Einstellungen zu Rendering- und Datenverarbeitungserweiterungen gespeichert, die in Berichts-Designer verfügbar sind. Informationen zu datenverarbeitungserweiterungen befindet sich in der `Data` Element. Die Informationen zu Renderingerweiterungen werden im `Render`-Element gespeichert. Das `Designer`-Element zählt die in Berichts-Designer verwendeten Abfrage-Generatoren auf.  
  
 Berichts-Designer verwendet integrierte Berichtsserverfunktionen für die Berichtsvorschau. Zur Unterstützung der lokalen serverseitigen Verarbeitung für Vorschauvorgänge können serverbezogene Einstellungen angegeben werden. Weitere Informationen zu Konfigurationseinstellungen für Berichtsserver, finden Sie unter [RSReportServer-Konfigurationsdatei](rsreportserver-config-configuration-file.md).  
  
## <a name="file-location"></a>Dateispeicherort  
 Diese Datei befindet sich unter \Programme\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies.  
  
## <a name="editing-guidelines"></a>Bearbeitungsrichtlinien  
 Ändern Sie die Einstellungen in dieser Datei nur, wenn Sie eine benutzerdefinierte Erweiterung bereitstellen bzw. entfernen, das Zwischenspeichern während der Vorschau deaktiviert haben oder nach einem Service Pack-Upgrade eine neue Datenverarbeitungserweiterung registrieren.  
  
 Wenn Sie Renderingerweiterungseinstellungen anpassen, sind spezifische Anweisungen zum Bearbeiten von Konfigurationsdateien verfügbar. Weitere Informationen finden Sie unter [Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.Config](../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
 Allgemeine Anleitungen zum Bearbeiten von Konfigurationsdateien finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei („RSreportserver.config“)](modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="example-configuration-file"></a>Beispiel für eine Konfigurationsdatei  
 Das folgende Beispiel veranschaulicht das Format der Datei RSReportDesigner.config.  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## <a name="configuration-settings"></a>Konfigurationseinstellungen  
  
|Einstellung|Description|  
|-------------|-----------------|  
|`SecureConnectionLevel`|Der Sicherheitsgrad der Webdienstverbindung. Gültige Werte sind 0 bis 3, wobei 0 die geringste Sicherheit bietet. Weitere Informationen finden Sie unter [Using Secure Web Service Methods](../report-server-web-service/net-framework/using-secure-web-service-methods.md).|  
|`InstanceName`|Ein Bezeichner für den Vorschauserver. Ändern Sie diesen Wert nicht.|  
|`SessionCookies`|Gibt an, ob der Berichtsserver Sitzungsinformationen mithilfe von Browsercookies verwaltet. Gültige Werte sind `true` und `false`. Der Standardwert ist `true`. Wenn Sie diesen Wert auf false festlegen, werden Sitzungsdaten in der **reportservertempdb** -Datenbank gespeichert.|  
|`SessionTimeoutMinutes`|Gibt an, für welchen Zeitraum ein Sitzungscookie gültig ist. Der Standardwert ist 3 Minuten.|  
|`PolicyLevel`|Gibt die Sicherheitsrichtlinien-Konfigurationsdatei an. Der gültige Wert ist Rspreviewpolicy.config. Weitere Informationen finden Sie unter [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).|  
|`CacheDataForPreview`|Bei Festlegung auf `True`, speichert Berichts-Designer Daten in einer Cachedatei auf dem lokalen Computer. Gültige Werte sind `True` (Standard) und `False`. Weitere Informationen finden Sie unter [Previewing Reports](../reports/previewing-reports.md).|  
|`Render`|Zählt die Renderingerweiterungen auf, die für Berichts-Designer zur Vorschau verfügbar sind. Die für die Vorschau verwendeten Renderingerweiterungen sollten mit den Renderingerweiterungen identisch sein, die mit dem Berichtsserver installiert werden.<br /><br /> `Name` Gibt die Renderingerweiterung an. Wenn Sie eine Renderingerweiterung per Code aufrufen, verwenden Sie diesen Wert zur Angabe einer bestimmten Erweiterung.<br /><br /> `Type` Gibt an, den vollqualifizierten Namen der Erweiterungsklasse sowie den Namen der Bibliothek, durch Trennzeichen getrennte.<br /><br /> `Visible` gibt an, ob der Name auf einer Benutzeroberfläche angezeigt wird. Dieser Wert kann sein `True` (Standard) oder `False`. Bei `True` wird der Name auf Benutzeroberflächen angezeigt.|  
|`Data`|Zählt die Datenverarbeitungserweiterungen auf, die für Berichts-Designer zum Herstellen einer Verbindung zu Datenquellen verfügbar sind, die wiederum Daten für Berichte bereitstellen. Die in Berichts-Designer verwendeten Datenverarbeitungserweiterungen sollten mit den Datenverarbeitungserweiterungen identisch sein, die mit dem Berichtsserver installiert werden. Wenn Sie hinzufügen oder Entfernen benutzerdefinierter Erweiterungen, finden Sie unter [Bereitstellen einer Datenverarbeitungserweiterung](../extensions/data-processing/deploying-a-data-processing-extension.md).<br /><br /> `Name` gibt die Datenverarbeitungserweiterung an.<br /><br /> `Type` Gibt an, den vollqualifizierten Namen der Erweiterungsklasse sowie den Namen der Bibliothek, durch Trennzeichen getrennte.|  
|`Designer`|Zählt die Abfrage-Generatoren auf, die für Berichts-Designer verfügbar sind. Abfrage-Generatoren bieten eine Benutzeroberfläche zum Erstellen von Abfragen, die in Berichten verwendete Daten abrufen. Die Abfrage-Generatoren für verschiedene Datenverarbeitungserweiterungen können voneinander abweichen. Standardmäßig bietet Reporting Services eine grafische Datentool-Benutzeroberfläche für alle Datenverarbeitungserweiterungen, die im Lieferumfang des Produkts enthalten sind. Wenn Sie allerdings Datenverarbeitungsanwendungen erstellen oder Datenverarbeitungsanwendungen von Drittanbietern verwenden, werden möglicherweise andere Abfrage-Generator-Oberflächen angewendet.|  
|`PreviewProcessingServiceStartupTimeoutSeconds`|Gibt den Zeitraum an, der auf das Starten des Vorschauverarbeitungsdienst gewartet wird, bevor eine Fehlermeldung angezeigt wird. Der Standardwert ist 15 Sekunden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurationsdateien](reporting-services-configuration-files.md)   
 [Abfrageentwurfstools im Berichts-Designer SQL-Server-Datatools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)  
  
  
