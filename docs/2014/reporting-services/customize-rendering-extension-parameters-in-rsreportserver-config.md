---
title: Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- configuration options [Reporting Services]
- DeviceInfo settings
- rendering extensions [Reporting Services], overriding behaviors
- parameters [Reporting Services], report rendering
- overriding report rendering behavior
- extensions [Reporting Services], rendering
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 83f12c0641768722156322e6e5a655b9e5e5a88b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220930"
---
# <a name="customize-rendering-extension-parameters-in-rsreportserverconfig"></a>Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config
  Sie können in der RSReportServer-Konfigurationsdatei Parameter für Renderingerweiterungen angeben, um das standardmäßige Rendern von Berichten zu überschreiben, die auf einem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver ausgeführt werden. Sie können die Parameter für Renderingerweiterungen ändern, um Folgendes zu bewirken:  
  
-   Ändern der Anzeige des Renderingerweiterungsnamens in der Exportliste der Berichtssymbolleiste (z. B. Ändern von "Webarchiv" in "MHTML") oder Lokalisieren des Namens in eine andere Sprache.  
  
-   Erstellen mehrerer Instanzen derselben Renderingerweiterung, um verschiedene Berichtspräsentationsoptionen zu unterstützen (z. B. Darstellung einer Bildrenderingerweiterung im Hoch- und im Querformat).  
  
