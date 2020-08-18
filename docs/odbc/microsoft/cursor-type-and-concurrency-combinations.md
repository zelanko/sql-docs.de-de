---
description: Cursortyp und Parallelitätskombinationen
title: Cursor-und Parallelitäts Kombinationen | Microsoft-Dokumentation
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
ms.openlocfilehash: ae82825f7b5c6f670e111b859ee02ab4ab875626
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412901"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Cursortyp und Parallelitätskombinationen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Cursor Typen steuern die Funktionalität des Cursors, der für den Benutzer bereitgestellt wird. Parallelitäts Optionen steuern das Aktualisier barkeits-und Sperr Verhalten eines Resultsets.  
  
|Cursortyp|Parallelität (zulässige Werte)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup> siehe [Einschränkungen bei der Verwendung von keysetgesteuerten Cursorn](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2]</sup> SQL_CONCUR_LOCK wird nur unterstützt, wenn die SQL_AUTOCOMMIT-Verbindungs Option auf "SQL_AUTOCOMMIT_OFF" festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungsoption](../../odbc/microsoft/connect-options.md)
