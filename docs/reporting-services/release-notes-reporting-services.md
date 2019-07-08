---
title: Anmerkungen zu dieser Version (SSRS) 2017 und höher | Microsoft-Dokumentation
ms.date: 02/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.reviewer: maggies
author: casualoak
ms.author: rhys
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 8767640e2ad0a7b71bb7977ab6eb997892845403
ms.sourcegitcommit: eacc2d979f1f13cfa07e0aa4887eb9d48824b633
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67533833"
---
# <a name="release-notes-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Versionshinweise für SQL Server Reporting Services (SSRS) 2017 und höher

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)]

Dieser Artikel beschreibt die Änderungen in [!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS), für die Versionen 2017 und höher.

Die Versionshinweise für Berichts-Viewer-Steuerelemente finden Sie unter [Versionshinweise für den Berichts-Viewer-Steuerelemente für WebForms und WinForms von SSRS](application-integration/release-notes-ssrs-application-integration.md).

<!--
We are "standardizing" all our 'Release Notes' style articles:

  - File names:   'release-notes-[TechArea-Name].md'


  - Content format:   2-column tables.  No longer using bullet lists.

    - Ideally, the 'Details' column should contain a link to another SSRS documentation article wherein the particular issue fix is discussed in any way.  Or if there is more to say beyond one sentence, the other sentences of elaboration would go into the 'Details' column.


  - H2 header names are kept short, for better display.


  - Try to keep all Release Notes in one .md file.  Avoid having multiple R.N. files whose names differ only by version or date.

    - Seriously consider erasing info about ancient releases that are so old that nobody cares about them anymore.  If you really want to retain ancient info, consider doing so in an HTML comment at the end of the .md file, just in case a Microsoft employee needs to re-examine ancient info.  In any case, this file cannot get ever longer, and some deletion or hiding of oldest info must eventually occur.


  - Do use '::: moniker range=' zones when version 2017 is no longer the only version represented inside this .md file.

    - Use the '=' operator on the moniker, not the '>=' operator.
    - In contrast, in our 'Whats New' articles we do use the '>=', rather than '='.

GeneMi, DevOps = 1467988 (MsEng > TechnicalContent) , 2019/03/19
-->

## <a name="1406001274-20190701"></a>14.0.600.1274, 1.7.2019

| Problem wurde behoben | Details |
| :---------- | :------ |
| Sicherheitsupdates | &nbsp; |
| Keine Wochentage auswählen beim Erstellen eines freigegebenen Zeitplans für wöchentlichen | &nbsp; |
| Bericht zeigt keine Wagenrückläufe ordnungsgemäß im Word-Format an | &nbsp; |
| System Center Operations Manager(SCOM) 2019 wird nicht mehr funktioniert mit aktuellen SSRS 2017 aktualisiert. | &nbsp; |
| Fehler beim Aufrufen von autorisierungserweiterungen für freigegebenes Dataset | &nbsp; |
| Logik, die geändert werden, auf die gespeicherte Prozedur GetAllProperties in SSRS 2017 und PBIRS, wodurch die Webdienst-Endpunkt kann nicht abgerufen werden keine Daten für verknüpften Bericht ReportingService2010.GetProperties-Methode | &nbsp; |
| Einfaches Raster Zeilenheader im mobilen Bericht nicht mehr angezeigt wird, wenn ein Element innerhalb des Rasters geklickt wird | &nbsp; |
| Keine Date-Felds im Parameter für datengesteuertes Abonnement verwenden | &nbsp; |
| Geschachtelte Tablix Zeigt kleine oder Schriftart teilweise in SSRS 2016 und höher | &nbsp; |
| Abonnements mit DateTime-Parameter Fehler nach Benutzer mit verschiedenen Gebietsschemas Änderungen das Abonnement | &nbsp; |
| Erstellen ein datengesteuertes Abonnement mit Null-Übermittlungserweiterung kann nicht mit "verfügt über eine Bereitstellung Fehler" | &nbsp; |
| URL-Codierung ist falsch, beim Festlegen des Werts im Excel\Word-format | &nbsp; |

## <a name="1406001109-20190212"></a>14.0.600.1109, 12. Februar 2019

