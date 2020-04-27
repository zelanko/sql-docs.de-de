---
title: Kopieren und Einfügen von Daten (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad25ecae16a9b5e5f32554350a315156e9818241
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086967"
---
# <a name="copy-and-paste-data-ssas-tabular"></a>Kopieren und Einfügen von Daten (SSAS – tabellarisch)
  Sie können Tabellendaten aus externen Anwendungen kopieren und sie in eine neue oder vorhandene Tabelle im Modell-Designer einfügen. Die Daten, die Sie aus der Zwischenablage einfügen, müssen im HTML-Format vorliegen, z. B. Daten, die aus Excel oder Word kopiert werden. Der Modell-Designer erkennt automatisch Datentypen und wenden sie auf die eingefügten Daten an. Sie können den Datentyp auch manuell ändern oder die Formatierung einer Spalte anzeigen.  
  
 Im Unterschied zu Tabellen mit einer Datenquellenverbindung verfügen eingefügte Tabellen über keine ConnectionName-Eigenschaft oder SourceData-Eigenschaft. Eingefügte Daten werden in der Datei Model.bim beibehalten. Beim Speichern des Projekts oder der Datei Model.bim werden die eingefügten Daten ebenfalls gespeichert.  
  
 Bei der Modellbereitstellung werden die eingefügten Daten mit dem Modell bereitgestellt, und zwar unabhängig davon, ob das Modell mit der Bereitstellung verarbeitet wird.  
  
 Abschnitte in diesem Thema:  
  
-   [Voraussetzungen](#bkmk_prerequisites)  
  
-   [Einfügen von Daten](#bkmk_paste_data)  
  
-   [Vorschau einfügen (Dialogfeld)](#bkmk_paste_preview)  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> Voraussetzungen  
 Beim Einfügen von Daten müssen verschiedene Einschränkungen beachtet werden:  
  
-   Eingefügte Tabellen dürfen maximal 10.000 Zeilen enthalten.  
  
-   Eingefügte Tabellen können nicht partitioniert werden.  
  
-   Eingefügte Tabellen werden nicht im DirectQuery-Modus unterstützt.  
  
-   Beim Arbeiten mit einer Tabelle, die anfänglich durch Einfügen von Daten aus der Zwischenablage erstellt wurde, sind nur die Optionen **Am Ende einfügen** und **Am Ende ersetzen** verfügbar. Sie können **Am Ende einfügen** oder **Am Ende ersetzen** nicht verwenden, um einer Tabelle, die importierte Daten enthält, Daten aus einem anderen Datenquellentyp hinzuzufügen.  
  
-   Wenn Sie **Am Ende einfügen** oder **Am Ende ersetzen**verwenden, müssen in den neuen Daten genau die gleiche Anzahl von Spalten wie in den ursprünglichen Daten enthalten sein. Idealerweise sollten die Datenspalten, die Sie einfügen oder anfügen, denselben oder einen mit den Spalten in der Zieltabelle kompatiblen Datentyp aufweisen. In einigen Fällen können Sie einen anderen Datentyp verwenden, dabei kann jedoch ein **Typenkonflikt** -Fehler angezeigt werden.  
  
##  <a name="paste-data"></a><a name="bkmk_paste_data"></a> Einfügen von Daten  
  
#### <a name="to-paste-data-into-the-designer"></a>So fügen Sie Daten in den Designer ein  
  
-   Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf das Menü **Bearbeiten** , und klicken Sie dann auf eine der folgenden Optionen:  
  
    -   Klicken Sie auf **Einfügen** , um den Inhalt der Zwischenablage in eine neue Tabelle einzufügen.  
  
    -   Klicken Sie auf **Am Ende einfügen** , um den Inhalt der Zwischenablage als zusätzliche Zeilen in die ausgewählte Tabelle einzufügen. Die neuen Zeilen werden am Ende der Tabelle hinzugefügt.  
  
    -   Klicken Sie auf **Am Ende ersetzen** , um die ausgewählte Tabelle durch den Inhalt der Zwischenablage zu ersetzen. Alle vorhandenen Namen von Spaltenüberschriften bleiben in der Tabelle, und Beziehungen werden beibehalten.  
  
##  <a name="paste-preview-dialog-box"></a><a name="bkmk_paste_preview"></a>Vorschau einfügen (Dialog Feld)  
 Im Dialogfeld **Vorschau einfügen** können Sie eine Vorschau der in das Designer-Fenster kopierten Daten anzeigen und sicherstellen, dass die Daten ordnungsgemäß kopiert werden. Kopieren Sie zum Öffnen des Dialogfelds tabellenbasierte Daten im HTML-Format in die Zwischenablage, und klicken Sie anschließend im Designer auf das Menü **Bearbeiten** . Klicken Sie anschließend auf **Einfügen**, **Am Ende anfügen**oder **Beim Einfügen ersetzen**. Die Optionen **Am Ende einfügen** und **Am Ende ersetzen** sind nur verfügbar, wenn Sie Daten in einer Tabelle hinzufügen oder ersetzen, die durch das Kopieren und Einfügen aus der Zwischenablage erstellt wurde. Sie können **Am Ende einfügen** oder **Am Ende ersetzen** nicht verwenden, um Daten einer Tabelle mit importierten Daten hinzuzufügen.  
  
 Die Optionen in diesem Dialogfeld unterscheiden sich abhängig davon, ob Sie Daten in eine vollkommen neue Tabelle einfügen, Daten in eine vorhandene Tabelle einfügen und die vorhandenen Daten durch die neuen Daten ersetzen oder Daten an eine vorhandene Tabelle anfügen.  
  
### <a name="paste-to-new-table"></a>In neue Tabelle einfügen  
 **Tabellenname**  
 Geben Sie den Namen der Tabelle an, die im Designer erstellt werden soll.  
  
 **Einzufügende Daten**  
 Zeigt ein Beispiel für den Inhalt der Zwischenablage an, der der Zieltabelle hinzugefügt wird.  
  
### <a name="paste-append"></a>Am Ende einfügen  
 **Vorhandene Daten in der Tabelle**  
 Zeigt ein Beispiel der vorhandenen Daten in der Tabelle an, damit Sie die Spalten, Datentypen usw. überprüfen können.  
  
 **Einzufügende Daten**  
 Zeigt ein Beispiel für den Inhalt der Zwischenablage an. Diese Daten werden an die vorhandenen Daten angefügt.  
  
### <a name="paste-replace"></a>Am Ende ersetzen  
 **Vorhandene Daten in der Tabelle**  
 Zeigt ein Beispiel der vorhandenen Daten in der Tabelle an, damit Sie die Spalten, Datentypen usw. überprüfen können.  
  
 **Einzufügende Daten**  
 Zeigt ein Beispiel für den Inhalt der Zwischenablage an. Die vorhandenen Daten in der Zieltabelle werden gelöscht, und die neuen Zeilen werden in die Tabelle eingefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Importieren von Daten &#40;tabellarischen SSAS-&#41;](import-data-ssas-tabular.md)   
 [Unterstützte Datenquellen &#40;tabellarischen SSAS-&#41;](tabular-models/data-sources-supported-ssas-tabular.md)   
 [Festlegen des Datentyps einer Spalte &#40;SSAS – tabellarisch&#41;](tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  
