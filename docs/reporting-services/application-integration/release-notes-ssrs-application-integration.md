---
title: Versionshinweise für die Steuerelemente der Berichtanzeige von SSRS
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maggies
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: d6c7130e45e535ad1849bed5713313bf6f89020f
ms.sourcegitcommit: 071065bc5433163ebfda4fdf6576349f9d195663
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2019
ms.locfileid: "71923813"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Versions Hinweise für die Report Viewer-Steuerelemente für WebForms und WinForms von SSRS

Dies sind die Anmerkungen zu dieser Version für die Report Viewer-Steuerelemente von WebForms und WinForms im Zusammenhang mit [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Die Anmerkungen zu dieser Version von SSRS finden Sie unter Versions [Hinweise für SQL Server Reporting Services (SSRS) 2017 und](../release-notes-reporting-services.md)höher.

## <a name="15013580"></a>150.1358.0
| Beschreibung ändern | Details |
| :----------------- | :------ |
| Fehlerbehebungen | Es wurde eine Änderung zurückgesetzt, die die Microsoft. Report Viewer. Design-Assemblys aus den Projekt verweisen entfernt hat. |
|           | Im Rahmen anderer Änderungen wurden zwei Assemblys von 15,0 Version in 15,3 geändert. Diese wurde wieder hergestellt. |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Beschreibung ändern | Details |
| :----------------- | :------ |
| Behebung von Programmfehlern  | Richtige Druckvorschau für einen hohen dpi-Monitor |
|            | Dialogfeld "Drucken" würde außerhalb des sichtbaren Raums angezeigt |
|            | Eine große Anzahl von Parametern führte dazu, dass die Parameter Scrollleisten und Dropdown Listen nicht ordnungsgemäß funktionieren. |
|            | Problem mit NULL-und Datums-/Uhrzeitparametern behoben |
|            | JQuery in Version 3.3.1 aktualisiert |
|            | Korrigieren der Überlappung mit Tablix--Zellen im HTML-Rendering |
|            | Die Entwurfszeit Projekt Verweise wurden entfernt, um das Hinzufügen fehlerhafter vs-Assemblys zu vermeiden. |
|            | Barrierefreiheits Korrektur für die Symbolleiste, die nur für aktive Elemente angezeigt werden soll |
| &nbsp; | &nbsp; |

## <a name="15900148"></a>15.900.148

| Beschreibung ändern | Details |
| :----------------- | :------ |
| Korrektur eines Fehlers, der verhinderte, dass Berichte ohne Parameter über **Server.LoadReportDefinition** geladen werden konnten. | &nbsp; |
| Das Report Viewer-Steuerelement „WebForms“. | Unterstützt die Einbettung in RTL-Seiten (Seiten, auf denen der Textfluss mithilfe der CSS-Eigenschaft *direction: rtl;* geändert wird).<br/><br/>Unterstützt die Anpassung des Texts auf dem Druckdialogfeld über die Lokalisierungsschnittstelle *IReportViewerMessages5*.<br/><br/>Verbesserte Unterstützung für die Barrierefreiheit.<br/><br/>&bull; &nbsp; &nbsp;- [nuget-Paket für das Berichts-Viewer-Steuerelement von WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Das Report Viewer-Steuerelement „WinForms“. | Korrektur eines Fehlers beim Drucken, wenn ein App im Modus mit hohem DPI-Wert ausgeführt wird.<br/><br/>&bull; &nbsp; &nbsp;- [nuget-Paket für das Berichts-Viewer-Steuerelement von WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte](integrating-reporting-services-using-reportviewer-controls-get-started.md) mit den Report Viewer-Steuerelementen.

Haben Sie dazu Fragen? [Besuchen Sie das Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231).
