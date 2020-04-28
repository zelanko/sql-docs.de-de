---
title: Diagnose für Desktop-Datenbanktreiber | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 99603c047e77d3cd3e077c1b07c2192eeb65f93c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303481"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnose für Desktop-Datenbanktreiber
Alle Fehler und Warnungen, die vom Treiber-Manager nicht geprüft oder teilweise geprüft werden, werden vom Treiber verarbeitet. Der Treiber ordnet auch systemeigene Fehler oder von der Datenquelle zurückgegebene Fehler zu Sqlstates zu. Jede in der *ODBC-Programmier Referenz* aufgelistete Funktion enthält einen Abschnitt "Diagnostics", der Bedingungen und Meldungen angibt.  
  
 Anwendungen rufen **SQLGetDiagRec** auf, um SQLSTATE, systemeigenen Fehlercode und Diagnosemeldungen abzurufen. Durch Aufrufen von **SQLGetDiagField** und angeben des Felds werden einzelne Diagnose Felder abgerufen. Die Unterstützungs Ebene der Diagnose Bezeichner ist in der folgenden Tabelle aufgeführt.  
  
|Diagbezeichner|Supportebene|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Nicht unterstützt|  
|SQL_DIAG_CLASS_ORIGIN|Unterstützt. Immer "ODBC 3,0" für die Versionen 3,0 und höher dieses Treibers.|  
|SQL_DIAG_COLUMN_NUMBER|Unterstützt|  
|SQL_DIAG_CURSOR_ROW_COUNT|Nicht unterstützt|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Nicht unterstützt|  
|SQL_DIAG_MESSAGE_TEXT|Unterstützt|  
|SQL_DIAG_NATIVE|Unterstützt|  
|SQL_DIAG_NUMBER|Unterstützt|  
|SQL_DIAG_RETURNCODE|Unterstützt, aber vom Treiber-Manager implementiert|  
|SQL_DIAG_ROW_COUNT|Unterstützt|  
|SQL_DIAG_ROW_NUMBER|Unterstützt|  
|SQL_DIAG_SERVER_NAME|Nicht unterstützt|  
|SQL_DIAG_SQLSTATE|Unterstützt|  
|SQL_DIAG_SUBCLASS_ORIGIN|Unterstützt|
