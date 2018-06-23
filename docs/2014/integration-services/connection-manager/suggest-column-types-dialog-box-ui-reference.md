---
title: Referenz zur Benutzeroberfläche des Dialogfelds „Spaltentypen vorschlagen“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.suggestdatatypes.f1
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0fbb0e83bda9f5a7f5b5f10705ef1b770e3205f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160953"
---
# <a name="suggest-column-types-dialog-box-ui-reference"></a>Referenz zur Benutzeroberfläche des Dialogfelds Spaltentypen vorschlagen
  Identifizieren Sie mithilfe des Dialogfelds **Spaltentypen vorschlagen** den Datentyp und die -länge von Spalten im Verbindungs-Manager für Flatfiles basierend auf einer Stichprobe für den Dateiinhalt.  
  
 Weitere Informationen zu den von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]verwendeten Datentypen, finden Sie unter [Integration Services-Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="options"></a>Tastatur  
 **Anzahl von Zeilen**  
 Geben Sie die Anzahl der Zeilen im vom Algorithmus verwendeten Beispiel an, oder wählen Sie die Anzahl aus.  
  
 **Den kleinsten integer-Datentyp vorschlagen**  
 Deaktivieren Sie dieses Kontrollkästchen, um die Analyse auszulassen. Wenn dieses Kontrollkästchen aktiviert ist, bestimmt es den kleinsten integer-Datentyp für Spalten, die numerische Daten vom integer-Typ enthalten.  
  
 **Den kleinsten Real-Datentyp vorschlagen**  
 Deaktivieren Sie dieses Kontrollkästchen, um die Analyse auszulassen. Wenn dieses Kontrollkästchen aktiviert ist, bestimmt es, ob Spalten mit numerischen Daten vom real-Typ den kleineren real-Datentyp, DT_R4, verwenden können.  
  
 **Boolesche Spalten mithilfe der folgenden Werte identifizieren**  
 Geben Sie die beiden Werte ein, die Sie als die booleschen Werte für true und false verwenden möchten. Die Werte müssen durch ein Komma getrennt sein. Der erste Wert repräsentiert True.  
  
 **Auffüllung zu Zeichenfolgenspalten hinzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um die Zeichenfolgenauffüllung zu aktivieren.  
  
 **Prozentsatz der Auffüllung**  
 Geben Sie den Prozentsatz der Spaltenlänge ein, um den die Länge von Spalten für Zeichendatentypen vergrößert werden soll, oder wählen Sie den Wert aus. Der Prozentsatz muss als ganze Zahl angegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../integration-services-error-and-message-reference.md)   
 [Verbindungs-Manager für Flatfiles](file-connection-manager.md)  
  
  