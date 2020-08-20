---
description: Unterstütztes Parallelitätsmodell (Visual FoxPro-ODBC-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be0a7e9ea3700941282f23956a8c304a1ef7f5e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500103"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Unterstütztes Parallelitätsmodell (Visual FoxPro-ODBC-Treiber)
Der Visual FoxPro-ODBC- *Treiber unterstützt*die schreibgeschützte Parallelität. Die Anwendung kann [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) mit einer SQL_CONCURRENCY Option von SQL_CONCUR_READ_ONLY aufrufen.  
  
 Weitere Informationen finden Sie in der [ODBC Programmer es Reference](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>schreibgeschützte Parallelität  
 Der Cursor kann nicht aktualisiert werden.  
  
## <a name="row-versioning"></a>Zeilenversionsverwaltung  
 Im wesentlichen Zeitstempel Unterstützung, bei der Zeilen Versionen zur Aktualisierungszeit verglichen werden.
