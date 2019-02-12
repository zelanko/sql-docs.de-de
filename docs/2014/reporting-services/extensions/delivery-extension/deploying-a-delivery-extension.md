---
title: Bereitstellen von Übermittlungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: 4436ce48-397d-42c7-9b5d-2a267e2a1b2c
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a461f3dfa1dca66efb2708e15f56c7fa30c58dc6
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56037461"
---
# <a name="deploying-a-delivery-extension"></a>Bereitstellen von Übermittlungserweiterungen
  Übermittlungserweiterungen geben ihre Konfigurationsinformationen in Form einer XML-Konfigurationsdatei an. Die XML-Datei entspricht dem für Übermittlungserweiterungen definierten XML-Schema. Übermittlungserweiterungen verfügen über eine Infrastruktur zum Einstellen und Ändern der Konfigurationsdatei.  
  
 Wenn eine Übermittlungserweiterung ersetzt oder aktualisiert wird, bleiben alle Abonnements, die auf die Übermittlungserweiterung verweisen, gültig.  
  
 Nachdem Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung geschrieben und in eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Bibliothek kompiliert haben, müssen Sie die Erweiterung in das entsprechende Verzeichnis kopieren und einen Eintrag in der entsprechenden [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Konfigurationsdatei vornehmen, damit sie vom Berichtsserver gefunden werden kann.  
  
## <a name="configuration-file-extension-element"></a>Extension-Element für die Konfigurationsdatei  
 Übermittlungserweiterungen, die Sie für den Berichtsserver bereitstellen, müssen in der Konfigurationsdatei als `Extension`-Elemente hinzugefügt werden. Die Konfigurationsdatei für den Berichtsserver heißt RSReportServer.config.  
  
 In der folgenden Tabelle werden die Attribute für das `Extension`-Element für Übermittlungserweiterungen beschrieben.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Ein eindeutiger Name für die Erweiterung (z. B. "Berichtsserver-E-Mail" für eine E-Mail-Übermittlungserweiterung oder "Berichtsserver-Dateifreigabe" für eine Dateifreigabe-Übermittlungserweiterung). Die maximale Länge für das `Name`-Attribut beträgt 255 Zeichen. Der Name muss für sämtliche Einträge im `Extension`-Element einer Konfigurationsdatei eindeutig sein. Wenn ein Name doppelt vorhanden ist, gibt der Berichtsserver einen Fehler zurück.|  
|`Type`|Eine durch Trennzeichen getrennte Liste, die den vollqualifizierten Namespace und den Namen der Assembly enthält|  
|`Visible`|Der Wert `false` gibt an, dass die Übermittlungserweiterung auf Benutzeroberflächen nicht sichtbar sein soll. Wenn das Attribut nicht enthalten ist, ist `true` der Standardwert.|  
  
 Weitere Informationen über die Datei „RSReportServer.config“ finden Sie unter [Reporting Services-Konfigurationsdateien](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Bereitstellen der Erweiterung auf dem Berichtsserver  
 Der Berichtsserver verwendet Übermittlungserweiterungen zur Verarbeitung und Übermittlung von Benachrichtigungen oder Berichten. Sie sollten die Assembly für Übermittlungserweiterungen auf dem Berichtsserver als private Assembly bereitstellen. Sie müssen auch einen Eintrag in der Konfigurationsdatei des Berichtsservers RSReportServer.config vornehmen.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-a-report-server"></a>So stellen Sie eine Assembly für Übermittlungserweiterungen auf einem Berichtsserver bereit  
  
1.  Kopieren Sie die Assembly aus dem Bereitstellungsverzeichnis in das BIN-Verzeichnis des Berichtsservers, auf dem Sie die Übermittlungserweiterung verwenden möchten. Der Standardspeicherort des Bin-Verzeichnis des Berichtsservers ist %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \reporting.  
  
    > [!IMPORTANT]  
    >  Wenn Sie versuchen, eine vorhandene Assembly für Übermittlungserweiterungen zu überschreiben, müssen Sie zuerst den Berichtsserverdienst anhalten, bevor Sie die aktualisierte Assembly kopieren können. Starten Sie den Dienst neu, nachdem die Assembly kopiert wurde.  
  
2.  Nachdem die Assemblydatei kopiert wurde, öffnen Sie die Datei RSReportServer.config. Die Datei "rsreportserver.config" befindet sich in %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \reporting-Verzeichnis. Sie müssen einen Eintrag in der Konfigurationsdatei für die Assemblydatei der Übermittlungserweiterung vornehmen. Sie können die Konfigurationsdatei mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] oder in einem einfachen Text-Editor wie Editor öffnen.  
  
3.  Suchen Sie das `Delivery`-Element in der Datei RSReportServer.config. In folgendem Verzeichnis muss ein Eintrag für die neu erstellte Übermittlungserweiterung erstellt werden:  
  
    ```  
    <Extensions>  
       <Delivery>  
          <Your extension configuration information goes here>  
       </Delivery>  
    </Extensions>  
    ```  
  
4.  Fügen Sie einen Eintrag für die Übermittlungserweiterung hinzu. Der Eintrag sollte ein `Extension`-Element mit den Werten für `Name` und `Type` enthalten und kann folgendermaßen aussehen:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryExtensionClass, AssemblyName" />  
    ```  
  
     Der Wert für `Name` ist der eindeutige Name der Übermittlungserweiterung. Der Wert für `Type` ist eine durch Trennzeichen getrennte Liste, die einen Eintrag für den vollqualifizierten Namespace der Klasse enthält, die die Schnittstelle <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> implementiert, gefolgt vom Namen der Assembly (ohne die Dateierweiterung .dll). Übermittlungserweiterungen sind standardmäßig sichtbar. Um eine Erweiterung in Benutzeroberflächen wie dem Berichts-Manager auszublenden, fügen Sie das `Visible`-Attribut zum `Extension`-Element hinzu und setzen es auf `false`.  
  
5.  Zum Schluss müssen Sie eine Codegruppe für die benutzerdefinierte Assembly hinzufügen, die die Berechtigung `FullTrust` für die Übermittlungserweiterung erteilt. Hierzu fügen Sie die Codegruppe zur Datei "rssrvpolicy.config" befindet sich standardmäßig in %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \reporting. Die Codegruppe kann folgendermaßen aussehen:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     Die URL-Mitgliedschaft ist eine der vielen Mitgliedschaftsbedingungen, die Sie für die Übermittlungserweiterung auswählen können. Weitere Informationen zur Codezugriffssicherheit in [!INCLUDE[ssRS](../../../includes/ssrs.md)] finden Sie unter [Sichere Entwicklung (Reporting Services)](../secure-development/secure-development-reporting-services.md).  
  
## <a name="deploying-the-extension-to-report-manager"></a>Bereitstellen der Erweiterung auf dem Berichts-Manager  
 Wenn die Übermittlungserweiterung die Schnittstelle <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> implementiert, kann die Übermittlungserweiterung mit der Seite "Berichtabonnement" verwendet werden. Um die Benutzeroberfläche des Abonnements verfügbar zu machen, müssen Sie die Erweiterung im Berichts-Manager bereitstellen.  
  
#### <a name="to-deploy-a-deliver-extension-assembly-to-report-manager"></a>So stellen Sie eine Assembly für Übermittlungserweiterungen im Berichts-Manager bereit  
  
1.  Kopieren Sie die Assembly aus dem Bereitstellungsverzeichnis in das BIN-Verzeichnis des Berichts-Managers. Der Standardspeicherort des Berichts-Manager-Bin-Verzeichnisses ist %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \Reporting Services\ReportManager\bin.  
  
2.  Nachdem die Assemblydatei kopiert wurde, öffnen Sie die Datei RSReportServer.config. Die Datei "rsreportserver.config" befindet sich in %ProgramFiles%\Microsoft SQL Server\MSRS10_50. \<InstanceName > \reporting-Verzeichnis. Sie müssen einen Eintrag in der Konfigurationsdatei für die Assemblydatei der Übermittlungserweiterung vornehmen. Sie können die Konfigurationsdatei mit Visual Studio .NET oder einem einfachen Texteditor wie Editor öffnen.  
  
3.  Suchen Sie das `DeliveryUI`-Element in der Datei RSReportServer.config. In folgendem Verzeichnis muss ein Eintrag für die neu erstellte Übermittlungserweiterung erstellt werden:  
  
    ```  
    <Extensions>  
       <DeliveryUI>  
          <Your extension configuration information goes here>  
       </DeliveryUI>  
    </Extensions>  
    ```  
  
4.  Fügen Sie einen Eintrag für die Übermittlungserweiterung hinzu. Der Eintrag sollte enthalten eine `Extension` -Element mit den Werten `Name` und `Type` und kann wie folgt aussehen:  
  
    ```  
    <Extension Name="My Delivery Extension Name" Type="CompanyName.ExtensionName.MyDeliveryUIExtensionClass, AssemblyName" />  
    ```  
  
     Der Wert für `Name` ist der eindeutige Name der Übermittlungserweiterung. Der Wert für `Type` ist eine durch Trennzeichen getrennte Liste, die einen Eintrag für den vollqualifizierten Namespace der Klasse enthält, die die Schnittstelle <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> implementiert, gefolgt vom Namen der Assembly (ohne die Dateierweiterung .dll).  
  
    > [!IMPORTANT]  
    >  Der Wert des `Name`-Attributs muss für die Einträge in den beiden Konfigurationsdateien des Berichtsservers und des Berichts-Managers identisch sein. Wenn sie nicht identisch sind, ist die Serverkonfiguration nicht gültig.  
  
     Zum Schluss müssen Sie eine Codegruppe für die benutzerdefinierte Assembly hinzufügen, die die Berechtigung `FullTrust` für die Übermittlungserweiterung erteilt. Hierzu fügen Sie die Codegruppe zur Datei RSmgrpolicy.config befindet sich standardmäßig in c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSRS10_50. \<InstanceName > \Reporting Services\ReportManager. Die Codegruppe kann folgendermaßen aussehen:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my delivery UI extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<InstanceName>\Reporting Services\ReportManager\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
     Die URL-Mitgliedschaft ist eine der vielen Mitgliedschaftsbedingungen, die Sie für die Übermittlungserweiterung auswählen können. Weitere Informationen zur Codezugriffssicherheit in [!INCLUDE[ssRS](../../../includes/ssrs.md)] finden Sie unter [Sichere Entwicklung (Reporting Services)](../secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Überprüfen der Bereitstellung  
 Sie können prüfen, ob die Übermittlungserweiterung erfolgreich auf dem Berichtsserver bereitgestellt wurde, indem Sie die Webdienstmethode <xref:ReportService2010.ReportingService2010.ListExtensions%2A> verwenden. Sie können auch den Berichts-Manager öffnen und prüfen, ob die Erweiterung in der Liste der für ein Abonnement verfügbaren Übermittlungserweiterungen enthalten ist. Weitere Informationen zu Berichts-Manager und Abonnements finden Sie unter [Abonnements und Übermittlung &#40;Reporting Services&#41;](../../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
