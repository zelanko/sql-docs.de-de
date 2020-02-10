---
title: Quellen-Editor für Flatfiles (Seite Spalten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f8fda95b51f568098b0ac9fc13b8a204adb71c51
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058608"
---
# <a name="flat-file-source-editor-columns-page"></a>Quellen-Editor für Flatfiles (Seite Spalten)
  Mithilfe des Knotens **Spalten** des Dialogfelds **Quellen-Editor für Flatfiles** können Sie jeder externen (Quell-)Spalte eine Ausgabespalte zuordnen.  
  
> [!NOTE]  
>  Die `FileNameColumnName` -Eigenschaft der Flatfilequelle und die `FastParse` -Eigenschaft ihrer Ausgabespalten sind nicht im Quellen- **Editor für Flatfiles**verfügbar, können jedoch mit dem- **Erweiterter Editor**festgelegt werden. Weitere Informationen zu diesen Eigenschaften finden Sie im Abschnitt Flatfilequelle von [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Weitere Informationen zur Flatfilequelle finden Sie unter [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Tastatur  
 **Verfügbare externe Spalten**  
 Zeigt die Liste der in der Datenquelle verfügbaren externen Spalten an. Mit der Tabelle können keine Spalten hinzugefügt oder gelöscht werden.  
  
 **Externe Spalte**  
 Zeigt die externen (Quell-)Spalten in der Reihenfolge an, in der sie von dem Task gelesen werden. Sie können die Reihenfolge ändern, indem Sie zunächst die ausgewählten Spalten in der Tabelle löschen. Wählen Sie anschließend die externen Spalten in einer anderen Reihenfolge aus der Liste aus.  
  
 **Ausgabespalte**  
 Geben Sie für jede Ausgabespalte einen eindeutigen Namen an. Standardmäßig wird der Name der ausgewählten externen (Quell-)Spalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Quellen-Editor für Flatfiles &#40;Seite Verbindungs-Manager&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Quellen-Editor für Flatfiles &#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Verbindungs-Manager für Flatfiles](connection-manager/file-connection-manager.md)  
  
  
