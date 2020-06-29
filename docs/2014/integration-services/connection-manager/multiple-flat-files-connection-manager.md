---
title: Verbindungs-Manager für mehrere Flatfiles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 15084294d26be8afc8e933c7c7c4066506ef3fd9
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438367"
---
# <a name="multiple-flat-files-connection-manager"></a>Verbindungs-Manager für mehrere Flatfiles
  Mit einem Verbindungs-Manager für mehrere Flatfiles kann ein Paket auf Daten in mehreren Flatfiles zugreifen. Eine Flatfilequelle kann beispielsweise einen Verbindungs-Manager für mehrere Flatfiles verwenden, wenn sich der Datenflusstask in einem Schleifencontainer wie dem For-Schleifencontainer befindet. In jeder Schleife des Containers werden von der Flatfilequelle Daten vom nächsten Dateinamen geladen, der vom Verbindungs-Manager für mehrere Flatfiles bereitgestellt wird.  
  
 Wenn Sie einem Paket einen Verbindungs-Manager für mehrere Flatfiles hinzufügen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt einen Verbindungs-Manager, der zur Laufzeit in eine Verbindung für mehrere Flatfiles aufgelöst wird, die Eigenschaften für den Verbindungs-Manager für mehrere Flatfiles festlegt und der-Auflistung des Pakets den Verbindungs-Manager für mehrere Flatfiles hinzufügt `Connections` .  
  
 Die `ConnectionManagerType`-Eigenschaft des Verbindungs-Managers ist auf `MULTIFLATFILE` festgelegt.  
  
 Es gibt folgende Möglichkeiten, um einen Verbindungs-Manager für mehrere Flatfiles zu konfigurieren:  
  
-   Geben Sie die Dateien, das Gebietsschema und die Codepage an, die Sie verwenden möchten. Mithilfe des Gebietsschemas werden gebietsschemabezogene Daten interpretiert, wie z. B. Datumsangaben, und mithilfe der Codepage werden Zeichenfolgendaten in Unicode-Daten konvertiert.  
  
-   Geben Sie das Dateiformat an. Sie können ein Format mit Trennzeichen, fester Breite oder rechtem Flatterrand verwenden.  
  
-   Geben Sie eine Kopfzeile, eine Datenzeile und Spaltentrennzeichen an. Spaltentrennzeichen können auf Dateiebene festgelegt und auf Spaltenebene überschrieben werden.  
  
-   Zeigen Sie an, ob die erste Zeile in den Dateien Spaltennamen enthalten.  
  
-   Geben Sie ein Textqualifiziererzeichen an. Für jede Spalte kann die Erkennung eines Textqualifizierers konfiguriert werden.  
  
-   Legen Sie Eigenschaften wie z. B. den Namen, den Datentyp und die maximale Breite für einzelne Spalten fest.  
  
 Wenn der Verbindungs-Manager für mehrere Flatfiles auf mehrere Dateien verweist, werden die Pfade der Dateien durch einen senkrechten Strich (|) getrennt. Die `ConnectionString`-Eigenschaft des Verbindungs-Managers hat folgendes Format:  
  
 \<*path*>|\<*path*>  
  
 Mehrere Dateien können Sie auch mithilfe von Platzhalterzeichen angeben. Um beispielsweise auf alle Textdateien auf dem Laufwerk C zu verweisen, kann der Wert der `ConnectionString` Eigenschaft auf c: \\ *. txt festgelegt werden.  
  
 Falls ein Verbindungs-Manager für Flatfiles auf mehrere Dateien verweist, müssen alle Dateien das gleiche Format aufweisen.  
  
 Der Verbindungs-Manager für mehrere Flatfiles legt die Länge von Zeichenfolgenspalten standardmäßig auf 50 Zeichen fest. Sie können im Dialogfenster **Verbindungs-Manager-Editor für mehrere Flatfiles** Beispieldaten auswerten und automatisch die Länge dieser Spalten ändern, um zu vermeiden, dass Daten abgeschnitten werden oder die Spaltenbreite überschritten wird. Es sei denn, Sie ändern die Spaltenlänge in einer Flatfilequelle oder in einer Transformation. Dann bleibt die Spaltenlänge der Zeichenfolgenspalte im gesamten Datenfluss gleich. Wenn diese Spalten Zielspalten zugeordnet sind, die schmaler sind, werden in der Benutzeroberfläche Warnungen angezeigt. Darüber hinaus können aufgrund der abgeschnittenen Daten zur Laufzeit Fehler angezeigt werden. Sie können im Verbindungs-Manager für Flatfiles, in der Flatfilequelle oder in einer Transformation die Größe der Spalten auf die Größe der Zielspalten ändern. Wenn Sie die Länge der Ausgabespalten ändern möchten, legen Sie die `Length` -Eigenschaft der Ausgabe Spalte auf der Registerkarte **Eingabe-und Ausgabe Eigenschaften** im Dialogfeld **Erweiterter Editor** fest.  
  
 Wenn Sie die Spaltenlängen im Verbindungs-Manager für mehrere Flatfiles aktualisieren, nachdem Sie die Flatfilequelle, die den Verbindungs-Manager verwendet, hinzugefügt und geändert haben, ist das manuelle Ändern der Ausgabespaltengröße in der Flatfilequelle nicht erforderlich. Wenn Sie das Dialogfeld **Flatfilequelle** öffnen, stellt die Flatfilequelle eine Option zum Synchronisieren der Spaltenmetadaten bereit.  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a>Konfiguration des Verbindungs-Managers für mehrere Flatfiles  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Allgemein“&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Spalten“&#41;](../multiple-flat-files-connection-manager-editor-columns-page.md)  
  
-   [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Erweitert“&#41;](../multiple-flat-files-connection-manager-editor-advanced-page.md)  
  
-   [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Vorschau“&#41;](../multiple-flat-files-connection-manager-editor-preview-page.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Flatfilequelle](../data-flow/flat-file-source.md)   
 [Flatfileziel](../data-flow/flat-file-destination.md)   
 [Integration Services (SSIS) Connections (Integration Services-Verbindungen (SSIS))](integration-services-ssis-connections.md)  
  
  
