---
title: Veröffentlichen von Berichten auf einem Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5c73e75bbdf458b27d0f879a91e72ececc832b88
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66102486"
---
# <a name="publishing-reports-to-a-report-server"></a>Veröffentlichen von Berichten auf einem Berichtsserver
  Nachdem Sie entworfen und einen Bericht getestet haben oder Reihe von Berichten, Sie die integrierten Bereitstellungsfunktionen in können [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] um die Berichte auf einem Berichtsserver veröffentlichen. Sie können einzelne Berichte oder ein Berichtsserverprojekt veröffentlichen. Die einfachste Möglichkeit zum Veröffentlichen mehrerer Berichte ist die Veröffentlichung eines Berichtsserverprojekts. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verwendet den Begriff *bereitstellen*, anstatt den Begriff *veröffentlichen*. Die beiden Begriffe sind austauschbar.  
  
 Zum Veröffentlichen eines Berichts benötigen Sie die entsprechende Berechtigung. Die Berechtigung wird durch rollenbasierte Sicherheit bestimmt, die vom Berichtsserveradministrator definiert wird. Berechtigungen für Veröffentlichungsvorgänge werden in der Regel über die Verleger-Rolle gewährt.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] stellt Projektkonfigurationen für die Verwaltung der Berichtsveröffentlichung bereit. Die Konfiguration gibt den Speicherort des Berichtsservers und die Version der auf dem Berichtsserver installierten SQL Server Reporting Services an; weiter legt sie fest, ob die auf dem Berichtsserver veröffentlichten Datenquellen überschrieben werden usw. Zusätzlich zur Verwendung der von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] bereitgestellten Konfigurationen können Sie zusätzliche Konfigurationen erstellen.  
  
## <a name="project-configurations"></a>Projektkonfigurationen  
 Berichte werden vor der Veröffentlichung erstellt, um sicherzustellen, dass nur gültige Berichtsdefinitionen auf dem Berichtsserver veröffentlicht werden. Projektkonfigurationen schließen Eigenschaften zum Erstellen von Berichten ein, z. B. den Ordner, in dem die erstellten Berichte vorübergehend gespeichert werden, und die Behandlung von Erstellungsproblemen. Die Konfigurationen verfügen außerdem über Eigenschaften, mit denen Sie den Speicherort und die Version des Berichtsservers und die Ordner auf dem Berichtsserver angeben.  
  
 In der Standardeinstellung [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] stellt die drei Projektkonfigurationen bereit: DebugLocal, Debug und Release. Die Standardkonfiguration ist DebugLocal. Mit der DebugLocal-Konfiguration können Sie Berichte in der Regel in einem lokalen Vorschaufenster anzeigen, mit der Debug-Konfiguration können Sie Berichte auf einem Testserver veröffentlichen, und mit der Release-Konfiguration veröffentlichen Sie Berichte auf einem Produktionsserver. Die aktive Konfiguration wird auf der Standardsymbolleiste in der Dropdownliste Projektmappenkonfigurationen angezeigt. Wenn Sie eine andere Konfiguration verwenden möchten, wählen Sie sie aus der Liste aus.  
  
 Die Berichterstellungsumgebung kann mehrere Berichtsserver und verschiedene Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aufweisen. Sie können mehrere Konfigurationen erstellen und dann je nach Bereitstellungsszenario eine andere verwenden. Weitere Informationen finden Sie unter [Bereitstellung und Versionsunterstützung in SQL Server Data Tools &#40;SSRS&#41; ](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) und [Festlegen von Bereitstellungseigenschaften &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).  
  
## <a name="publishing-reports"></a>Veröffentlichen von Berichten  
 Sie können einen einzelnen Bericht oder ein Berichtsserverprojekt veröffentlichen, das mehrere Berichte enthält. Anweisungen zum Veröffentlichen von Berichten finden Sie [Berichte veröffentlichen](../publish-reports.md).  
  
### <a name="publishing-a-single-report"></a>Veröffentlichen eines einzelnen Berichts  
 Wenn Sie nicht alle Berichte in einem Projekt veröffentlichen möchten, können Sie einen einzelnen Bericht veröffentlichen. Wählen Sie dazu eine Konfiguration aus, durch die der Bericht bereitgestellt wird (z.B. die Release-Konfiguration), klicken Sie mit der rechten Maustaste auf den Bericht, und klicken Sie dann auf **Bereitstellen**.  
  
 Wenn ein Bericht eine freigegebene Datenquelle verwendet, müssen Sie ebenfalls die freigegebene Datenquelle bereitstellen, oder der bereitgestellte Bericht wird nicht ausgeführt. Klicken Sie mit der rechten Maustaste auf die freigegebene Datenquelle, und klicken Sie dann auf **Bereitstellen**.  
  
 Die Zielserver-URL des Berichtsservers muss angegeben werden. Zudem können Sie die Standardordner ändern, in denen Berichte und freigegebene Datenquellen bereitgestellt werden.  
  
### <a name="publishing-multiple-reports"></a>Veröffentlichen mehrerer Berichte  
 Wenn Sie ein Berichtsserverprojekt veröffentlichen, werden alle Berichte in diesem Projekt veröffentlicht. Alle Berichte werden mithilfe derselben Projektkonfiguration bereitgestellt: auf demselben Berichtsserver, im selben Ordner auf dem Server usw. Zur Veröffentlichung von Berichten auf verschiedenen Servern veröffentlichen Sie sie entweder nacheinander oder schließen nur die gewünschten Berichte in das Berichtsserverprojekt ein. Eine Projektmappe kann mehrere Berichtsserverprojekte enthalten. Die Verwendung mehrerer Projekte erleichtert zudem die Verwaltung der Berichtsbereitstellung, weil Sie zur Bereitstellung unterschiedlicher Projekte jeweils eine andere Konfiguration verwenden können.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaftsseiten für Projekt (Dialogfeld)](../tools/project-property-pages-dialog-box.md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../report-server/report-server-content-management-ssrs-native-mode.md)   
 [Aktualisieren von Berichten](../install-windows/upgrade-reports.md)  
  
  
