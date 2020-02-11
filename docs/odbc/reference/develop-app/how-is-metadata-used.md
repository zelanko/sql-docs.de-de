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
ms.openlocfilehash: ab2efd47ca5b5492c67b88261795cf524c440bda
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139008"
---
# <a name="how-is-metadata-used"></a>Wie werden Metadaten verwendet?
Anwendungen erfordern Metadaten für die meisten Resultsetvorgänge. Die Anwendung verwendet z. B. den Datentyp einer Spalte, um zu bestimmen, welche Art von Variable an diese Spalte gebunden werden soll. Die Byte Länge einer Zeichenspalte wird verwendet, um zu bestimmen, wie viel Speicherplatz zum Anzeigen von Daten aus dieser Spalte benötigt wird. Wie eine Anwendung die Metadaten für eine Spalte bestimmt, hängt vom Typ der Anwendung ab.  
  
 Vertikale Anwendungen arbeiten mit vordefinierten Tabellen und führen vordefinierte Vorgänge für diese Tabellen aus. Da die Resultsetmetadaten für solche Anwendungen definiert sind, bevor die Anwendung überhaupt geschrieben und vom Anwendungsentwickler gesteuert wird, kann Sie in der Anwendung hart codiert werden. Wenn beispielsweise eine OrderID-Spalte in der Datenquelle als 4-Byte-Ganzzahl definiert ist, kann die Anwendung stets eine 4-Byte-Ganzzahl an diese Spalte binden. Wenn Metadaten in der Anwendung hartcodiert sind, bedeutet eine Änderung an den von der Anwendung verwendeten Tabelle im Allgemeinen eine Änderung am Anwendungscode. Dies ist selten ein Problem, da diese Änderungen normalerweise im Rahmen einer neuen Version der Anwendung vorgenommen werden.  
  
 Wie bei vertikalen Anwendungen arbeiten benutzerdefinierte Anwendungen in der Regel mit vordefinierten Tabellen und führen vordefinierte Vorgänge für diese Tabellen aus. Beispielsweise kann eine Anwendung zum Übertragen von Daten zwischen drei verschiedenen Datenquellen geschrieben werden. die zu übertragenden Daten sind normalerweise bekannt, wenn die Anwendung geschrieben wird. Daher haben benutzerdefinierte Anwendungen auch tendenziell hart codierte Metadaten.  
  
 Generische Anwendungen, insbesondere solche, die Ad-hoc-Abfragen unterstützen, kennen die Metadaten der erstellten Resultsets fast nie. Daher müssen Sie die Metadaten zur Laufzeit mithilfe der Funktionen **SQLNumResultCols**, **SQLDescribeCol**und **SQLColAttribute**ermitteln, die im nächsten Abschnitt [SQLDescribeCol und SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)beschrieben werden.  
  
 Alle Anwendungen können unabhängig von Ihrem Typ Metadaten für die Resultsets, die von den Katalog Funktionen zurückgegeben werden, hart codieren. Diese Resultsets werden im Verweis Abschnitt dieses Handbuchs definiert.
