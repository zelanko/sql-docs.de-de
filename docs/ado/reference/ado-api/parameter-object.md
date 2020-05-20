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
author: rothja
ms.author: jroth
ms.openlocfilehash: 22af5fadda96adbe67c1c03aaa5cde3527df1113
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759996"
---
# <a name="parameter-object"></a>Parameter-Objekt
Stellt einen Parameter oder ein Argument dar, der einem [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur zugeordnet ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Viele Anbieter unterstützen parametrisierte Befehle. Dabei handelt es sich um Befehle, bei denen die gewünschte Aktion einmal definiert ist, aber Variablen (oder Parameter) zum Ändern einiger Details des Befehls verwendet werden. Beispielsweise könnte eine SQL-SELECT-Anweisung einen-Parameter verwenden, um die Übereinstimmungs Kriterien einer WHERE-Klausel zu definieren, und einen anderen zum Definieren des Spaltennamens für eine Sort by-Klausel.  
  
 **Parameter** Objekte stellen Parameter dar, die parametrisierten Abfragen zugeordnet sind, oder die in/out-Argumente und die Rückgabewerte gespeicherter Prozeduren. Abhängig von der Funktionalität des Anbieters sind einige Auflistungen, Methoden oder Eigenschaften eines **Parameter** Objekts möglicherweise nicht verfügbar.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Parameter** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Legen Sie den Namen eines Parameters mit der Eigenschaft [Name](../../../ado/reference/ado-api/name-property-ado.md) fest, oder geben Sie ihn zurück.  
  
-   Legen Sie den Wert eines Parameters mit der [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft fest oder geben Sie ihn zurück. **Value** ist die Standard Eigenschaft des **Parameter** Objekts.  
  
-   Festlegen oder Zurückgeben von Parameter Merkmalen mit den Eigenschaften [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md), [Richtung](../../../ado/reference/ado-api/direction-property.md), [Genauigkeit](../../../ado/reference/ado-api/precision-property-ado.md), [numericskala](../../../ado/reference/ado-api/numericscale-property-ado.md), [Größe](../../../ado/reference/ado-api/size-property-ado-parameter.md)und [Typ](../../../ado/reference/ado-api/type-property-ado.md) .  
  
-   Übergeben Sie lange Binär-oder Zeichendaten an einen Parameter mit der [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) -Methode.  
  
-   Greifen Sie mithilfe der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Attribute zu.  
  
 Wenn Sie die Namen und Eigenschaften der Parameter kennen, die der gespeicherten Prozedur oder der parametrisierten Abfrage zugeordnet sind, die Sie aufrufen möchten, können Sie mit der Methode "| [ateparameter](../../../ado/reference/ado-api/createparameter-method-ado.md) " **Parameter** Objekte mit den entsprechenden Eigenschafts Einstellungen erstellen und die [Append](../../../ado/reference/ado-api/append-method-ado.md) -Methode verwenden, um Sie der [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung hinzuzufügen. Dies ermöglicht es Ihnen, Parameterwerte festzulegen und zurückzugeben, ohne die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode für die **Parameter** Auflistung aufrufen zu müssen, um die Parameterinformationen vom Anbieter abzurufen, ein potenziell ressourcenintensiver Vorgang.  
  
 Das **Parameter** Objekt ist für die Skripterstellung nicht sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Parameter Objekteigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Kreateparameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Parameter Auflistung (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
