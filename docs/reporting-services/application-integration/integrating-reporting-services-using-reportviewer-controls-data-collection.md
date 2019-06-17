---
title: Datensammlung im ReportViewer-Steuerelement 2016
uthor: markingmyname
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.custom: ''
ms.date: 09/18/2018
ms.openlocfilehash: 69d37c54e49943807c35102362f161e2dbf23068
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66823006"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrieren von Reporting Services mit den ReportViewer-Steuerelementen: Datensammlung

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
## <a name="see-also"></a>Siehe auch

[Verwenden des Report Viewer-Steuerelements „WebForms“](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrieren von Reporting Services mit den Report Viewer-Steuerelementen](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



