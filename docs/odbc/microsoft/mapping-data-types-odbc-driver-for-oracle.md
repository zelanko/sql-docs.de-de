---
title: Zuordnen von Datentypen (ODBC-Treiber für Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 432c21b70efcdd63ef36bfe3d26f8488ddb11d1d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302671"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Zuordnen von Datentypen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Oracle Server unterstützt eine Reihe von Datentypen. Der ODBC-Treiber für Oracle ordnet diese Datentypen den entsprechenden ODBC SQL-Datentypen zu. In der folgenden Tabelle sind die Oracle 7.3 Server-Datentypen und die entsprechenden ODBC SQL-Datentypen aufgeführt.  
  
 Der ODBC-Treiber für Oracle unterstützt Oracle 7.3 und einige Oracle8-Datentypen. Weitere Informationen zu unterstützten Oracle8-Datentypen finden Sie unter [Unterstützte Datentypen](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Oracle Server-Datentyp|ODBC SQL-Datentyp|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|GLEITKOMMAZAHL|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  Weitere Informationen zur zulässigen Größe der VARCHAR-Spalte finden Sie unter [VARCHAR-Spaltengröße](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) in diesem Handbuch.
