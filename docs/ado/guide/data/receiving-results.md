---
title: Empfangene Ergebnisse | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b861553e9a71ce56377f8d87bba0f9e26e929c2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924523"
---
# <a name="receiving-results"></a>Empfangen von Ergebnissen
In ADO werden die meisten Befehle zum Aufrufer zurückgegeben. Für Befehle, die das Rowset zurückgeben, werden die Ergebnisse in einem **Recordset** -Objekt empfangen, das wahrscheinlich die am häufigsten verwendeten ADO-Objekte ist.  
  
 Es gibt mehrere Möglichkeiten, Daten in einem **Recordset** -Objekt aus einer Datenquelle zu empfangen, einschließlich des folgenden:  
  
-   [Connection. Execute-Methode](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command. Execute-Methode](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset. Open-Methode](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection. namedcommand](../../../ado/guide/data/named-commands.md)  
  
-   ["Connection. StoredProcedure"](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Beim Empfangen von Daten in einem **Recordset** -Objekt wird der Prozess zum Empfangen von Daten mit der Teilnahme an einem **Verbindungs** Objekt und einem **Befehls** Objekt (implizit oder explizit) beendet. In einem typischen Client/Server-Anwendungssystem erfordert der gesamte Prozess des abfüllungs von Daten einen Roundtrip über das Netzwerk für jedes gefüllte **Recordset**.  
  
 Um mehr als ein Resultset zu erhalten, müssen Sie mehrere Roundtrips über das Netzwerk durchführen, eine für jedes Dataset, das in einem **Recordset** -Objekt gekapselt ist. Bei langsamen oder überlasteten Netzwerken kann das Reduzieren der Anzahl von Roundtrips dazu beitragen, die Leistung der Anwendung zu verbessern. Aus diesem Grund bieten einige Anbieter Unterstützung für den Empfang mehrerer **Recordsets**in einem einzelnen Roundtrip. Dies wird im folgenden Thema erläutert:  
  
-   [Empfangen von mehreren Recordsets](../../../ado/guide/data/receiving-multiple-recordsets.md)
