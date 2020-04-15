---
title: Verwenden von concise Enisen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306781"
---
# <a name="using-concise-functions"></a>Verwenden präziser Funktionen
Einige ODBC-Funktionen erhalten impliziten Zugriff auf Deskriptoren. Anwendungsautoren finden sie möglicherweise bequemer als das Aufrufen von **SQLSetDescField** oder **SQLGetDescField**. Diese Funktionen werden als *Prägnanzfunktionen* bezeichnet, da sie eine Reihe von Funktionen ausführen, einschließlich des Festlegens oder Abrufens von Deskriptorfeldern. Einige präzise Funktionen ermöglichen es einer Anwendung, mehrere verwandte Deskriptorfelder in einem einzelnen Funktionsaufruf festzulegen oder abzurufen.  
  
 Concise-Funktionen können aufgerufen werden, ohne vorher ein Deskriptor-Handle für die Verwendung als Argument abzurufen. Diese Funktionen arbeiten mit den Deskriptorfeldern, die dem Anweisungshandle zugeordnet sind, zu dem sie aufgerufen werden.  
  
 Die prägnanten Funktionen **SQLBindCol** und **SQLBindParameter** binden eine Spalte oder einen Parameter, indem sie die Deskriptorfelder festlegen, die ihren Argumenten entsprechen. Jede dieser Funktionen führt mehr Aufgaben aus, als einfach Deskriptoren festzulegen. **SQLBindCol** und **SQLBindParameter** stellen eine vollständige Spezifikation der Bindung einer Datenspalte oder eines dynamischen Parameters bereit. Eine Anwendung kann jedoch einzelne Details einer Bindung ändern, indem sie **SQLSetDescField** oder **SQLSetDescRec** aufruft und eine Spalte oder einen Parameter vollständig bindet, indem sie eine Reihe geeigneter Aufrufe für diese Funktionen ausarbeitet.  
  
 Die Prägnanten Funktionen **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**und **SQLNumResultCols** rufen Werte in Deskriptorfeldern ab.  
  
 **SQLSetDescRec** und **SQLGetDescRec** sind präzise Funktionen, die mit einem Aufruf mehrere Deskriptorfelder festlegen oder abrufen, die sich auf den Datentyp und die Speicherung von Spalten- oder Parameterdaten auswirken. **SQLSetDescRec** ist eine effektive Möglichkeit, die Bindung von Spalten- oder Parameterdaten in einem Schritt zu ändern.  
  
 **SQLSetStmtAttr** und **SQLGetStmtAttr** dienen in einigen Fällen als prägnante Funktionen. (Siehe [Deskriptorfelder](../../../odbc/reference/develop-app/descriptor-fields.md).)
