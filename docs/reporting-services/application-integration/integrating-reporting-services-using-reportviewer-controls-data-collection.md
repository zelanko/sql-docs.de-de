---
title: Datensammlung im ReportViewer-Steuerelement 2016
uthor: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.technology: application-integration
ms.topic: reference
ms.custom: ''
ms.date: 09/18/2018
ms.openlocfilehash: 52f23cd615179b774392920c84ab4370892e1dd5
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100195"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integrieren von Reporting Services mit den ReportViewer-Steuerelementen: Datensammlung

Das Steuerelement sammelt anonyme Nutzungsdaten, damit Unternehmen besser verstehen, wie Kunden ein Produkt verwenden. Nutzungsdaten ermöglichen es, sich bei Neuentwicklungen auf die Verbesserungen zu konzentrieren, die am wichtigsten für die Kunden sind.

Eine Erläuterung der Verfahren zur Datensammlung und -nutzung von Microsoft SQL Server und Report Viewer finden Sie in der [Datenschutzerklärung](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Deaktivieren der Datensammlung

Die Sammlung von Nutzungsdaten kann über die Eigenschaft ```EnableTelemetry``` deaktiviert werden.

```
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

Alternativ dazu ist eine pragmatische Deaktivierung möglich, bevor das Steuerelement gerendert wird.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Siehe auch

[Verwenden des Report Viewer-Steuerelements „WebForms“](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integrieren von Reporting Services mit den Report Viewer-Steuerelementen](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



