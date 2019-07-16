---
title: Diagnose für Desktop-Datenbank, Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4e7c8ea96708886f9edf54047bd2a2104ba0ec8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031221"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnose für Desktop-Datenbanktreiber
Alle Fehler und Warnungen, die nicht überprüft oder nur teilweise aktiviert der Treiber-Manager werden vom Treiber verarbeitet. Der Treiber ordnet außerdem native Fehler oder Fehler, die von der Datenquelle an SQLSTATEs zurückgegeben. Jede Funktion aufgeführt, die der *ODBC Programmer's Reference* enthält einen Abschnitt "Diagnose", der angibt, Bedingungen und Nachrichten.  
  
 -Anwendungen rufen **SQLGetDiagRec** SQLSTATE, systemeigener Fehlercode und diagnosemeldungen abrufen. Aufrufen von **SQLGetDiagField** und Angeben des Felds einzelner Diagnosefelder abruft. Die Ebene der Unterstützung der Diagnose-Bezeichner wird in der folgenden Tabelle aufgeführt.  
  
|DiagIdentifiers|Supportebene|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Nicht unterstützt|  
|SQL_DIAG_CLASS_ORIGIN|Unterstützt. Immer "ODBC 3.0" für die Versionen 3.0 und späteren Versionen von diesem Treiber.|  
|SQL_DIAG_COLUMN_NUMBER|Supported|  
|SQL_DIAG_CURSOR_ROW_COUNT|Nicht unterstützt|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Nicht unterstützt|  
|SQL_DIAG_MESSAGE_TEXT|Supported|  
|SQL_DIAG_NATIVE|Supported|  
|SQL_DIAG_NUMBER|Supported|  
|SQL_DIAG_RETURNCODE|Unterstützt, aber vom Treiber-Manager implementiert|  
|SQL_DIAG_ROW_COUNT|Supported|  
|SQL_DIAG_ROW_NUMBER|Supported|  
|SQL_DIAG_SERVER_NAME|Nicht unterstützt|  
|SQL_DIAG_SQLSTATE|Supported|  
|SQL_DIAG_SUBCLASS_ORIGIN|Supported|
