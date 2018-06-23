---
title: Klassenbibliotheken für ein benutzerdefiniertes Berichtselement | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
caps.latest.revision: 27
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b45b9db6304df41d14f30ca226346ff73ef2a9f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058240"
---
# <a name="custom-report-item-class-libraries"></a>Klassenbibliotheken für ein benutzerdefiniertes Berichtselement
  Benutzerdefinierte Berichtselemente verwenden Klassen aus dem `Microsoft.ReportDesigner`-Namespace. Die Klassen, die zum Implementieren eines benutzerdefinierten Berichtselements verwendet werden, können in zwei Hauptkategorien gruppiert werden: eindeutige Klassen zur Unterstützung der Infrastruktur eines benutzerdefinierten Berichtselements und verwaltete Wrapperklassen, die die Funktionalität von relevanten RDL-Elementen (Report Definition Language) kapseln. Ein Codebeispiel für die Verwendung dieser Klassen finden Sie unter [SQL Server Reporting Services-Produktbeispiele](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-infrastructure-classes"></a>Infrastrukturklassen eines benutzerdefinierten Berichtselements  
 Die folgenden Klassen werden zum Implementieren eines benutzerdefinierten Berichtselements verwendet.  
  
> [!NOTE]  
>  Die nachfolgenden Tabellen stellen keine vollständige Liste dar. Sie enthalten nur die am häufigsten verwendeten Eigenschaften und Methoden für jede Klasse.  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a>Microsoft.ReportDesigner.CustomReportItemDesigner  
 Dies ist die Hauptklasse eines benutzerdefinierten Berichtselements. Die Hauptklasse der Implementierung eines benutzerdefinierten Berichtselements muss von dieser Klasse erben.  
  
#### <a name="public-properties"></a>Öffentliche Eigenschaften  
  
|||  
|-|-|  
|`Name`|Der Name des benutzerdefinierten Berichtselements.|  
|`Type`|Der Typ des benutzerdefinierten Berichtselements.|  
|`CustomData`|Ein <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>-Objekt, das die während der Entwurfszeit angegebenen Dateneigenschaften für ein benutzerdefiniertes Berichtselement kapselt.|  
|`CustomProperties`|Eine Auflistung benutzerdefinierter Eigenschaften für das benutzerdefinierte Berichtselement.|  
|`Height`|Die Höhe der Steuerung für ein benutzerdefiniertes Berichtselement.|  
|`Width`|Die Breite der Steuerung für ein benutzerdefiniertes Berichtselement.|  
|`Report`|Ein Container für die Eigenschaften auf Berichtsebene, z. B. die Liste der Datasets in dem Bericht.|  
|`AltReportItem`|Das alternative Berichtselementobjekt, das verwendet werden muss, wenn die Laufzeitsteuerung für das benutzerdefinierte Berichtselement nicht unterstützt wird.|  
|`Style`|Die Stileigenschaften für das benutzerdefinierte Berichtselement.|  
|`Adornment`|Ein Gestaltungsfenster für die interaktive Bearbeitung der Steuerung.|  
|`Site`|Die `ISite` der Komponente.|  
|`DesignerVerbCollection`|Ein Array der benutzerdefinierten Verben für das Kontextmenü der Steuerung.|  
  
#### <a name="public-methods"></a>Öffentliche Methoden  
  
|||  
|-|-|  
|`BeginEdit`|Aktiviert die interaktive Bearbeitung der Steuerung.|  
|`DoDefaultAction`|Wird als Reaktion auf das Doppelklicken oder Drücken der EINGABETASTE auf der Steuerung aufgerufen.|  
|`EndEdit`|Deaktiviert die interaktive Bearbeitung der Steuerung.|  
|`GetService`|Gibt ein Objekt zurück, das einen Dienst darstellt.|  
|`InitializeNewComponent`|Wird aufgerufen, wenn ein neues benutzerdefiniertes Berichtselement erstellt wird.|  
|`Invalidate`|Zeichnet die gesamte Oberfläche der Steuerung neu.|  
|`OnDragEnter`<br /><br /> `OnDragDrop`|Wird aufgerufen, wenn ein Objekt auf die Steuerung gezogen wird.|  
|`OnPaint`|Wird als Reaktion auf das `Paint`-Ereignis aufgerufen.|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a>Microsoft.ReportDesigner.CustomReportItemAttribute  
 Dieses Attribut wird zur Identifizierung des Typs des benutzerdefinierten Berichtselements verwendet. Der Name muss dem Wert des <`Name`>-Attributs des `ReportItem`-Elements in der Konfigurationsdatei des Berichts-Designers entsprechen.  
  
#### <a name="public-methods"></a>Öffentliche Methoden  
  
|||  
|-|-|  
|`CustomReportItemAttribute`|Erstellt das CustomReportItemAttribute-Objekt.|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a>Microsoft.ReportDesigner.LocalizedNameAttribute  
 Dieses Attribut wird zum Festlegen des Anzeigenamens für den Designer des benutzerdefinierten Berichtselements verwendet.  
  
#### <a name="public-methods"></a>Öffentliche Methoden  
  
|||  
|-|-|  
|`LocalizedNameAttribute`|Erstellt das LocalizedNameAttribute-Objekt.|  
  
### <a name="microsoftreportdesigneradornment"></a>Microsoft.ReportDesigner.Adornment  
 Die `Adornment`-Klasse wird von der Entwurfszeitkomponente eines benutzerdefinierten Berichtselements verwendet, um Bereiche außerhalb des Hauptrechtecks der Entwurfsoberfläche bereitzustellen. Diese Bereiche behandeln Benutzeroberflächenereignisse wie Mausklicks und Drag und Drop-Vorgänge.  
  
#### <a name="public-methods"></a>Öffentliche Methoden  
  
|||  
|-|-|  
|`OnShow`|Wird aufgerufen, wenn `Adornment` aktiviert wird.|  
|`OnHide`|Wird aufgerufen, wenn `Adornment` deaktiviert wird.|  
|`Paint`|Wird als Reaktion auf das `Paint`-Ereignis aufgerufen.|  
|`OnDragEnter`<br /><br /> `OnDragOver`<br /><br /> `OnDragLeave`<br /><br /> `OnDragDrop`|Wird aufgerufen, wenn ein Objekt in `Adornment` gezogen wird.|  
  
### <a name="microsoftreportdesigneradornerservice"></a>Microsoft.ReportDesigner.AdornerService  
 Diese Klasse wird zum Bereitstellen einer Auflistung von Anzeigediensten verwendet, die vom benutzerdefinierten Berichtselement zum Unterstützen von `Adornment`-Objekten für die Entwurfszeitkomponente eines benutzerdefinierten Berichtselements genutzt werden.  
  
#### <a name="public-properties"></a>Öffentliche Eigenschaften  
  
|||  
|-|-|  
|`AdornerWindowBounds`|Die Begrenzungen des Gestaltungsfensters.|  
|`AdornerWindowRegion`|Der Bereich des Gestaltungsfensters.|  
|`AdornerWindowGraphics`|Ein Grafikontext für das Gestaltungsfenster.|  
  
#### <a name="public-methods"></a>Öffentliche Methoden  
  
|||  
|-|-|  
|`ComponentRectInDesignerFrame`|Gibt die Begrenzungen der Komponente zurück, die in Designerrahmenkoordinaten umgewandelt wurden.|  
|`InvalidateAdorner`|Führt dazu, dass das Gestaltungsfenster ungültig wird.|  
|`PointToAdorner`|Gibt einen Punkt in Bildschirmkoordinaten zurück, der in Gestaltungsfensterkoordinaten umgewandelt wurde.|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a>Microsoft.ReportDesigner.ExpressionEditor  
 Diese Klasse kann von der Entwurfszeitsteuerung eines benutzerdefinierten Berichtselements verwendet werden, um den Ausdrucks-Editor aufzurufen.  
  
#### <a name="public-methods"></a>Öffentliche Methoden  
  
|||  
|-|-|  
|`EditValue`|Ruft den mit dem angegebenen Objektwert initialisierten Ausdrucks-Editor auf.|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a>Microsoft.ReportDesigner.IFieldsDataObject  
 Diese Klasse ist eine Auflistung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Feldern und wird zum Unterstützen von Drag und Drop-Vorgängen in der Entwurfsumgebung verwendet. Erbt von `IReportItemDataObject`.  
  
#### <a name="public-properties"></a>Öffentliche Eigenschaften  
  
|||  
|-|-|  
|`DataSetName`|Der Name des Datasets mit den Feldern, die abgelegt werden soll.|  
|`Fields`|Die Auflistung von Feldern (`Microsoft.ReportDesigner.Field`), die abgelegt werden sollen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsdefinitionssprache (SSRS)](../reports/report-definition-language-ssrs.md)   
 [Erstellen einer Laufzeitkomponente für ein benutzerdefiniertes Berichtselement](creating-a-custom-report-item-run-time-component.md)   
 [Creating a Custom Report Item Design-Time Component (Erstellen einer Entwurfszeitkomponente für ein benutzerdefiniertes Berichtselement)](creating-a-custom-report-item-design-time-component.md)  
  
  