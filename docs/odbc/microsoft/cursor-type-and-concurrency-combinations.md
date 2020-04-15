---
title: Cursortyp und Parallelitätskombinationen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6397b5d675546bf41102f037b68c0022bec74df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280770"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Cursortyp und Parallelitätskombinationen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Cursortypen steuern die Funktionalität des Cursors, der dem Benutzer zur Verfügung gestellt wird. Parallelitätsoptionen steuern die Aufstandbarkeit und das Sperrverhalten eines Resultsets.  
  
|Cursortyp|Parallelität (zulässige Werte)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup> Siehe [Einschränkungen der Verwendung von Keyset-gesteuerten Cursorn](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2]</sup> SQL_CONCUR_LOCK wird nur unterstützt, wenn die SQL_AUTOCOMMIT Verbindungsoption auf SQL_AUTOCOMMIT_OFF festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungsoption](../../odbc/microsoft/connect-options.md)
