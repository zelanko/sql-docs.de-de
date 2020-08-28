---
description: Empfangen von Ergebnissen
title: Empfangene Ergebnisse | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
author: rothja
ms.author: jroth
ms.openlocfilehash: 6fb6a86cb976d8ed8a3c96a10cdca9fd786a5128
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979961"
---
# <a name="receiving-results"></a>Empfangen von Ergebnissen
In ADO werden die meisten Befehle zum Aufrufer zurückgegeben. Für Befehle, die das Rowset zurückgeben, werden die Ergebnisse in einem **Recordset** -Objekt empfangen, das wahrscheinlich die am häufigsten verwendeten ADO-Objekte ist.  
  
 Es gibt mehrere Möglichkeiten, Daten in einem **Recordset** -Objekt aus einer Datenquelle zu empfangen, einschließlich des folgenden:  
  
-   [Connection.Exeniedliche Methode](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command.Exeniedliche Methode](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset. Open-Methode](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection. namedcommand](../../../ado/guide/data/named-commands.md)  
  
-   ["Connection. StoredProcedure"](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Beim Empfangen von Daten in einem **Recordset** -Objekt wird der Prozess zum Empfangen von Daten mit der Teilnahme an einem **Verbindungs** Objekt und einem **Befehls** Objekt (implizit oder explizit) beendet. In einem typischen Client/Server-Anwendungssystem erfordert der gesamte Prozess des abfüllungs von Daten einen Roundtrip über das Netzwerk für jedes gefüllte **Recordset**.  
  
 Um mehr als ein Resultset zu erhalten, müssen Sie mehrere Roundtrips über das Netzwerk durchführen, eine für jedes Dataset, das in einem **Recordset** -Objekt gekapselt ist. Bei langsamen oder überlasteten Netzwerken kann das Reduzieren der Anzahl von Roundtrips dazu beitragen, die Leistung der Anwendung zu verbessern. Aus diesem Grund bieten einige Anbieter Unterstützung für den Empfang mehrerer **Recordsets**in einem einzelnen Roundtrip. Dies wird im folgenden Thema erläutert:  
  
-   [Empfangen von mehreren Recordsets](../../../ado/guide/data/receiving-multiple-recordsets.md)
