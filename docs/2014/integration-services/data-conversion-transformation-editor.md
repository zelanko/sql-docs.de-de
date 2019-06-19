---
title: Transformations-Editor für Datenkonvertierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5346c808c7d724ae630bb3dd25016a9977af363e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060053"
---
# <a name="data-conversion-transformation-editor"></a>Transformations-Editor für Datenkonvertierung
  Im Dialogfeld **Transformations-Editor für Datenkonvertierung** können Sie die zu konvertierenden Spalten und den Datentyp, in den die Spalte konvertiert werden soll, auswählen und Konvertierungsattribute festlegen.  
  
> [!NOTE]  
>  Die `FastParse` -Eigenschaft der Ausgabespalten der Transformation für Datenkonvertierung ist nicht verfügbar, in der **Transformations-Editor für Datenkonvertierung**, aber kann festgelegt werden, mithilfe der **Erweiterter Editor**. Weitere Informationen zu dieser Eigenschaft finden Sie im Abschnitt "Transformation für Datenkonvertierung" von [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Weitere Informationen zur Transformation für Datenkonvertierung finden Sie unter [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Verfügbare Eingabespalten**  
 Wählen Sie mithilfe der Kontrollkästchen die zu konvertierenden Spalten aus. Durch Ihre Auswahl werden der nachfolgenden Tabelle Eingabespalten hinzugefügt.  
  
 **Eingabespalte**  
 Wählen Sie zu konvertierende Spalten aus der Liste der verfügbaren Eingabespalten aus. Ihre Auswahl wird entsprechend in der Auswahl der Kontrollkästchen oben deutlich.  
  
 **Ausgabealias**  
 Geben Sie einen Alias für jede neue Spalte ein. Der Standard lautet `Copy of`, gefolgt vom Namen der Eingabespalte. Sie können jedoch auch einen eindeutigen, beschreibenden Namen auswählen.  
  
 **Datentyp**  
 Wählen Sie einen verfügbaren Datentyp aus der Liste aus. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).  
  
 **Länge**  
 Legt für Zeichenfolgendaten die Spaltenlänge fest.  
  
 **Genauigkeit**  
 Legt für numerische Daten die Genauigkeit fest.  
  
 **Dezimalstellen**  
 Legt für numerische Daten die Dezimalstellen fest.  
  
 **Codepage**  
 Wählen Sie die geeignete Codepage für Spalten vom Typ DT_STR aus.  
  
 **Fehlerausgabe konfigurieren**  
 Geben Sie mithilfe des Dialogfelds [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) an, wie Fehler auf Zeilenebene behandelt werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Konvertieren von Daten in einen anderen Datentyp mithilfe der Transformation für Datenkonvertierung](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
