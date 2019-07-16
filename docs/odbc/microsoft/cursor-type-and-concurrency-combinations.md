---
title: Cursortyp und Parallelitätskombinationen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a29fc2d02cb46dda44fa22b2344cbab475443f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096528"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Cursortyp und Parallelitätskombinationen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Cursortypen steuern, die Funktionalität des Cursors an den Benutzer bereitgestellt wird. Optionen der Cursorparallelität aktualisierbarkeit und Sperrverhalten eines Resultsets steuern.  
  
|Cursortyp|Parallelität (zulässige Werte)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1] </sup> Finden Sie unter [Einschränkungen bei der Verwendung keysetgesteuerter Cursor](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2] </sup> SQL_CONCUR_LOCK wird nur unterstützt, wenn die Verbindungsoption SQL_AUTOCOMMIT auf SQL_AUTOCOMMIT_OFF festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Verbindungsoption](../../odbc/microsoft/connect-options.md)
