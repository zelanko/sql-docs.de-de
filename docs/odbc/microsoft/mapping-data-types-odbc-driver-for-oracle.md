---
title: Zuordnung von Datentypen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 47646fd6fdf1e8fd16165af1bcfc5e741c6e610f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080740"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Zuordnen von Datentypen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Oracle-Server unterstützt einen Satz von Datentypen. Der ODBC-Treiber für Oracle ordnet diese Datentypen den entsprechenden ODBC-SQL-Datentypen zu. In der folgenden Tabelle werden die Oracle 7,3-Server Datentypen und ihre entsprechenden ODBC-SQL-Datentypen aufgelistet.  
  
 Der ODBC-Treiber für Oracle unterstützt Oracle 7,3 und einige Oracle8-Datentypen. Weitere Informationen zu unterstützten Oracle8-Datentypen finden Sie [unter Unterstützte Datentypen](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Oracle-Server Datentyp|ODBC SQL-Datentyp|  
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
>  Weitere Informationen zur zulässigen Größe der varchar-Spalte finden Sie in diesem Handbuch unter [varchar Column size](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) .
