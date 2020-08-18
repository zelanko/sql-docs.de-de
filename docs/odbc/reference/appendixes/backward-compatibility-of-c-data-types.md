---
description: Abwärtskompatibilität von C-Datentypen
title: Abwärtskompatibilität von C-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e50a07d3c49438fcdfbc0b57ec70380d20c88440
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411316"
---
# <a name="backward-compatibility-of-c-data-types"></a>Abwärtskompatibilität von C-Datentypen
SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT wurden durch signierte und unsignierte Typen in ODBC ersetzt: SQL_C_SSHORT und SQL_C_USHORT, SQL_C_SLONG und SQL_C_ULONG sowie SQL_C_STINYINT und SQL_C_UTINYINT. Ein ODBC *3. x* -Treiber, der mit ODBC *2. x* -Anwendungen funktionieren sollte, sollte SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT unterstützen, denn wenn Sie aufgerufen werden, übergibt der Treiber-Manager Sie an den Treiber.
