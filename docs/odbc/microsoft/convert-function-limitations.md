---
title: Einschränkungen für die Konvertierung von Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, CONVERT function limitations
- Convert function limitations [ODBC]
ms.assetid: 3c81fc58-57f0-4dd7-be16-2b146eb15cbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63f4258e737327ae11f03a96cfef3cdecf133e53
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281030"
---
# <a name="convert-function-limitations"></a>Einschränkungen der CONVERT-Funktion
Typkonvertierungs Fehler führen dazu, dass die betroffene Spalte auf NULL festgelegt wird.  
  
 Weder der Date-noch der timestamp-Datentyp kann von der Convert-Funktion in einen anderen Datentyp (oder selbst) konvertiert werden.
