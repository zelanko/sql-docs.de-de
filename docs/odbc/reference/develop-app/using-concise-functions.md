---
title: Verwenden präziser Funktionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43004601845d3032d404c308b7b1fa4850f694ee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022192"
---
# <a name="using-concise-functions"></a>Verwenden präziser Funktionen
Einige ODBC-Funktionen erhalten die impliziten Zugriff auf die Deskriptoren. Anwendungsentwickler vielleicht finden Sie diese besser geeignet als die Aufrufen **SQLSetDescField** oder **SQLGetDescField**. Diese Funktionen aufgerufen werden *präzise* funktioniert, da sie eine Reihe von Funktionen, einschließlich festlegen oder Abrufen von deskriptorfelder ausführen. Einige präzisen Funktionen können eine Anwendung festgelegt oder abgerufen werden mehrere verwandte Descriptor-Felder in einem einzigen Funktionsaufruf.  
  
 Präzise Funktionen können aufgerufen werden, ohne zuerst einen Deskriptorhandle für die Verwendung als ein Argument abzurufen. Diese Funktionen funktionieren mit der deskriptorfelder das Anweisungshandle zugeordnet, denen auf dem sie aufgerufen werden.  
  
 Die präzisen Funktionen **SQLBindCol** und **SQLBindParameter** binden Sie eine Spalte oder des Parameters, indem Sie die deskriptorfelder, die entsprechen, die ihre Argumente festlegen. Jede dieser Funktionen führt mehr Aufgaben als das Festlegen der Deskriptoren. **SQLBindCol** und **SQLBindParameter** bieten vollständige Spezifikation der Bindung einer Datenspalte oder den dynamischen Parameter. Eine Anwendung kann jedoch die einzelnen Details einer Bindung ändern, indem Aufrufen **SQLSetDescField** oder **SQLSetDescRec** und können vollständig Binden einer Spalte oder Parameter, die eine Reihe von geeigneten aufrufen Diese Funktionen.  
  
 Die präzisen Funktionen **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, und  **SQLNumResultCols** Werte in deskriptorfeldern abrufen.  
  
 **SQLSetDescRec** und **SQLGetDescRec** präzise Funktionen, die mit einem einzigen Aufruf festlegen oder Abrufen von mehreren deskriptorfelder, die den Datentyp und die Speicherung von Daten für Spalte oder Parameter zu beeinflussen. **SQLSetDescRec** ist eine effektive Methode, die Bindung der Spalte oder des Parameters-Daten in einem Schritt ändern.  
  
 **SQLSetStmtAttr** und **SQLGetStmtAttr** als präziser Funktionen in einigen Fällen dienen. (Finden Sie unter [Deskriptorfelder](../../../odbc/reference/develop-app/descriptor-fields.md).)
