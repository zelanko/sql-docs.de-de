---
title: Transformations-Editor für abgeleitete Spalte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 3983e75bdde3379fac48a74a595959af2568a3ab
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84951650"
---
# <a name="derived-column-transformation-editor"></a>Transformations-Editor für abgeleitete Spalte
  Mithilfe des Dialogfelds **Transformations-Editor für abgeleitete Spalte** können Sie Ausdrücke erstellen, die neue Spalten oder Ersatzspalten auffüllen.  
  
 Weitere Informationen zur Transformation für abgeleitete Spalten finden Sie unter [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Variablen und Spalten**  
 Erstellen Sie einen Ausdruck, der eine Variable oder eine Eingabespalte verwendet, indem Sie die Variable oder Spalte aus der Liste der verfügbaren Variablen und Spalten in eine vorhandene Tabellenzeile im unteren Bereich oder in eine neue Zeile am Ende der Liste ziehen.  
  
 **Funktionen und Operatoren**  
 Erstellen Sie einen Ausdruck, der eine Funktion oder einen Operator zum Bewerten der Eingabedaten und zum Weiterleiten der Ausgabedaten verwendet, indem Sie die Funktionen und Operatoren aus der Liste in den unteren Bereich ziehen.  
  
 **Name der abgeleiteten Spalte**  
 Geben Sie einen Namen für die abgeleitete Spalte an. Standardwert ist eine nummerierte Liste mit abgeleiteten Spalten; Sie können jedoch einen eindeutigen, beschreibenden Namen auswählen.  
  
 **Abgeleitete Spalte**  
 Wählen Sie eine abgeleitete Spalte aus der Liste aus. Wählen Sie aus, ob die abgeleitete Spalte als neue Ausgabespalte hinzugefügt wird oder die Daten in einer vorhandenen Spalte ersetzt werden.  
  
 **Begriff**  
 Geben Sie einen Ausdruck ein, oder erstellen Sie einen, indem Sie aus der vorherigen Liste der verfügbaren Spalten, Variablen, Funktionen und Operatoren die entsprechenden Teile ziehen.  
  
 Der Wert dieser Eigenschaft kann mithilfe eines Eigenschaftsausdrucks angegeben werden.  
  
 **Verwandte Themen:**[Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Operatoren &#40;SSIS-Ausdruck&#41;](expressions/operators-ssis-expression.md) und [Funktionen &#40;SSIS-Ausdruck&#41;](expressions/functions-ssis-expression.md)  
  
 **Datentyp**  
 Beim Hinzufügen von Daten zu einer neuen Spalte wertet das Dialogfeld **Transformations-Editor für abgeleitete Spalten** automatisch den Ausdruck aus und legt den Datentyp entsprechend fest. Der Wert dieser Spalte ist schreibgeschützt. Weitere Informationen finden Sie unter [Integration Services-Datentypen](data-flow/integration-services-data-types.md).  
  
 **Länge**  
 Beim Hinzufügen von Daten zu einer neuen Spalte wertet das Dialogfeld **Transformations-Editor für abgeleitete Spalten** automatisch den Ausdruck aus und legt die Spaltenlänge für Zeichenfolgendaten entsprechend fest. Der Wert dieser Spalte ist schreibgeschützt.  
  
 **Genauigkeit**  
 Beim Hinzufügen von Daten zu einer neuen Spalte legt das Dialogfeld **Transformations-Editor für abgeleitete Spalten** automatisch die Genauigkeit für numerische Daten basierend auf dem Datentyp fest. Der Wert dieser Spalte ist schreibgeschützt.  
  
 **Skalierung**  
 Beim Hinzufügen von Daten zu einer neuen Spalte legt das Dialogfeld **Transformations-Editor für abgeleitete Spalten** automatisch die Skala für numerische Daten basierend auf dem Datentyp fest. Der Wert dieser Spalte ist schreibgeschützt.  
  
 **Codepage**  
 Beim Hinzufügen von Daten zu einer neuen Spalte legt das Dialogfeld **Transformations-Editor für abgeleitete Spalten** automatisch die Codepage für den DT_STR-Datentyp fest. Sie können den Wert von **Codepage**aktualisieren.  
  
 **Fehlerausgabe konfigurieren**  
 Geben Sie mithilfe des Dialogfelds [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) an, wie Fehler behandelt werden sollen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Ableiten von Spaltenwerten mithilfe der Transformation für abgeleitete Spalten](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  
