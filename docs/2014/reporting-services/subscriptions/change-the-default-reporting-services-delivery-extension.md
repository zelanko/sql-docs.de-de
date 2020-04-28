---
title: Ändern der Standardübermittlungserweiterung für Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a92d967e0b37f1143c9fd37a0d5ee8154ac21db
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177120"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a>Ändern der Standardübermittlungserweiterung für Reporting Services
  Sie können [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Konfigurationseinstellungen ändern, um die Standardübermittlungserweiterung in der Liste **Übermittelt von** einer Abonnementdefinitionsseite zu ändern. Sie können die Konfiguration z. B. so ändern, dass beim Erstellen eines neuen Abonnements durch den Benutzer standardmäßig eine Dateifreigabeübermittlung statt einer E-Mail-Übermittlung ausgewählt wird. Sie können auch die Reihenfolge der in der Benutzeroberfläche aufgeführten Übermittlungserweiterungen ändern.

 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Einheitlicher Modus | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint-Modus

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthält E-Mail- und Windows-Dateifreigabe-Übermittlungserweiterungen. Ihr Berichtsserver verfügt möglicherweise über zusätzliche Übermittlungserweiterungen, wenn Sie benutzerdefinierte Erweiterungen oder Drittanbietererweiterungen zur Unterstützung der benutzerdefinierten Übermittlung bereitgestellt haben. Die Verfügbarkeit einer Übermittlungserweiterung hängt davon ab, ob sie auf einem Berichtsserver bereitgestellt wurde.

## <a name="default-native-mode-report-server-configuration"></a>Standardkonfiguration für einen Berichtsserver im einheitlichen Modus
 Die Reihenfolge der Übermittlungserweiterungen im Berichts-Manager in der Liste **Übermittelt von** basiert auf der Reihenfolge der Übermittlungserweiterungseinträge in der Datei **RSReportServer.config** . Im folgenden Bild wird E-Mail zuerst in der Liste angezeigt und ist standardmäßig ausgewählt.

 ![Standardliste der Übermittlungserweiterungen](../media/ssrs-default-delivery.png "Standardliste der Übermittlungserweiterungen")

 Im Folgenden ist der Standardabschnitt von **RSReportServer.config** dargestellt, der die Standardübermittlungserweiterung und die Reihenfolge steuert, in der diese im Berichts-Manager angezeigt werden. Beachten Sie, dass die E-Mail in der Datei zuerst angezeigt und als Standard festgelegt wird.

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a>Konfigurieren der Dateifreigabeübermittlung als Standardübermittlungserweiterung im Berichts-Manager

1.  Mit den Schritten in diesem Verfahren können Sie die Konfiguration so ändern, dass die Dateifreigabe-Übermittlung als erste Option in der Benutzeroberfläche aufgeführt wird und Standardauswahl ist.

     Öffnen Sie die Datei RSReportServer.config in einem Text-Editor. Weitere Informationen zur Konfigurationsdatei finden Sie unter [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md). Nach Änderung der Konfiguration sieht die Benutzeroberfläche wie folgt aus:

     ![Geänderte Liste der Übermittlungserweiterungen](../media/ssrs-modified-delivery.png "Geänderte Liste der Übermittlungserweiterungen")

2.  Ändern Sie den Abschnitt DeliveryUI wie folgt und beachten Sie die wichtigsten Änderungen:

    1.  Die FileShare-Erweiterung befindet sich vor der E-Mail-Erweiterung. Dadurch wird die Reihenfolge geändert, in der die Erweiterungen im Berichts-Manager aufgeführt sind.

    2.  Die Dateifreigabeerweiterung enthält das DefaultExtension-Tag `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` , und das Extension-Tag wurde hinzugefügt `</Extension>`.

    3.  Die E-Mail-Erweiterung ist nicht mehr als Standard konfiguriert. `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  Speichern Sie die Konfigurationsdatei.

4.  Innerhalb weniger Minuten wird der Berichtsserver die Konfigurationsdatei laden und die neuen Einstellungen übernehmen. Sie können den Berichtsserverdienst neu starten, um das Laden der Konfigurationsdatei zu erzwingen.

     Das folgende Ereignis wird beim Lesen der Konfiguration im Windows-Ereignisprotokoll geschrieben.

     **Ereignis-ID:** 109

     **Quelle:** Berichtsserver-Windows-Dienst (Instanzname)

     Die Datei „RSReportServer.config“ wurde geändert.

## <a name="sharepoint-mode-report-servers"></a>Berichtsserver im SharePoint-Modus
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint-Modus speichert Erweiterungsinformationen in den SharePoint-Dienstanwendungsdatenbanken, und nicht in der Datei „RsrReportServer.config“. Im SharePoint-Modus wird die Konfiguration für die Übermittlungserweiterung mit PowerShell geändert.

#### <a name="configure-the-default-delivery-extension"></a>Konfigurieren der Standardübermittlungserweiterung

1.  Öffnen Sie die **SharePoint-Verwaltungsshell**.

2.  Sie können diesen Schritt überspringen, wenn Sie den Namen Ihrer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dienstanwendung bereits kennen. Verwenden Sie den folgende PowerShell-Befehl zum Auflisten der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dienstanwendungen in der SharePoint-Farm.

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  Führen Sie den folgenden PowerShell-Befehl zum Überprüfen der aktuellen Standardübermittlungserweiterung für die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dienstanwendung „ssrsapp“ aus.

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a>Weitere Informationen
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md) [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md) [Freigabe Übermittlung in Reporting Services](file-share-delivery-in-reporting-services.md) [e-Mail-Übermittlung in Reporting Services](e-mail-delivery-in-reporting-services.md) [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)
