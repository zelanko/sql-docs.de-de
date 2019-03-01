---
title: Änderungsprotokoll für SQL Server Reporting Services (SSRS) 2017 und höher | Microsoft-Dokumentation
ms.date: 08/31/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: casualoak
ms.author: RhysSchmidtke
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0eec59b0d2618686f866e6b7799922d9c255b238
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56230907"
---
# <a name="change-log-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Änderungsprotokoll für SQL Server Reporting Services (SSRS) 2017 und höher

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)] 

In diesem Artikel werden Änderungen in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben. 

## <a name="sql-server-2017-reporting-services"></a>SQL Server 2017 Reporting Services 

### <a name="version-1406001109-released-february-12-2019"></a>Version 14.0.600.1109, veröffentlicht am 12. Februar 2019

Die folgenden Probleme wurden behoben:

 - Nach Änderung des Abonnements ändern sich die Zeitpläne für Cache-Berichtsmomentaufnahmen in „Berichtsspezifischer Zeitplan“.
 - „rc:Toolbar=false“ funktionierte in der Express-Edition nicht.
 - Bestimmte thailändische Zeichen wurden beim Exportieren paginierter Berichte in PDF nicht ordnungsgemäß gerendert.
 - Deadlock während der Benachrichtigung für abgeschlossene datengesteuerte Abonnements.
 - Eingebettete Bilder wurden in bestimmten Fällen nicht angezeigt, wenn der Parameter „rc: Toolbar=False“ verwendet wurde.
 - Für Berichte mit kaskadierenden Parametern konnten keine datengesteuerten Abonnements erstellt werden.
 - Mit einem ungültigen Intervall konfigurierte Abonnements konnten nicht bearbeitet werden.
 - Sicherheitsupdates
 - Benutzeroberfläche für verknüpfte Berichte wurde nicht angezeigt.
 - Bestimmte paginierte Berichte mit geschachtelten Tablix-Steuerelementen wiesen falsche Schriftarten auf.
 - Bestimmten paginierten Berichten mit Tablix-Datenbereichen wurden fälschlicherweise Leerzeichen hinzugefügt.
 - Kopfzeilen verschwanden beim Erweitern einfacher Datenraster in Mobilgeräteberichten.

### <a name="version-140600906-released-september-12-2018"></a>Version 14.0.600.906, veröffentlicht am 12. September 2018

Das folgende Problem wurde behoben:

- Benutzerdefinierte Authentifizierung, die keine richtigen Cookieinformationen zurückgibt

### <a name="version-140600892-released-august-31-2018"></a>Version 14.0.600.892, veröffentlicht am 31. August 2018

Die folgenden Probleme wurden behoben:

- Ein Textfeld in „Rectangle“ bewirkt, dass das Rechteck nicht vertikal erweitert wird, wenn „rc:Toolbar=False“ festgelegt ist und das Feld viel Text umfasst. 
- Die Textgröße wird nicht skaliert, wenn „pageHeight“ unter 0,5 Zoll liegt. 
- Bei Verwendung mit CRM tritt in der SSRS-Katalogdatenbank ein Deadlock auf. 
- Vertikal ausgerichtete Spaltenüberschriften werden beim Herunterscrollen im Bericht falsch angezeigt. 
- Für Benutzer, die der SCOM-Berichterstellungsrolle hinzugefügt werden, ist der Zugriff auf das SSRS-Webportal blockiert. 
- Thailändische Zeichen werden nicht richtig in das PDF-Format exportiert. 
- Behavior Change bei der Browserrolle. 
- „rc:Toolbar=false“ funktioniert in der Express-Edition nicht. 
- Im Eingabeaufforderungsbereich für Parameter fehlt die vertikale Scrollleiste. 
- Die Laufzeit des Mobilgeräteberichts wurde aktualisiert. 

### <a name="version-140600744-released-april-25-2018"></a>Version 14.0.600.744, veröffentlicht am 25. April 2018 

Die folgenden Probleme wurden behoben:

- Auf der Seite „Datengesteuertes Abonnement“ wird nach der Erstellung die Übermittlungsoption nicht angezeigt
- Das Upgrade von SSRS 2012 auf SSRS 2017 führt dazu, dass RSManagement alle paar Sekunden eine Ausnahme auslöst
- Die Standardwerte für mehrwertige Parameter in IE11 können nicht geändert werden
- Zeitpläne sind stets leer, wenn freigegebener Zeitplan ausgeführt wird

### <a name="version-140600689-released-february-28-2018"></a>Version 14.0.600.689, veröffentlicht am 28. February 2018

Die folgenden Probleme wurden behoben:

- Die Sichtbarkeit von Berichtsparametern in einem verknüpften Bericht wird nach dem Bearbeiten der zugehörigen Eigenschaften zurückgesetzt.
- Der URL-Parameter „rc:Toolbar = false“ funktioniert nicht in der Express Edition.
- Wenn Ausdrücke im Textfeld mit der Eigenschaft „CanGrow“ auf „false“ gesetzt sind, werden die Werte nicht angezeigt.
- Der Link „Weitere Informationen“ für den Product Key wurde zum Setup hinzugefügt.
- Das Webportal mit der benutzerdefinierten Formularauthentifizierung ignoriert Cookie mit variablem Ablauf.
- Beim Export nach Word wird eine ungleiche Zeilenhöhe erstellt, wenn der Zeileninhalt leer ist.

### <a name="version-140600594-released-january-9-2018"></a>Version 14.0.600.594, veröffentlicht am 9. Januar 2018

Sicherheitsupdates

### <a name="version-140600490-released-november-1-2017"></a>Version 14.0.600.490, veröffentlicht am 1. November 2017

Die folgenden Probleme wurden behoben:

- Durch das SKU-Upgrade behobene Probleme

### <a name="version-140600451-released-september-30-2017"></a>Version 14.0.600.451, veröffentlicht am 30. September 2017 

Erste Veröffentlichung

## <a name="next-steps"></a>Nächste Schritte

[Neues bei Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)   

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
