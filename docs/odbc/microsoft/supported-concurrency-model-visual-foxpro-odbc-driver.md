---
title: Unterstütztes Parallelitäts Modell (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 597d1022fa6946e0ae768cb9600a3f4534c67a25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080696"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Unterstütztes Parallelitätsmodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC- *Treiber unterstützt*die schreibgeschützte Parallelität. Die Anwendung kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer SQL_CONCURRENCY Option von SQL_CONCUR_READ_ONLY aufrufen.  
  
 Weitere Informationen finden Sie in der [ODBC Programmer es Reference](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>schreibgeschützte Parallelität  
 Der Cursor kann nicht aktualisiert werden.  
  
## <a name="row-versioning"></a>Zeilenversionsverwaltung  
 Im wesentlichen Zeitstempel Unterstützung, bei der Zeilen Versionen zur Aktualisierungszeit verglichen werden.