-   Ändern der standardmäßigen Renderingerweiterungsparameter, um verschieden Werte zu verwenden (beispielsweise wird für die Bildrenderingerweiterung TIFF als Standardausgabeformat verwendet; sie können die Erweiterungsparameter so ändern, dass stattdessen EMF verwendet wird).  
  
 Eine Änderung der Parameter für Renderingerweiterungen wirkt sich nur auf die Renderingvorgänge auf dem Berichtsserver aus. Sie können die Renderingerweiterungseinstellungen in der Berichtsvorschau im Berichts-Designer nicht überschreiben.  
  
 Die Angabe von Parametern für Renderingerweiterungen in den Konfigurationsdateien wirkt sich global auf Renderingerweiterungen aus. Die Einstellungen in den Konfigurationsdateien werden bei Verwendung einer bestimmten Renderingerweiterung statt der Standardwerte verwendet. Wenn Sie Renderingerweiterungsparameter für einen bestimmten Bericht oder Rendervorgang festlegen möchten, müssen Sie die Geräteinformationen entweder programmgesteuert mithilfe der <xref:ReportExecution2005.ReportExecutionService.Render%2A> -Methode angeben oder durch Angabe der Geräteinformationseinstellungen für eine Berichts-URL. Weitere Informationen zum Angeben von Geräteinformationseinstellungen für einen Rendervorgang und zum Anzeigen der vollständigen Liste der Geräteinformationseinstellungen finden Sie unter [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="finding-and-modifying-rsreportserverconfig"></a>Suchen und Ändern von RSReportServer.config  
 Konfigurationseinstellungen für Berichtsausgabeformate werden als Renderingerweiterungsparameter in der Datei RSReportServer.config angegeben. Wenn Sie Parameter für Renderingerweiterungen in den Konfigurationsdateien angeben möchten, müssen Sie wissen, wie die XML-Strukturen definiert werden, die Renderingparameter festlegen. Es stehen zwei XML-Strukturen zur Verfügung, die geändert werden können:  
  
-   Die `OverrideNames` -Element definiert den Anzeigenamen und die Sprache der Renderingerweiterung.  
  
-   Die `DeviceInfo` XML-Struktur definiert die Einstellungen der Geräteinformationen, die von einer Renderingerweiterung verwendet werden. Die meisten Parameter für Renderingerweiterungen werden als Geräteinformationseinstellungen angegeben.  
  
 Sie können die Datei mithilfe eines Text-Editors ändern. Die Datei RSReportServer.config befindet sich im Ordner \Reporting Services\Report Server\Bin. Weitere Informationen zum Ändern von Konfigurationsdateien finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei (RSreportserver.config)](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="changing-the-display-name"></a>Ändern des Anzeigenamens  
 Der Anzeigename für eine Renderingerweiterung wird in der Exportliste der Berichtssymbolleiste angezeigt. Zu den Standardanzeigenamen gehören unter anderem Webarchiv, TIFF-Datei und Acrobat-Datei (PDF-Datei). Sie können den Standardanzeigenamen durch einen benutzerdefinierten Wert ersetzen, durch Angabe der `OverrideNames` Element in der Konfigurationsdatei. Darüber hinaus können Sie das `OverrideNames`-Element verwenden, um die einzelnen Instanzen in der Exportliste voneinander zu unterscheiden, wenn Sie zwei Instanzen für eine einzelne Renderingerweiterung definieren.  
  
 Da die Anzeigenamen lokalisiert werden, müssen Sie festlegen der `Language` Attribut, wenn Sie den Standardanzeigenamen durch einen benutzerdefinierten Wert ersetzen. Andernfalls werden die von Ihnen angegebenen Namen ignoriert. Der von Ihnen festgelegte Sprachwert muss für den Berichtsservercomputer gültig sein. Wenn der Berichtsserver beispielsweise mit einem französischen Betriebssystem ausgeführt wird, sollten Sie als Attributwert "fr-FR" angeben.  
  
 Im folgenden Beispiel wird dargestellt, wie Sie einen benutzerdefinierten Namen auf einem englischen Berichtsserver bereitstellen:  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## <a name="changing-device-information-settings"></a>Ändern der Geräteinformationseinstellungen  
 Wenn Sie die standardmäßigen Geräteinformationseinstellungen ändern möchten, die von einer bereits auf dem Berichtsserver bereitgestellten Renderingerweiterung verwendet werden, müssen Sie die `DeviceInfo`-XML-Struktur in die Konfigurationsdateien eingeben. Jede Renderingerweiterung unterstützt Geräteinformationseinstellungen, die für die jeweilige Erweiterung eindeutig sind. Die vollständige Liste der Geräteinformationseinstellungen finden Sie unter [übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
 Im folgenden Beispiel wird die XML-Struktur und -Syntax veranschaulicht, mit der die Standardeinstellungen für die Bildrenderingerweiterung geändert werden:  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="configuring-multiple-entries-for-a-rendering-extension"></a>Konfigurieren mehrerer Einträge für eine Renderingerweiterung  
 Sie können mehrere Instanzen derselben Renderingerweiterung erstellen, damit verschiedene Berichtspräsentationsoptionen unterstützt werden. Die von Ihnen definierten Instanzen können verschiedene Kombinationen der Parameterwerte aufweisen. Stellen Sie beim Definieren neuer Instanzen einer vorhandenen Renderingerweiterung Folgendes sicher:  
  
-   Geben Sie einen eindeutigen Namen für die Erweiterung an.  
  
     Jede Instanz müssen einen eindeutigen Wert für die `Name` Attribut. Im folgenden Beispiel werden die Namen "IMAGE (EMF Landscape)" und "IMAGE (EMF Portrait)" verwendet, um die beiden Instanzen voneinander unterscheiden zu können.  
  
     Gehen Sie beim Ändern des Namens für eine bereits bereitgestellte Renderingerweiterung mit Bedacht vor. Entwickler, die Renderingerweiterungen programmgesteuert angeben, verwenden den Erweiterungsnamen zur Identifizierung der für einen bestimmten Rendervorgang zu verwendenden Instanz. Stellen Sie sicher, dass der Entwickler informiert wird, sobald Sie einen vorhandenen Erweiterungsnamen ändern oder einen neuen hinzufügen, wenn Sie eine benutzerdefinierte [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Anwendung auf Ihrem Berichtsserver ausführen.  
  
-   Geben Sie einen eindeutigen Anzeigenamen an, damit Benutzer die Unterschiede zwischen den einzelnen Ausgabeformaten nachvollziehen können.  
  
     Wenn Sie mehrere Versionen derselben Erweiterung konfigurieren, Sie können jede Version einen eindeutigen Namen zuweisen durch Angeben eines Werts für `OverrideNames`. Andernfalls weisen alle Versionen der Erweiterung in der Exportoptionenliste auf der Berichtssymbolleiste denselben Namen auf.  
  
 Im folgenden Beispiel wird die Verwendung der standardmäßigen Bildrenderingerweiterung veranschaulicht (wobei das Ausgabeformat TIFF erstellt wird), um die EMF im Hochformat auszugeben, sowie eine zweite Instanz, mit der Berichte als EMF im Querformat ausgegeben werden. Beachten Sie, dass die einzelnen Erweiterungsnamen eindeutig sind. Achten Sie beim Testen dieses Beispiels darauf, dass Sie Berichte auswählen, die keine interaktiven Funktionen wie Optionen zum Ein- und Ausblenden, Matrizen oder Drillthroughlinks enthalten (interaktive Funktionen können in Bildrenderingerweiterungen nicht ausgeführt werden).  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md)   
 [RSReportDesigner-Konfigurationsdatei](report-server/rsreportdesigner-configuration-file.md)   
 [CSV Device Information Settings (CSV-Geräteinformationseinstellungen)](csv-device-information-settings.md)   
 [Excel Device Information Settings (Geräteinformationseinstellungen für Excel)](excel-device-information-settings.md)   
 [HTML-Geräteinformationseinstellungen](html-device-information-settings.md)   
 [Geräteinformationseinstellungen für Bilder](image-device-information-settings.md)   
 [Geräteinformationseinstellungen für MHTML](mhtml-device-information-settings.md)   
 [PDF Device Information Settings (PDF-Geräteinformationseinstellungen)](pdf-device-information-settings.md)   
 [XML Device Information Settings (XML-Geräteinformationseinstellungen)](xml-device-information-settings.md)  
  
  
