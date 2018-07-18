---
title: Diagnose für Desktop Datenbank Treiber | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d5d82eb22f57fd033ea9250e1dd5532e72174e3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904225"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnose für Desktop-Datenbanktreiber
Alle Fehler und Warnungen nicht oder teilweise ausgecheckt vom Treiber-Manager werden vom Treiber gehandhabt. Der Treiber ordnet auch systemeigene Fehler oder Fehler, die von der Datenquelle an SQLSTATEs zurückgegeben. Jede Funktion aufgeführt, die der *ODBC Programmer's Reference* enthält einen Diagnoseabschnitt "", der angibt, Bedingungen und Nachrichten.  
  
 -Anwendungen rufen **SQLGetDiagRec** SQLSTATE, systemeigener Fehlercode und diagnosemeldungen abgerufen. Aufrufen von **SQLGetDiagField** und Angeben des Felds, einzelne Diagnosefelder abruft. Das Maß an Unterstützung für die Diagnose Bezeichner wird in der folgenden Tabelle aufgeführt.  
  
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
