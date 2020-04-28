---
title: Verwenden von präzisen Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63313e3dfaec8dbcd91f3bb084bbaab46da40c6e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306781"
---
# <a name="using-concise-functions"></a>Verwenden präziser Funktionen
Einige ODBC-Funktionen erhalten impliziten Zugriff auf Deskriptoren. Anwendungs Schreiber finden Sie möglicherweise bequemer als das Aufrufen von **SQLSetDescField** oder **SQLGetDescField**. Diese Funktionen werden als *präzise* Funktionen bezeichnet, da Sie eine Reihe von Funktionen ausführen, einschließlich dem Festlegen oder dem erhalten von Deskriptorfeldern. Einige präzise Funktionen ermöglichen es einer Anwendung, mehrere verwandte Deskriptorfelder in einem einzelnen Funktions aufzurufen festzulegen oder abzurufen.  
  
 Präzise Funktionen können aufgerufen werden, ohne zuerst ein Deskriptorhandle für die Verwendung als Argument abzurufen. Diese Funktionen funktionieren mit den Deskriptorfeldern, die dem Anweisungs Handle zugeordnet sind, für das Sie aufgerufen werden.  
  
 Die präzisen Funktionen **SQLBindCol** und **SQLBindParameter** binden eine Spalte oder einen Parameter durch Festlegen der Deskriptorfelder, die ihren Argumenten entsprechen. Jede dieser Funktionen führt mehr Aufgaben aus, als einfach nur Deskriptoren festzulegen. **SQLBindCol** und **SQLBindParameter** stellen eine umfassende Spezifikation der Bindung einer Datenspalte oder eines dynamischen Parameters bereit. Eine Anwendung kann jedoch einzelne Details einer Bindung durch Aufrufen von **SQLSetDescField** oder **SQLSetDescRec** ändern und eine Spalte oder einen Parameter vollständig binden, indem er eine Reihe geeigneter Aufrufe dieser Funktionen durchführen kann.  
  
 Die präzisen Funktionen **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**und **SQLNumResultCols** rufen Werte in Deskriptorfeldern ab.  
  
 **SQLSetDescRec** und **SQLGetDescRec** sind präzise Funktionen, die mit einem-Befehl mehrere Deskriptorfelder festlegen oder abrufen können, die sich auf den Datentyp und die Speicherung von Spalten-oder Parameterdaten auswirken. **SQLSetDescRec** ist eine effektive Möglichkeit, die Bindung von Spalten-oder Parameterdaten in einem Schritt zu ändern.  
  
 **SQLSetStmtAttr** und **SQLGetStmtAttr** dienen in einigen Fällen als präzise Funktionen. (Siehe [Deskriptorfelder](../../../odbc/reference/develop-app/descriptor-fields.md).)
