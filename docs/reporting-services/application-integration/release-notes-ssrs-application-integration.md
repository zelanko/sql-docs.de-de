---
title: Versionshinweise für die Steuerelemente der Berichtanzeige von SSRS
ms.date: 09/20/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maghan
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: d6d4da6d5574288fa66ea18a9c63b1488a6abcca
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290945"
---
# <a name="release-notes-for-the-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Anmerkungen zu dieser Version für die Berichts-Viewer-Steuerelemente für WebForms und WinForms von SSRS

Hierbei handelt es sich um die Anmerkungen zu dieser Version für die Berichts-Viewer-Steuerelemente eines WebForms und WinForms, die im Zusammenhang mit [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Die Versionshinweise für SSRS finden Sie unter [Versionsanmerkungen für SQL Server Reporting Services (SSRS) 2017 und höher](../release-notes-reporting-services.md).

## <a name="15900148"></a>15.900.148

| Beschreibung der Änderung | Details |
| :----------------- | :------ |
| Korrektur eines Fehlers, der verhinderte, dass Berichte ohne Parameter über **Server.LoadReportDefinition** geladen werden konnten. | &nbsp; |
| Das Report Viewer-Steuerelement „WebForms“. | Unterstützt die Einbettung in RTL-Seiten (Seiten, auf denen der Textfluss mithilfe der CSS-Eigenschaft *direction: rtl;* geändert wird).<br/><br/>Unterstützt die Anpassung des Texts auf dem Druckdialogfeld über die Lokalisierungsschnittstelle *IReportViewerMessages5*.<br/><br/>Verbesserte Unterstützung für die Barrierefreiheit.<br/><br/>&bull; &nbsp; &nbsp; [NuGet-Paket für das Berichts-Viewer-Steuerelement eines WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Das Report Viewer-Steuerelement „WinForms“. | Korrektur eines Fehlers beim Drucken, wenn ein App im Modus mit hohem DPI-Wert ausgeführt wird.<br/><br/>&bull; &nbsp; &nbsp; [NuGet-Paket für das Berichts-Viewer-Steuerelement von Windows Forms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte](integrating-reporting-services-using-reportviewer-controls-get-started.md) mit den Report Viewer-Steuerelementen.

Haben Sie dazu Fragen? [Besuchen Sie das Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231).
