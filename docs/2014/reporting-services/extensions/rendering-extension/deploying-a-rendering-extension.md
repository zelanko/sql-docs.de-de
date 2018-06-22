---
title: Bereitstellen von Renderingerweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deploying [Reporting Services], extensions
- rendering extensions [Reporting Services], deploying
ms.assetid: 9fb8c887-5cb2-476e-895a-7b0e2dd11398
caps.latest.revision: 43
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1cd6fb05217c0bde25dcc00e5f520dfd126385ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149347"
---
# <a name="deploying-a-rendering-extension"></a>Bereitstellen von Renderingerweiterungen
  Wenn Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Berichtsrenderingerweiterung geschrieben und in eine [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Bibliothek kompiliert haben, müssen Sie sie für den Berichtsserver und den Berichts-Designer erkennbar machen. Hierzu müssen Sie lediglich die Erweiterung in das entsprechende Verzeichnis kopieren und Einträge zu den zugehörigen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Konfigurationsdateien hinzufügen.  
  
## <a name="configuration-file-rendering-extension-element"></a>Renderingerweiterungselement der Konfigurationsdatei  
 Sobald eine Renderingerweiterung in eine .DLL kompiliert wurde, fügen Sie eine Eintragung in die Datei rsreportserver.config hinzu. Standardmäßig ist der Speicherort „%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instanzname>\Reporting Services\ReportServer“. Das übergeordnete Element ist \<Render>. Unter dem Render-Element befindet sich ein Erweiterungselement für jede Renderingerweiterung. Die `Extension` -Element enthält zwei Attribute: Name und Typ.  
  
 Die folgende Tabelle beschreibt die Attribute für das `Extension` -Element für Renderingerweiterungen zur Verfügung:  
  
|attribute|Description|  
|---------------|-----------------|  
|**Name**|Ein eindeutiger Name für die Erweiterung. Die maximale Länge für das **Name** -Attribut beträgt 255 Zeichen. Der Name muss für sämtliche Einträge im **Extension** -Element einer Konfigurationsdatei eindeutig sein. Wenn ein Name doppelt vorhanden ist, gibt der Berichtsserver einen Fehler zurück.|  
|**Typ**|Eine durch Trennzeichen getrennte Liste, die den vollqualifizierten Namespace und den Namen der Assembly enthält|  
|**Visible**|Der Wert `false` gibt an, dass die Renderingerweiterung auf Benutzeroberflächen nicht sichtbar sein soll. Wenn das Attribut nicht enthalten ist, wird der Standardwert ist `true`.|  
|**LogAllExecutionRequests**|Der Wert `false` gibt an, dass nur für die erste Berichtsausführung in einer Sitzung ein Eintrag protokolliert wird. Wenn das Attribut nicht enthalten ist, wird der Standardwert ist `true`.<br /><br /> Diese Einstellung legt zum Beispiel fest, ob nur für die erste Seite eines Berichts (`false`) oder für alle Seiten eines Berichts ein Eintrag protokolliert werden soll (`true`).|  
  
 Weitere Informationen finden Sie unter [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).  
  
## <a name="deploying-the-extension-to-the-report-server"></a>Bereitstellen der Erweiterung auf dem Berichtsserver  
 Der Berichtsserver exportiert Berichte mithilfe von Renderingerweiterungen in andere Formate. Sie sollten Ihre Assembly für Renderingerweiterungen auf dem Berichtsserver als private Assembly bereitstellen. Sie müssen auch einen Eintrag in der Konfigurationsdatei des Berichtsservers rsreportserver.config vornehmen.  
  
### <a name="to-deploy-the-assembly"></a>So stellen Sie die Assembly bereit  
  
1.  Kopieren Sie die Assembly aus dem Bereitstellungsverzeichnis in das BIN-Verzeichnis des Berichtsservers, auf dem Sie die Renderingerweiterung verwenden möchten. Der standardmäßige Speicherort des Bin-Verzeichnisses des Berichtsservers lautet „%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<InstanceName>\Reporting Services\ReportServer\Bin“.  
  
2.  Nachdem die Assemblydatei kopiert wurde, öffnen Sie die Datei rsreportserver.config. Die Datei rsreportserver.config befindet sich auch im BIN-Verzeichnis des Berichtsservers. Sie müssen einen Eintrag in der Konfigurationsdatei für die Datei Ihrer Erweiterungsassembly vornehmen. Sie können die Datei in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] oder einem einfachen Text-Editor öffnen.  
  
     Weitere Informationen finden Sie unter [RSReportServer Configuration File](../../report-server/rsreportserver-config-configuration-file.md).  
  
3.  Suchen Sie das **Render** -Element in der Datei Rsreportserver.config. Im folgenden Verzeichnis muss ein Eintrag für Ihre neu erstellte Erweiterung erstellt werden:  
  
    ```  
    <Extensions>  
       <Render>  
          <extension configuration>  
       </Render>  
    </Extensions>  
    ```  
  
4.  Fügen Sie einen Eintrag für die Renderingerweiterung hinzu. Der Eintrag sollte ein Element mit Werten für **Name** und **Typ**enthalten und kann folgendermaßen aussehen:  
  
    ```  
    <Extension Name="My Rendering Extension Name" Type="CompanyName.ExtensionName.MyRenderingProvider, AssemblyName" />  
    ```  
  
     Der Wert für **Name** ist ein eindeutiger Name der Renderingerweiterung. Der Wert für **Type** ist eine durch Komma getrennte Liste, die einen Eintrag für den vollqualifizierten Namespace Ihrer <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension>-Implementierung enthält, gefolgt vom Namen Ihrer Assembly (ohne die DLL-Dateierweiterung). Standardmäßig sind Renderingerweiterungen sichtbar. Um eine Erweiterung in Benutzeroberflächen wie dem Berichts-Manager auszublenden Hinzufügen einer **sichtbar** -Attribut auf die `Extension` Element, und legen Sie dafür `false`.  
  
## <a name="verifying-the-deployment"></a>Überprüfen der Bereitstellung  
 Sie können auch den Berichts-Manager öffnen und prüfen, ob die Erweiterung in der Liste der für einen Bericht verfügbaren Exporttypen enthalten ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](implementing-a-rendering-extension.md)   
 [Übersicht über Renderingerweiterungen](rendering-extensions-overview.md)   
 [Implementieren der IRenderingExtension-Schnittstelle](implementing-the-irenderingextension-interface.md)   
 [Security Considerations for Extensions (Überlegungen zur Sicherheit von Erweiterungen)](../security-considerations-for-extensions.md)  
  
  