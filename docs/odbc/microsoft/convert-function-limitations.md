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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65cc8fa7517d3093b7314cacdafd8f607d89bc3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081996"
---
# <a name="convert-function-limitations"></a>Einschränkungen der CONVERT-Funktion
Typkonvertierungs Fehler führen dazu, dass die betroffene Spalte auf NULL festgelegt wird.  
  
 Weder der Date-noch der timestamp-Datentyp kann von der Convert-Funktion in einen anderen Datentyp (oder selbst) konvertiert werden.
