---
title: Änderungsprotokoll für die Report Viewer-Steuerelemente der Reporting Services
ms.date: 09/19/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 57eca1ced359ec08dc9b64f6840d0eadf1fb3f3e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771379"
---
# <a name="changelog-for-the-report-viewer-controls"></a>Änderungsprotokoll für die Report Viewer-Steuerelemente

Dieses Änderungsprotokoll verfolgt die Freigabe der Report Viewer-Steuerelemente „WinForms“ und „WebForms“ nach.

## <a name="15900148"></a>15.900.148
In diesem Update
 - Korrektur eines Fehlers, der verhinderte, dass Berichte ohne Parameter über Server.LoadReportDefinition geladen werden konnten.

Das Report Viewer-Steuerelement [WebForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148).
 - Unterstützt die Einbettung in RTL-Seiten (Seiten, auf denen der Textfluss mithilfe der CSS-Eigenschaft *direction: rtl;* geändert wird).
 - Unterstützt die Anpassung des Texts auf dem Druckdialogfeld über die Lokalisierungsschnittstelle *IReportViewerMessages5*.
 - Verbesserte Unterstützung für die Barrierefreiheit.

Das Report Viewer-Steuerelement [WinForms](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148).
 - Korrektur eines Fehlers beim Drucken, wenn ein App im Modus mit hohem DPI-Wert ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte](integrating-reporting-services-using-reportviewer-controls-get-started.md) mit den Report Viewer-Steuerelementen  
Haben Sie dazu Fragen? [Besuchen Sie das Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
