---
title: Excel-Ziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldest.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 84647752eb549bd5d3607637d679e58356597a6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62827223"
---
# <a name="excel-destination"></a>Excel-Ziel
  Das Excel-Ziel lädt Daten in Arbeitsblätter oder Bereiche in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel-Arbeitsmappen.  
  
## <a name="access-modes"></a>Zugriffsmodi  
 Das Excel-Ziel stellt drei verschiedene Datenzugriffsmodi zum Laden von Daten bereit:  
  
-   Eine Tabelle oder Sicht.  
  
-   Eine in einer Variablen angegebene Tabelle oder Sicht.  
  
-   Die Ergebnisse einer SQL-Anweisung. Bei der Abfrage kann es sich um eine parametrisierte Abfrage handeln.  
  
> [!IMPORTANT]  
>  In Excel entspricht ein Arbeitsblatt oder ein Bereich einer Tabelle oder Sicht. In den Listen der verfügbaren Tabellen im Quellen-Editor und Ziel-Editor für Excel werden nur vorhandene Arbeitsblätter (identifiziert durch das an den Arbeitsblattnamen angefügte $-Zeichen, wie z. B. Sheet1$) und benannte Bereiche (identifiziert durch das Fehlen des $-Zeichens, wie z. B. MyRange) angezeigt.  
  
