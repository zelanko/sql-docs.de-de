---
title: Versionshinweise für die Report Viewer-Steuerelemente
description: Die Versionshinweise zu den Report Viewer-Steuerelementen für WebForms und WinForms (Reporting Services)
ms.date: 01/16/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maggies
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 5ee9bd80519e9dc9d75bb78a98b548b2a60ef247
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "76259378"
---
# <a name="release-notes-for-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Versionshinweise für die Report Viewer-Steuerelemente für WebForms und WinForms (SSRS)

Dies sind die Versionshinweise zu den Report Viewer-Steuerelementen für WebForms und WinForms. Sie beziehen sich auf [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Die Versionshinweise für SSRS finden Sie unter [Versionshinweise für SQL Server Reporting Services (SSRS) 2017 und höher](../release-notes-reporting-services.md).

## <a name="15014000"></a>150.1400.0
| Beschreibung der Änderung: | Details |
| :----------------- | :------ |
| Fehlerbehebungen | Es wurde ein Problem behoben, bei dem das Viewer-Steuerelement im Entwurfsmodus nicht geladen wurde. |
| &nbsp; | &nbsp; |

## <a name="15013580"></a>150.1358.0
| Beschreibung der Änderung: | Details |
| :----------------- | :------ |
| Fehlerbehebungen | Es wurde eine Änderung rückgängig gemacht, die die Microsoft.ReportViewer.Design-Assemblys aus den Projektverweisen entfernt hat. |
|           | Im Rahmen anderer Änderungen wurden zwei Assemblys von Version 15.0 in Version 15.3 geändert. Auch diese Änderung wurde rückgängig gemacht. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Beschreibung der Änderung: | Details |
| :----------------- | :------ |
| Behebung von Programmfehlern  | Korrekte Druckvorschau auf Monitoren mit hohem DPI-Wert |
|            | Dialogfeld „Drucken“ wurde außerhalb des sichtbaren Bereichs angezeigt |
|            | Eine große Anzahl von Parametern führte dazu, dass die Parameterscrollleisten und -Dropdownlisten nicht ordnungsgemäß funktionierten. |
|            | Problem mit NULL-und datetime-Parametern behoben |
|            | JQuery auf Version 3.3.1 aktualisiert |
|            | Überlappung von Tablix-Zellen im HTML-Rendering behoben |
|            | Die Projektverweise zur Entwurfszeit wurden entfernt, um das Hinzufügen fehlerhafter VS-Assemblys zu vermeiden. |
|            | Korrektur für Barrierefreiheit, damit für die Symbolleiste nur aktive Elemente ausgegeben werden |
| &nbsp; | &nbsp; |

## <a name="150900148"></a>150.900.148

| Beschreibung der Änderung: | Details |
| :----------------- | :------ |
| Korrektur eines Fehlers, der verhinderte, dass Berichte ohne Parameter über **Server.LoadReportDefinition** geladen werden konnten. | &nbsp; |
| Das Report Viewer-Steuerelement „WebForms“. | Unterstützt die Einbettung in RTL-Seiten (Seiten, auf denen der Textfluss mithilfe der CSS-Eigenschaft *direction: rtl;* geändert wird).<br/><br/>Unterstützt die Anpassung des Texts auf dem Druckdialogfeld über die Lokalisierungsschnittstelle *IReportViewerMessages5*.<br/><br/>Verbesserte Unterstützung für die Barrierefreiheit.<br/><br/>&bull; &nbsp; &nbsp; [Nuget-Paket für das Report Viewer-Steuerelement von WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Das Report Viewer-Steuerelement „WinForms“. | Korrektur eines Fehlers beim Drucken, wenn ein App im Modus mit hohem DPI-Wert ausgeführt wird.<br/><br/>&bull; &nbsp; &nbsp; [Nuget-Paket für das Report Viewer-Steuerelement von WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte](integrating-reporting-services-using-reportviewer-controls-get-started.md) mit den Report Viewer-Steuerelementen.

Haben Sie dazu Fragen? [Besuchen Sie das Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231).
