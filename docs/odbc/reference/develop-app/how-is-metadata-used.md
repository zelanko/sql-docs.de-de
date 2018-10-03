---
title: Wie werden Metadaten verwendet? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3604e9f3bd47a10ae1a6e5ec401b198675c2d3e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637048"
---
# <a name="how-is-metadata-used"></a>Wie werden Metadaten verwendet?
Anwendungen erfordern Metadaten für die meisten Resultsetvorgänge. Die Anwendung verwendet z. B. den Datentyp einer Spalte, um zu bestimmen, welche Art von Variable an diese Spalte gebunden werden soll. Er verwendet die Bytelänge einer Zeichenspalte, um zu bestimmen, wie viel Speicherplatz, Daten aus dieser Spalte angezeigt werden muss. Wie eine Anwendung die Metadaten für eine Spalte bestimmt, hängt vom Typ der Anwendung ab.  
  
 Vertikale Anwendungen funktionieren mit vordefinierten Tabellen und führen vordefinierte Vorgänge auf diese Tabellen. Da die resultsetmetadaten für solche Anwendungen definiert ist, bevor die Anwendung überhaupt geschrieben und wird durch den Entwickler der Anwendung gesteuert wird, kann es in der Anwendung hartcodiert sein. Wenn beispielsweise eine OrderID-Spalte in der Datenquelle als 4-Byte-Ganzzahl definiert ist, kann die Anwendung stets eine 4-Byte-Ganzzahl an diese Spalte binden. Wenn Metadaten in der Anwendung hartcodiert sind, bedeutet eine Änderung an den von der Anwendung verwendeten Tabelle im Allgemeinen eine Änderung am Anwendungscode. Dies ist nur selten ein Problem, da solche Änderungen in der Regel als Teil einer neuen Version der Anwendung vorgenommen werden.  
  
 Wie vertikale Anwendungen wird benutzerdefinierte Anwendungen in der Regel mit vordefinierten Tabellen arbeiten, und führen vordefinierte Vorgänge auf diese Tabellen. Beispielsweise könnte eine Anwendung geschrieben werden, zum Übertragen von Daten zwischen drei verschiedenen Datenquellen; der zu übertragenden Daten werden in der Regel bezeichnet, wenn die Anwendung geschrieben wird. Daher sind tendenziell benutzerdefinierte Anwendungen auch hartcodierte Metadaten auf.  
  
 Allgemeiner Anwendungen, insbesondere über diejenigen, die ad-hoc-Abfragen unterstützt, die fast nie wissen, die Metadaten des Resultsets, die sie erstellen. Aus diesem Grund müssen sie die Metadaten zur Laufzeit mithilfe der Funktionen ermittelt **SQLNumResultCols**, **SQLDescribeCol**, und **SQLColAttribute**, die beschrieben werden, der nächsten Abschnitt [SQLDescribeCol und SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md).  
  
 Alle Anwendungen, unabhängig von deren Typ, können es sich um hartcodieren-Metadaten für den Resultsets, die durch die Katalogfunktionen zurückgegeben. Diese Resultsets werden im Abschnitt "Referenz" dieses Handbuchs definiert.