## <a name="usage-considerations"></a>Überlegungen zur Verwendung  
 Der Excel-Verbindungs-Manager verwendet den [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für Jet 4.0 und den unterstützenden Excel-ISAM-Treiber (Indexed Sequential Access Method, indizierte sequenzielle Zugriffsmethode), um sich mit Excel-Datenquellen zu verbinden und diese zu lesen und in sie zu schreiben.  
  
 In vielen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base-Artikeln ist das Verhalten dieses Anbieters und Treibers dokumentiert. Diese Artikel beziehen sich zwar nicht speziell auf [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] oder die Vorgängerversion Data Transformation Services, aber Sie sollten bestimmte Verhaltensweisen kennen, die zu unerwarteten Ergebnissen führen können. Allgemeine Informationen zu Verwendung und Verhalten des Excel-Treibers finden Sie unter [SO WIRD'S GEMACHT: Verwenden von ADO mit Excel-Daten von Visual Basic oder VBA](https://support.microsoft.com/kb/257819).  
  
 Die folgenden Verhaltensweisen des im Excel-Treiber enthaltenen Jet-Anbieters können zu unerwarteten Ergebnissen führen, wenn Daten in ein Excel-Ziel gespeichert werden.  
  
-   **Speichern von Textdaten**. Wenn der Excel-Treiber Textdatenwerte in ein Excel-Ziel speichert, wird vor den Text jeder Zelle das einfache Anführungszeichen (') gesetzt, um sicherzustellen, dass die gespeicherten Werte als Textwerte interpretiert werden. Wenn Sie andere Anwendungen verwenden bzw. entwickeln, die die gespeicherten Daten lesen oder verarbeiten, kann eine spezielle Verarbeitung des vor jedem Textwert gesetzten einfachen Anführungszeichens erforderlich sein.  
  
     Informationen dazu, wie Sie das Einschließen des einfachen Anführungszeichens vermeiden, finden Sie in diesem Blogpost: [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](https://go.microsoft.com/fwlink/?LinkId=400876)(Einzelnes Anführungszeichen wird an alle Zeichenfolgen angehängt, wenn Daten für Excel umgewandelt werden und die Excel-Ziel-Datenflusskomponente in SSIS verwendet wird), auf msdn.com.  
  
-   Das **Speichern von Memo (ntext)** ist. Zum erfolgreichen Speichern von Zeichenfolgen mit mehr als 255 Zeichen in einer Excel-Spalte muss der Treiber den Datentyp der Zielspalte als **memo** und nicht als **string**erkennen. Wenn die Zieltabelle bereits Datenzeilen enthält, müssen die ersten Zeilen, die vom Treiber als Stichprobe genommen werden, mindestens eine Instanz eines Werts mit mehr als 255 Zeichen in der Memospalte enthalten. Wenn die Ziel Tabelle während des Paket Entwurfs oder zur Laufzeit erstellt wird, muss für die CREATE TABLE-Anweisung LONGTEXT (oder eines der Synonyme) als Datentyp der Memo Spalte verwendet werden.  
  
-   **Datentypen**. Der Excel-Treiber erkennt nur einen begrenzten Satz von Datentypen. Beispielsweise werden alle numerischen Spalten als Werte mit doppelter Genauigkeit (DT_R8) interpretiert, und alle Zeichenfolgenspalten (außer Memospalten) werden als Unicode-Zeichenfolgen mit 255 Zeichen (DT_WSTR) interpretiert. 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] werden die Excel-Datentypen folgendermaßen zugeordnet:  
  
    -   Numerisch – Gleitkommawert mit doppelter Genauigkeit (DT_R8)  
  
    -   Währung – Währung (DT_CY)  
  
    -   Boolesch – Boolesch (DT_BOOL)  
  
    -   Datum/Uhrzeit `datetime` (DT_DATE)  
  
    -   Zeichenfolge – Unicode-Zeichenfolge, Länge 255 (DT_WSTR)  
  
    -   Memo – Unicode-Textstream (DT_NTEXT)  
  
-   **Datentyp-und Längen Konvertierungen**. 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] werden Datentypen nicht implizit konvertiert. Daher müssen Sie eventuell die Transformationen für abgeleitete Spalten und für die Datenkonvertierung verwenden, um Excel-Daten vor dem Laden in ein Nicht-Excel-Ziel explizit zu konvertieren bzw. um Nicht-Excel-Daten vor dem Laden in ein Excel-Ziel zu konvertieren. In diesem Fall kann es nützlich sein, das erste Paket mit dem Import/Export-Assistenten zu erstellen, mit dem die Konfiguration notwendiger Konvertierungen vorgenommen wird. Im Folgenden finden Sie einige Beispiele für ggf. erforderliche Konvertierungen:  
  
    -   Konvertierung zwischen Unicode-Excel-Zeichenfolgenspalten und Nicht-Unicode-Zeichenfolgenspalten mit bestimmten Codepages.  
  
    -   Konvertierung zwischen Excel-Zeichenfolgenspalten mit 255 Zeichen und Zeichenfolgenspalten anderer Längen.  
  
    -   Konvertierung zwischen numerischen Excel-Spalten mit doppelter Genauigkeit und numerischen Spalten anderer Typen.  
  
## <a name="configuration-of-the-excel-destination"></a>Konfiguration des Excel-Ziels  
 Das Excel-Ziel verwendet einen Excel-Verbindungs-Manager zum Herstellen einer Verbindung mit einer Datenquelle. Dieser Verbindungs-Manager gibt die zu verwendende Arbeitsmappendatei an. Weitere Informationen finden Sie unter [Excel Connection Manager](../connection-manager/excel-connection-manager.md).  
  
 Das Excel-Ziel weist eine reguläre Eingabe und eine Fehlerausgabe auf.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Ziel-Editor für Excel** festlegen können:  
  
-   [Der Ziel-Editor für Excel &#40;Seite Verbindungs-Manager&#41;](../excel-destination-editor-connection-manager-page.md)  
  
-   [Ziel-Editor für Excel &#40;Seite "Zuordnungen"&#41;](../excel-destination-editor-mappings-page.md)  
  
-   [Der Ziel-Editor für Excel &#40;Seite Fehlerausgabe&#41;](../excel-destination-editor-error-output-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält alle Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Excel](excel-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Laden von Daten aus oder in Excel mit SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)  
  
-   [Schleife durch Excel-Dateien und Tabellen mit einem Foreach-Schleifencontainer](../control-flow/foreach-loop-container.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blogeintrag [Excel in Integration Services, Part 1 of 3: Connections and Components](https://go.microsoft.com/fwlink/?LinkId=217674)auf dougbert.com  
  
-   Blogeintrag [Excel in Integration Services, Part 2 of 3: Tables and Data Types](https://go.microsoft.com/fwlink/?LinkId=217675)auf dougbert.com.  
  
-   Blogeintrag [Excel in Integration Services, Part 3 of 3: Issues and Alternatives](https://go.microsoft.com/fwlink/?LinkId=217676)auf dougbert.com.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Excel-Quelle](excel-source.md)   
 [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md)   
 [Datenfluss](data-flow.md)   
 [Arbeiten mit Excel-Dateien mit dem Skripttask](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
