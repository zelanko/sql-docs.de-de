---
title: Sichern freigegebener Datenquellenelemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
- security [Reporting Services], data sources
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6b159467fc511292ecb1ae3832a04c73dabdd251
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009642"
---
# <a name="secure-shared-data-source-items"></a>Sichern freigegebener Datenquellenelemente
  Sie können ein freigegebenes Datenquellenelement sichern, um den Zugriff darauf zu aktivieren bzw. zu deaktivieren.  
  
 Ein Benutzer mit dem Mindestzugriffsrecht für eine freigegebene Datenquelle (z.B. der Zugriff über die **Browser** -Rolle) kann die Liste der Berichte anzeigen, die das Element verwenden, vorausgesetzt der Benutzer hat auch die Berechtigung zum Anzeigen der Berichte selbst.  
  
 Ein Benutzer mit zusätzlichen Zugriffsrechten (z.B. über die **Inhalts-Manager** -Rolle) kann Eigenschaften für die freigegebene Datenquelle anzeigen und festlegen.  
  
 Zum Festlegen der Sicherheit erstellen Sie eine Rollenzuweisung, die angibt, welches Benutzer- oder Gruppenkonto Zugriff auf die freigegebene Datenquelle hat. Benutzer mit Zugriff auf ein freigegebenes Datenquellenelement können dessen Namen, Beschreibung, Verbindungszeichenfolge oder Anmeldeinformationen ändern.  
  
## <a name="tasks-and-access-to-items"></a>Aufgaben und Zugriffsrechte für Elemente  
 Beim Erstellen von Rollenzuweisungen sollten Sie eine Rolle verwenden, die die folgenden Aufgaben einschließt, um den Benutzern und Gruppen die geeigneten Berechtigungen zuzuweisen.  
  
|Verwendete Aufgabe|Berechtigt zu folgender Aktion|  
|----------------------|---------------------------------|  
|Datenquellen anzeigen|Anzeigen des freigegebenen Datenquellenelements in der Ordnerhierarchie. Ohne diese Aufgabe ist das Element für die Benutzer nicht sichtbar, und sie wissen möglicherweise nicht, dass die Datenquelle verfügbar ist.|  
|Datenquellen verwalten|Anzeigen von Eigenschaften, die den Namen, eine Beschreibung und Verbindungsinformationen angeben. Mit dieser Aufgabe wird auch ein freigegebenes Datenquellenelement in der Ordnerhierarchie angezeigt. Wenn Sie diese Aufgabe auswählen, können Sie die Aufgabe "Datenquellen anzeigen" auslassen.|  
|Die Sicherheit für einzelne Elemente festlegen|Erstellen und Ändern von Rollenzuweisungen, die den Zugriff auf die freigegebene Datenquelle steuern. Diese Aufgabe muss zusammen mit Datenquellen anzeigen oder Datenquellen verwalten verwendet werden. Andernfalls zeigt sie keine Wirkung, weil der Benutzer das Element nicht auswählen kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Berichtsdatenquellen](../report-data/manage-report-data-sources.md)   
 [Sichere Ordner](secure-folders.md)   
 [Sichere Berichte und Ressourcen](secure-reports-and-resources.md)   
 [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](granting-permissions-on-a-native-mode-report-server.md)   
 [Speichern von Anmeldeinformationen in einer Reporting Services-Datenquelle](../report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  
