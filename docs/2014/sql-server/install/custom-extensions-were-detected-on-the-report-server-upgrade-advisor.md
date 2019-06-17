---
title: (Upgrade Advisor) auf dem Berichtsserver wurden benutzerdefinierte Erweiterungen erkannt. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rendering extensions [Reporting Services], custom extensions
- security extensions [Reporting Services]
- custom extensions [Reporting Services]
- data processing extensions [Reporting Services], custom extensions
- delivery extensions [Reporting Services]
ms.assetid: fa184bd7-11d6-4ea3-9249-bc1b13db49e5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 69df18da28672f05099f22821240fdf28e1fb880
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095967"
---
# <a name="custom-extensions-were-detected-on-the-report-server-upgrade-advisor"></a>Auf dem Berichtsserver wurden benutzerdefinierte Erweiterungen erkannt (Upgrade Advisor)
  Upgrade Advisor hat in den Konfigurationsdateien Einstellungen für benutzerdefinierte Erweiterungen gefunden. Dies ist ein Hinweis darauf, dass die Installation mindestens eine benutzerdefinierte Erweiterung zur Datenverarbeitung, Übermittlung, Sicherheit, Authentifizierung oder zum Rendering enthält. Beim Upgrade werden die Erweiterungskonfigurationseinstellungen zusammen mit dem aktualisierten Berichtsserver verschoben. Wenn die benutzerdefinierten Erweiterungen jedoch im vorhandenen Berichtsserver-Installationsordner installiert sind, werden ihre Assemblydateien beim Upgradevorgang nicht in den neuen Installationsordner verschoben. Nach Abschluss des Upgrades müssen Sie die Assemblydateien in den neuen Installationsordner von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verschieben.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** : [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Beschreibung  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet eine erweiterbare Architektur, die Entwicklern ermöglicht, benutzerdefinierte Erweiterungen für Datenverarbeitung, Übermittlung, Rendering, Sicherheit und Authentifizierung zu erstellen.  
  
 Wenn benutzerdefinierte Erweiterungen oder Assemblys in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation verwendet werden, können Sie mit Setup ein Upgrade durchführen. Allerdings müssen Sie möglicherweise nach Abschluss des Upgrades Erweiterungen an den neuen Installationsort verschieben, oder Sie müssen vor dem Upgrade bestimmte Schritte ausführen.  
  
> [!NOTE]  
>  Vom Updateratgeber wird nicht erkannt, ob benutzerdefinierte Code-Assemblys für die Verwendung in Berichten zur Berechnung von Elementwerten, Formaten und Formatierungen konfiguriert sind. Weitere Informationen finden Sie unter [andere Reporting Services Probleme beim Upgrade](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md).  
  
 Wenn Sie benutzerdefinierte Erweiterungen von einem Softwarehersteller erworben haben, bitten Sie den Hersteller um zusätzliche Informationen zum Aktualisieren der benutzerdefinierten Funktionalität.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Bestimmen Sie anhand der folgenden Abschnitte, welche Schritte Sie zusätzlich oder vor dem Upgrade von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ausführen müssen:  
  
 [Benutzerdefinierte datenverarbeitungs- oder übermittlungserweiterungen](#dataprocdeliver)  
  
 [Benutzerdefinierte Renderingerweiterungen](#render)  
  
 [Benutzerdefinierte Sicherheits- oder authentifizierungserweiterungen auf einem SQL Server 2000-Berichtsserver](#secauth2000)  
  
 [Benutzerdefinierte Sicherheits- oder authentifizierungserweiterungen auf einem SQL Server 2005-Berichtsserver](#secauth2005)  
  
 Verschieben Sie nach Abschluss des Upgrades die Erweiterungsassemblys in den neuen Installationsordner, und überprüfen Sie dann, ob die benutzerdefinierten Erweiterungen erwartungsgemäß arbeiten. Wenn die Erweiterung nicht funktioniert, müssen Sie sie unter Umständen neu kompilieren.  
  
#### <a name="to-recompile-an-extension"></a>So kompilieren Sie eine Erweiterung neu  
  
1.  Kopieren Sie die Datei Microsoft.ReportingServices.Interfaces.dll in den Ordner, der den Quellcode enthält.  
  
2.  Öffnen Sie das Projekt, das die Quelldateien enthält, und fügen Sie einen Verweis auf die Datei Microsoft.ReportingServices.Interfaces.dll hinzu.  
  
3.  Erstellen Sie die Lösung neu, um die Erweiterung zu binden.  
  
 Wenn Sie entscheiden, nicht mit dem Upgrade fortzufahren, können Sie entscheiden, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stattdessen zu migrieren. Die Schritte zum Migrieren benutzerdefinierter Erweiterungen finden Sie [migrieren benutzerdefinierter Erweiterungen](#migrcustext) in diesem Thema.  
  
###  <a name="dataprocdeliver"></a> Benutzerdefinierte datenverarbeitungs- oder übermittlungserweiterungen  
 Wenn der Upgrade Advisor benutzerdefinierte Datenverarbeitungs- oder Übermittlungserweiterungen erkennt, wird der Upgradevorgang nicht blockiert. Nach Abschluss des Upgrades müssen Sie jedoch möglicherweise weitere Schritte ausführen, damit die von diesen Erweiterungen bereitgestellte benutzerdefinierte Funktionalität verwendet werden kann. Beispielsweise müssen Sie weitere Schritte ausführen, wenn die Dateien für die benutzerdefinierten Erweiterungen im Installationsordner von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert sind.  
  
##### <a name="post-upgrade-steps-for-custom-data-processing-or-delivery-extensions"></a>Nach dem Upgrade auszuführende Schritte für benutzerdefinierte Datenverarbeitungs- oder Übermittlungserweiterungen  
  
1.  Verschieben Sie die Erweiterungsdatei(en) in den neuen Programmordner für den Berichtsserver. Standardmäßig ist der Berichtsserverordner-Programm unter \Programme\Microsoft SQL Server\MSRS10_50. \< *Instance_name*> \report Server.  
  
 Weitere Informationen finden Sie unter "Bereitstellen einer Datenverarbeitungserweiterung" und "Implementieren von Übermittlungserweiterungen" in der SQL Server-Onlinedokumentation.  
  
###  <a name="render"></a> Benutzerdefinierte Renderingerweiterungen  
 Wenn der Upgrade Advisor benutzerdefinierte Renderingerweiterungen erkennt, wird der Upgradevorgang blockiert. Sie können den Upgradevorgang fortsetzen, indem Sie die Konfigurationseinträge für die benutzerdefinierten Erweiterungen aus der Konfigurationsdatei entfernen. Dann stehen nach Abschluss des Upgrades die benutzerdefinierten Erweiterungen jedoch den Benutzern nicht zur Verfügung. Wenn Sie nach dem Upgrade benutzerdefinierte Renderingerweiterungen benötigen, müssen Sie aktualisierte Renderingerweiterungen erstellen oder von einem entsprechenden Anbieter beziehen.  
  
 Sie müssen Schritte ausführen, um ein Upgrade zu aktivieren, oder Sie können stattdessen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] migrieren.  
  
> [!IMPORTANT]  
>  Aktualisieren oder migrieren Sie Ihren Berichtsserver erst, nachdem Sie getestet und überprüft haben, ob die aktualisierte Renderingerweiterung ordnungsgemäß arbeitet.  
  
##### <a name="to-upgrade-custom-rendering-extensions"></a>So aktualisieren Sie benutzerdefinierte Renderingerweiterungen  
  
1.  Beziehen Sie Renderingerweiterungen mit den aktuellen Schnittstellen.  
  
2.  Entfernen Sie den alten Eintrag bzw. die alten Einträge für benutzerdefinierte Renderingerweiterungen aus RSReportServer.config.  
  
3.  Aktualisieren Sie den Berichtsserver.  
  
4.  Installieren Sie nach Abschluss des Upgrades die aktualisierten Erweiterungen auf dem Berichtsserver.  
  
 Weitere Informationen finden Sie unter "Implementieren von Renderingerweiterungen" in der SQL Server-Onlinedokumentation.  
  
###  <a name="secauth2000"></a> Benutzerdefinierte Sicherheits- oder authentifizierungserweiterungen auf einem SQL Server 2000-Berichtsserver  
 Wenn der Upgrade Advisor benutzerdefinierte Sicherheits- oder Authentifizierungserweiterungen auf einem Berichtsserver von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] erkennt, wird der Upgradevorgang blockiert. Sie müssen Schritte ausführen, um ein Upgrade zu aktivieren, oder Sie können stattdessen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] migrieren. In jedem der beiden Fälle müssen Sie die Erweiterungen anhand der aktuellen Schnittstellen in Microsoft.ReportingServices.Interfaces.dll aktualisieren und neu kompilieren, da die Schnittstellen beim Übergang von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] zu [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] geändert wurden.  
  
> [!IMPORTANT]  
>  Aktualisieren oder migrieren Sie Ihren Berichtsserver erst, nachdem Sie getestet und überprüft haben, ob die aktualisierte Sicherheits- oder Authentifizierungserweiterung ordnungsgemäß arbeitet.  
  
 Wenn Sie eine benutzerdefinierte Authentifizierungserweiterung verwenden, die Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erstellt haben, müssen Sie den Quellcode so ändern, dass er die neuen Klassen und Elemente unterstützt, die für die modellgesteuerte Berichterstellung eingeführt wurden.  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2000-report-server"></a>So aktualisieren Sie die benutzerdefinierte Sicherheits- oder authentifizierungserweiterungen von einem SQL Server 2000-Berichtsserver  
  
1.  Aktualisieren Sie alle Sicherheits- oder Authentifizierungserweiterungen anhand der aktuellen Schnittstellen, und kompilieren Sie sie neu.  
  
2.  Entfernen Sie den Eintrag bzw. die Einträge für Sicherheits- oder Authentifizierungserweiterungen aus RSReportServer.config.  
  
3.  Aktualisieren Sie den Berichtsserver.  
  
4.  Installieren Sie nach Abschluss des Upgrades die aktualisierten Erweiterungen auf dem Berichtsserver.  
  
 Weitere Informationen finden Sie unter "Implementieren von Sicherheitserweiterungen" in der SQL Server-Onlinedokumentation.  
  
###  <a name="secauth2005"></a> Benutzerdefinierte Sicherheits- oder authentifizierungserweiterungen auf einem SQL Server 2005-Berichtsserver  
 Wenn der Upgrade Advisor benutzerdefinierte Sicherheits- oder Authentifizierungserweiterungen auf einem Berichtsserver von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erkennt, wird der Upgradevorgang blockiert. Sie müssen Schritte ausführen, um ein Upgrade zu aktivieren, oder Sie können stattdessen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] migrieren.  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2005-report-server"></a>So aktualisieren Sie Sicherheits- oder Authentifizierungserweiterungen von einem Berichtsserver mit SQL Server 2005  
  
1.  Entfernen Sie die Konfigurationseinträge für Sicherheits- oder Authentifizierungserweiterungen aus RSReportServer.config.  
  
2.  Aktualisieren Sie den Berichtsserver.  
  
3.  Fügen Sie nach dem Abschluss des Upgrades die Konfigurationseinträge wieder in RSReportServer.config hinzu.  
  
4.  Wenn die Erweiterungsassemblys im alten Installationsordner von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert wurden, verschieben Sie sie in den neuen Installationsordner.  
  
 Weitere Informationen finden Sie unter "Implementieren von Sicherheitserweiterungen" in der SQL Server-Onlinedokumentation.  
  
###  <a name="migrcustext"></a> Migrieren benutzerdefinierter Erweiterungen  
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] migrieren möchten, statt ein Upgrade auszuführen, verwenden Sie die Schritte zum Migrieren benutzerdefinierter Erweiterungen zur neuen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Instanz.  
  
##### <a name="to-migrate-custom-extensions-to-a-new-reporting-services-instance"></a>So migrieren Sie benutzerdefinierte Erweiterungen zu einer neuen Reporting Services-Instanz  
  
1.  Erstellen oder beziehen Sie aktualisierte Erweiterungen mit den aktuellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Schnittstellen.  
  
2.  Migrieren Sie den Berichtsserver zu einer neuen Instanz.  
  
3.  Konfigurieren Sie die Erweiterungen für die neue Instanz.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
