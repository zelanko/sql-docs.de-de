---
title: Datensammlung im ReportViewer-Steuerelement
description: Das ReportViewer-Steuerelement erfasst anonyme Nutzungsdaten, um zu ermitteln, wie Kunden das Produkt verwenden, damit sich die Entwicklung auf Verbesserungen konzentrieren kann, die für Kunden am relevantesten sind.
author: maggiesMSFT
ms.author: maggies
ms.custom: seo-lt-2019
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.date: 06/03/2020
ms.openlocfilehash: 22f693824c244e02f313e488a067a0b732b2fa10
ms.sourcegitcommit: dc6ea6665cd2fb58a940c722e86299396b329fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84423398"
---
# <a name="integrate-reporting-services-using-reportviewer-controls---data-collection"></a>Integrieren von Reporting Services mit den ReportViewer-Steuerelementen: Datensammlung

Das Steuerelement sammelt anonyme Nutzungsdaten, damit Unternehmen besser verstehen, wie Kunden ein Produkt verwenden. Nutzungsdaten ermöglichen es, sich bei Neuentwicklungen auf die Verbesserungen zu konzentrieren, die am wichtigsten für die Kunden sind.

Eine Erläuterung der Verfahren zur Datensammlung und -nutzung von Microsoft SQL Server und Report Viewer finden Sie in der [Datenschutzerklärung](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Deaktivieren der Datensammlung

Die Sammlung von Nutzungsdaten kann über die Eigenschaft ```EnableTelemetry``` deaktiviert werden.

```xml
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

Alternativ dazu ist eine pragmatische Deaktivierung möglich, bevor das Steuerelement gerendert wird.
    
```csharp
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Weitere Informationen

[Verwenden des Report Viewer-Steuerelements „WebForms“](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrieren von Reporting Services mit den Report Viewer-Steuerelementen](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



