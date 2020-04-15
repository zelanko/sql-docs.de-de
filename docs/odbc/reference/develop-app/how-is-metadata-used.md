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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbbba96fa2e99a2ccc0618f31e3b29e7d479f703
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300170"
---
# <a name="how-is-metadata-used"></a>Wie werden Metadaten verwendet?
Anwendungen erfordern Metadaten für die meisten Resultsetvorgänge. Die Anwendung verwendet z. B. den Datentyp einer Spalte, um zu bestimmen, welche Art von Variable an diese Spalte gebunden werden soll. Es verwendet die Bytelänge einer Zeichenspalte, um zu bestimmen, wie viel Speicherplatz benötigt wird, um Daten aus dieser Spalte anzuzeigen. Wie eine Anwendung die Metadaten für eine Spalte bestimmt, hängt vom Typ der Anwendung ab.  
  
 Vertikale Anwendungen arbeiten mit vordefinierten Tabellen und führen vordefinierte Vorgänge für diese Tabellen aus. Da die Metadaten des Resultsets für solche Anwendungen definiert werden, bevor die Anwendung überhaupt geschrieben wird, und vom Anwendungsentwickler gesteuert wird, kann sie in der Anwendung hartcodiert werden. Wenn beispielsweise eine OrderID-Spalte in der Datenquelle als 4-Byte-Ganzzahl definiert ist, kann die Anwendung stets eine 4-Byte-Ganzzahl an diese Spalte binden. Wenn Metadaten in der Anwendung hartcodiert sind, bedeutet eine Änderung an den von der Anwendung verwendeten Tabelle im Allgemeinen eine Änderung am Anwendungscode. Dies ist selten ein Problem, da solche Änderungen in der Regel als Teil einer neuen Version der Anwendung vorgenommen werden.  
  
 Wie vertikale Anwendungen arbeiten benutzerdefinierte Anwendungen im Allgemeinen mit vordefinierten Tabellen und führen vordefinierte Vorgänge für diese Tabellen aus. Beispielsweise kann eine Anwendung geschrieben werden, um Daten zwischen drei verschiedenen Datenquellen zu übertragen. die zu übertragenden Daten sind in der Regel bekannt, wenn die Anwendung geschrieben wird. Daher verfügen benutzerdefinierte Anwendungen in der Regel auch über hartcodierte Metadaten.  
  
 Generische Anwendungen, insbesondere solche, die Ad-hoc-Abfragen unterstützen, kennen fast nie die Metadaten der von ihnen erstellten Ergebnissätze. Daher müssen sie die Metadaten zur Laufzeit mithilfe der Funktionen **SQLNumResultCols**, **SQLDescribeCol**und **SQLColAttribute**ermitteln, die im nächsten Abschnitt [SQLDescribeCol und SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)beschrieben werden.  
  
 Alle Anwendungen können unabhängig von ihrem Typ Metadaten für die von den Katalogfunktionen zurückgegebenen Resultsets hartcodieren. Diese Resultsets sind im Referenzabschnitt dieses Handbuchs definiert.
