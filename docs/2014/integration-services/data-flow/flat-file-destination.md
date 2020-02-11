---
title: Flatfileziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 30f8f566dc04726076dd9eb7c4d91b56f687218d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62902445"
---
# <a name="flat-file-destination"></a>Flatfileziel
  Das Flatfileziel schreibt Daten in eine Textdatei. Die Textdatei kann in verschiedenen Formaten vorliegen: mit Trennzeichen, mit fester Breite, mit fester Breite mit Zeilentrennzeichen oder mit rechtem Flatterrand.  
  
 Es gibt folgende Möglichkeiten, um das Flatfileziel zu konfigurieren:  
  
-   Geben Sie einen Textblock an, der in die Datei eingefügt wird, bevor Daten geschrieben werden. Der Text kann Informationen bereitstellen, wie z. B. Spaltenüberschriften.  
  
-   Geben Sie an, ob Daten in einer gleichnamigen Zieldatei überschrieben werden sollen.  
  
 Dieses Ziel verwendet für den Zugriff auf die Textdatei einen Verbindungs-Manager für Flatfiles. Durch Festlegen von Eigenschaften im Verbindungs-Manager für Flatfiles, der vom Flatfileziel verwendet wird, können Sie angeben, wie das Flatfileziel die Textdatei formatiert und schreibt. Wenn Sie den Verbindungs-Manager für Flatfiles konfigurieren, geben Sie Informationen zur Datei und zu jeder Spalte in der Datei an. Beispielsweise können Sie die Zeichen angeben, mit denen Spalten und Zeilen in der Datei getrennt werden, sowie den Datentyp und die Länge jeder Spalte. Weitere Informationen finden Sie unter [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Das Flatfileziel schließt die benutzerdefinierte Header-Eigenschaft ein. Diese Eigenschaft kann beim Laden des Pakets mithilfe eines Eigenschaftsausdrucks aktualisiert werden. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md), [Verwenden von Eigenschaftsausdrücken in Paketen](../expressions/use-property-expressions-in-packages.md) und [Benutzerdefinierte Eigenschaften der Flatfile](flat-file-custom-properties.md).  
  
 Das Ziel weist eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-flat-file-destination"></a>Konfiguration des Flatfileziels  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Quellen-Editor für Flatfiles** festlegen können:  
  
-   [Ziel-Editor für Flatfiles &#40;Seite Verbindungs-Manager&#41;](../flat-file-destination-editor-connection-manager-page.md)  
  
-   [Ziel-Editor für Flatfiles &#40;Seite Zuordnungen&#41;](../flat-file-destination-editor-mappings-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der Flatfile](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften einer Datenflusskomponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Flatfilequelle](flat-file-source.md)   
 [Datenfluss](data-flow.md)  
  
  
