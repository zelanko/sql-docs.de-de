---
title: Parameter-Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 152186c0bb1c2fb75197a920e06e0b6bb96dadd0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703315"
---
# <a name="parameter-object"></a>Parameter-Objekt
Stellt einen Parameter oder die zugeordnete Argument ein [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur.  
  
## <a name="remarks"></a>Hinweise  
 Viele Anbieter unterstützt die parametrisierte Befehle. Hierbei handelt es sich um Befehle, die in denen die gewünschte Aktion einmal definiert wird, aber Variablen (oder Parameter) werden verwendet, um einige Details des Befehls alter. Beispielsweise kann eine SQL SELECT-Anweisung einen Parameter verwenden, definieren Sie die entsprechenden Kriterien eine WHERE-Klausel und eine andere, um den Spaltennamen für eine SORT BY-Klausel definieren.  
  
 **Parameter** Objekte darstellen, Parameter, die parametrisierte Abfragen zugeordnet werden soll, oder den in/Out-Argumenten und Rückgabewerten von gespeicherten Prozeduren. Abhängig von den Funktionen von der Anbieter, einige Auflistungen, Methoden oder Eigenschaften eine **Parameter** Objekt möglicherweise nicht zur Verfügung.  
  
 Mit den Auflistungen, Methoden und Eigenschaften einer **Parameter** -Objekts können Sie folgende Möglichkeiten:  
  
-   Festlegen oder Zurückgeben der Name eines Parameters mit dem [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft.  
  
-   Festlegen oder den Wert eines Parameters mit Zurückgeben der [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft. **Wert** ist die Standardeigenschaft der **Parameter** Objekt.  
  
-   Festlegen oder Zurückgeben von Parametereigenschaften mit der [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md), [Richtung](../../../ado/reference/ado-api/direction-property.md), [Genauigkeit](../../../ado/reference/ado-api/precision-property-ado.md), [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md), [ Größe](../../../ado/reference/ado-api/size-property-ado-parameter.md), und [Typ](../../../ado/reference/ado-api/type-property-ado.md) Eigenschaften.  
  
-   Übergeben Sie lange Binär-oder Zeichendatentypen an einen Parameter mit dem [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) Methode.  
  
-   Zugriff auf Anbieter-spezifischen Attribute mithilfe der [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
 Wenn Sie wissen, dass die Namen und zugeordnete Eigenschaften der Parameter der gespeicherten Prozedur oder eine parametrisierte Abfrage, die Sie aufrufen möchten, können Sie die [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) Methode zum Erstellen **Parameter** Objekte und die entsprechenden Einstellungen und die Verwendung der [Append](../../../ado/reference/ado-api/append-method-ado.md) Methode zum Hinzufügen der [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung. Auf diese Weise können Sie festlegen und Zurückgeben von Werten ohne Aufruf der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode für die **Parameter** Auflistung abzurufende die Parameterinformationen vom Anbieter, eine potenziell ressourcenintensiver Vorgang.  
  
 Die **Parameter** Objekt ist nicht sicher für Skripting.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Parameter-Objekteigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Parameters-Auflistung (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
