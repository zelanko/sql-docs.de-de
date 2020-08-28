---
description: Parameter-Objekt
title: Parameter-Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 123ca1553ede61735565a6f82cb36b0035c56dcb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990171"
---
# <a name="parameter-object"></a>Parameter-Objekt
Stellt einen Parameter oder ein Argument dar, der einem [Befehls](./command-object-ado.md) Objekt auf Grundlage einer parametrisierten Abfrage oder gespeicherten Prozedur zugeordnet ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Viele Anbieter unterstützen parametrisierte Befehle. Dabei handelt es sich um Befehle, bei denen die gewünschte Aktion einmal definiert ist, aber Variablen (oder Parameter) zum Ändern einiger Details des Befehls verwendet werden. Beispielsweise könnte eine SQL-SELECT-Anweisung einen-Parameter verwenden, um die Übereinstimmungs Kriterien einer WHERE-Klausel zu definieren, und einen anderen zum Definieren des Spaltennamens für eine Sort by-Klausel.  
  
 **Parameter** Objekte stellen Parameter dar, die parametrisierten Abfragen zugeordnet sind, oder die in/out-Argumente und die Rückgabewerte gespeicherter Prozeduren. Abhängig von der Funktionalität des Anbieters sind einige Auflistungen, Methoden oder Eigenschaften eines **Parameter** Objekts möglicherweise nicht verfügbar.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Parameter** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Legen Sie den Namen eines Parameters mit der Eigenschaft [Name](./name-property-ado.md) fest, oder geben Sie ihn zurück.  
  
-   Legen Sie den Wert eines Parameters mit der [value](./value-property-ado.md) -Eigenschaft fest oder geben Sie ihn zurück. **Value** ist die Standard Eigenschaft des **Parameter** Objekts.  
  
-   Festlegen oder Zurückgeben von Parameter Merkmalen mit den Eigenschaften [Attribute](./attributes-property-ado.md), [Richtung](./direction-property.md), [Genauigkeit](./precision-property-ado.md), [numericskala](./numericscale-property-ado.md), [Größe](./size-property-ado-parameter.md)und [Typ](./type-property-ado.md) .  
  
-   Übergeben Sie lange Binär-oder Zeichendaten an einen Parameter mit der [AppendChunk](./appendchunk-method-ado.md) -Methode.  
  
-   Greifen Sie mithilfe der [Properties](./properties-collection-ado.md) -Auflistung auf anbieterspezifische Attribute zu.  
  
 Wenn Sie die Namen und Eigenschaften der Parameter kennen, die der gespeicherten Prozedur oder der parametrisierten Abfrage zugeordnet sind, die Sie aufrufen möchten, können Sie mit der Methode "| [ateparameter](./createparameter-method-ado.md) " **Parameter** Objekte mit den entsprechenden Eigenschafts Einstellungen erstellen und die [Append](./append-method-ado.md) -Methode verwenden, um Sie der [Parameter](./parameters-collection-ado.md) Auflistung hinzuzufügen. Dies ermöglicht es Ihnen, Parameterwerte festzulegen und zurückzugeben, ohne die [Refresh](./refresh-method-ado.md) -Methode für die **Parameter** Auflistung aufrufen zu müssen, um die Parameterinformationen vom Anbieter abzurufen, ein potenziell ressourcenintensiver Vorgang.  
  
 Das **Parameter** Objekt ist für die Skripterstellung nicht sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Parameter Objekteigenschaften, Methoden und Ereignisse](./parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Command-Objekt (ADO)](./command-object-ado.md)   
 [Kreateparameter-Methode (ADO)](./createparameter-method-ado.md)   
 [Parameter Auflistung (ADO)](./parameters-collection-ado.md)   
 [Properties-Collection (ADO)](./properties-collection-ado.md)