| Problem wurde behoben | Details |
| :---------- | :------ |
| Nach Änderung des Abonnements ändern sich die Zeitpläne für Cache-Berichtsmomentaufnahmen in „Berichtsspezifischer Zeitplan“. | &nbsp; |
| „rc:Toolbar=false“ hat in der Express Edition nicht funktioniert. | &nbsp; |
| Bestimmte thailändische Zeichen wurden beim Exportieren paginierter Berichte in PDF nicht ordnungsgemäß gerendert. | &nbsp; |
| Deadlock während der Benachrichtigung für abgeschlossene datengesteuerte Abonnements. | &nbsp; |
| Eingebettete Bilder wurden in bestimmten Fällen nicht angezeigt, wenn der Parameter „rc: Toolbar=False“ verwendet wurde. | &nbsp; |
| Für Berichte mit kaskadierenden Parametern konnten keine datengesteuerten Abonnements erstellt werden. | &nbsp; |
| Mit einem ungültigen Intervall konfigurierte Abonnements konnten nicht bearbeitet werden. | &nbsp; |
| Sicherheitsupdates | &nbsp; |
| Benutzeroberfläche für verknüpfte Berichte wurde nicht angezeigt. | &nbsp; |
| Bestimmte paginierte Berichte mit geschachtelten Tablix-Steuerelementen wiesen falsche Schriftarten auf. | &nbsp; |
| Leerzeichen wird nicht ordnungsgemäß auf bestimmte paginierte Berichte hinzugefügt, die Tablix-Datenbereiche enthalten. | &nbsp; |
| Kopfzeilen sind beim Erweitern einfacher Datenraster in Mobilgeräteberichten verschwunden. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600906-20180912"></a>14.0.600.906, 12. September 2018

Das folgende Problem wurde behoben:

| Problem wurde behoben | Details |
| :---------- | :------ |
| Benutzerdefinierte Authentifizierung, die keine richtigen Cookieinformationen zurückgegeben hat. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600892-20180831"></a>14.0.600.892, 31. August 2018

| Problem wurde behoben | Details |
| :---------- | :------ |
| Ein Textfeld in „Rectangle“ hat bewirkt, dass das Rechteck nicht vertikal erweitert wurde, wenn „rc:Toolbar=False“ festgelegt und in dem Feld viel Text enthalten war. | &nbsp; |
| Die Textgröße wurde nicht skaliert, wenn „pageHeight“ unter 0,5 Zoll lag. | &nbsp; |
| Deadlock tritt in der SSRS-Katalogdatenbank auf, wenn er mit CRM verwendet wird. | &nbsp; |
| Vertikal ausgerichtete Spaltenüberschriften wurden beim Herunterscrollen im Bericht falsch angezeigt. | &nbsp; |
| Benutzer, die System Center Operations Manager-Berichterstattung der Rolle hinzugefügt haben, Zugriff blockiert, SSRS-Webportal. | &nbsp; |
| Thai-Zeichen ist nicht ordnungsgemäß in die PDF-Datei exportiert. | &nbsp; |
| Behavior Change bei der Browserrolle. | &nbsp; |
| „rc:Toolbar=false“ hat in der Express Edition nicht funktioniert. | &nbsp; |
| Fehlt der vertikalen scrollleiste im Eingabeaufforderungsbereich für Parameter. | &nbsp; |
| Die Laufzeit des Mobilgeräteberichts wurde aktualisiert. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600744-20180425"></a>14.0.600.744, 25. April 2018

| Problem wurde behoben | Details |
| :---------- | :------ |
| Auf der Seite „Datengesteuertes Abonnement“ wurde nach der Erstellung die Übermittlungsoption nicht angezeigt. | &nbsp; |
| Das Upgrade von SSRS 2012 auf SSRS 2017 hat dazu geführt, dass RSManagement alle paar Sekunden eine Ausnahme auslöst. | &nbsp; |
| Die Standardwerte für mehrwertige Parameter in IE11 konnten nicht geändert werden. | &nbsp; |
| Zeitpläne waren stets leer, wenn freigegebener Zeitplan ausgeführt wurde. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600689-20180228"></a>14.0.600.689, 28. Februar 2018

| Problem wurde behoben | Details |
| :---------- | :------ |
| Die Sichtbarkeit von Berichtsparametern in einem verknüpften Bericht wurde nach dem Bearbeiten der zugehörigen Eigenschaften zurückgesetzt. | &nbsp; |
| Der URL-Parameter „rc:Toolbar = false“ hat in der Express Edition nicht funktioniert. | &nbsp; |
| Legen mit Ausdrücken in einem Textfeld mit dem "CanGrow"-Eigenschaft auf "false" ergeben sich Werte, die nicht angezeigt. | &nbsp; |
| Der Link _Weitere Informationen_ für den Product Key wurde zum Setup hinzugefügt. | &nbsp; |
| Das Webportal mit der benutzerdefinierten Formularauthentifizierung hat Cookie mit variablem Ablauf ignoriert. | &nbsp; |
| Beim Export nach Word wurde eine ungleiche Zeilenhöhe erstellt, wenn der Zeileninhalt leer war. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600594-20180109"></a>14.0.600.594, 09. Januar 2018

Es wurden einige Sicherheitsupdates implementiert.

### <a name="140600490-20171101"></a>14.0.600.490, 01. November 2017

Die Probleme beim SKU-Upgrade wurden behoben.

## <a name="140600451-20170930"></a>14.0.600.451, 30. September 2017

Erste Veröffentlichung

## <a name="next-steps"></a>Nächste Schritte

[Neuerungen in Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231).
