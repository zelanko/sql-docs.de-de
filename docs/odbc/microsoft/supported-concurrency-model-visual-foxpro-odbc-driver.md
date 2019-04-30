---
title: Parallelitätsmodell (Visual FoxPro-ODBC-Treiber) unterstützt | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8528ecb2f34d3f0ef7120c7047865ab5f6c1a72
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270102"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Unterstütztes Parallelitätsmodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC-Treiber unterstützt *Parallelität READ_ONLY*. Ihre Anwendung aufrufen kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer Option SQL_CONCURRENCY SQL_CONCUR_READ_ONLY.  
  
 Weitere Informationen finden Sie unter den [ODBC Programmer's Reference](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>Parallelität READ_ONLY  
 Der Cursor kann nicht aktualisiert werden.  
  
## <a name="row-versioning"></a>Zeilenversionsverwaltung  
 Im Wesentlichen Zeitstempel Unterstützung, in welcher Zeile Versionen zur Zeit der Aktualisierung verglichen werden.
