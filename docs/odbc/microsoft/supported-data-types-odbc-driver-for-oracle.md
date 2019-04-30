---
title: Unterstützte Datentypen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 219a6d2e837280ca3220382bea56d2ab610ce87a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270884"
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>Unterstützte Datentypen (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Der ODBC-Treiber für Oracle unterstützt alle Datentypen von Oracle 7.3. Allerdings unterstützt es eines der neuen 8-Datentypen, die hier aufgeführten nicht.  
  
|Datentyp|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|–|Nicht unterstützt|  
|BLOB|–|Nicht unterstützt|  
|CHAR|Supported|Supported|  
|CLOB|–|Nicht unterstützt|  
|DATE|Supported|Supported|  
|GLEITKOMMAZAHL|Supported|Supported|  
|INTEGER|Supported|Supported|  
|LONG|Supported|Supported|  
|LONG RAW|Supported|Supported|  
|NCHAR|–|Nicht unterstützt|  
|NCLOB|–|Nicht unterstützt|  
|NUMBER|Supported|Supported|  
|NVARCHAR2|–|Nicht unterstützt|  
|RAW|Supported|Supported|  
|VARCHAR2|Supported|Supported|  
|MLSLABEL|Wird nicht unterstützt.|Wird nicht unterstützt.|  
  
> [!NOTE]  
>  Weitere Informationen zu die zulässige Größe der Spalte VARCHAR, finden Sie unter [VARCHAR-Spaltengröße](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) in diesem Handbuch.
