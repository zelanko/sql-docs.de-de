---
title: SQLSpecialColumns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021570"
---
# <a name="sqlspecialcolumns"></a>'SQLSpecialColumns'
  Beim Anfordern von Zeilen bezeichgern (*IdentifierType* SQL_BEST_ROWID) gibt **SQLSpecialColumns** ein leeres Resultset (keine Daten Zeilen) für einen angeforderten Bereich außer SQL_SCOPE_CURROW zurück. Das generierte Resultset gibt an, dass die Spalten nur innerhalb dieses Bereichs gültig sind.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine Pseudospalten für Bezeichner. Das **SQLSpecialColumns** -Resultset identifiziert alle Spalten als SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** kann in einem statischen Cursor ausgeführt werden. Der Versuch, **SQLSpecialColumns** für eine aktualisierbare (keysetgesteuerte oder dynamische) auszuführen, gibt SQL_SUCCESS_WITH_INFO zurück, die angibt, dass der Cursortyp geändert wurde.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns-Unterstützung für erweiterte Funktionen zu Datum und Uhrzeit  
 Informationen zu den Werten, die für die Spalten DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH und DECIMAL_DIGTS für Datums-/Uhrzeittypen zurückgegeben werden, finden Sie unter [catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere allgemeine Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>SQLSpecialColumns -Unterstützung für große CLR-UDTs  
 **SQLSpecialColumns** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLSpecialColumns-Funktion](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
