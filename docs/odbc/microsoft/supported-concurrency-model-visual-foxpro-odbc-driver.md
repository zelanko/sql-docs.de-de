---
title: Unterstütztes Parallelitätsmodell (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 253a6dd86f6dc974d53dd151636bb8b8132e4d02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307716"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Unterstütztes Parallelitätsmodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro ODBC-Treiber unterstützt *schreibgeschützte Parallelität*. Ihre Anwendung kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer SQL_CONCURRENCY Option SQL_CONCUR_READ_ONLY aufrufen.  
  
 Weitere Informationen finden Sie in der [ODBC-Programmiererreferenz](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>Schreibgeschützte Parallelität  
 Der Cursor kann nicht aktualisiert werden.  
  
## <a name="row-versioning"></a>Zeilenversionsverwaltung  
 Im Wesentlichen Zeitstempelunterstützung, bei der Zeilenversionen zur Aktualisierungszeit verglichen werden.
