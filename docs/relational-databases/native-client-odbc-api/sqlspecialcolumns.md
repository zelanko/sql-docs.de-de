---
title: SQLSpecialColumns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 67c0ff950115a9d9f6f5685804f5e3955a8af4d7
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51676119"
---
# <a name="sqlspecialcolumns"></a>'SQLSpecialColumns'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Bei Anforderung von zeilenbezeichnern (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** gibt Sie für alle Bereich außer SQL_SCOPE_CURROW angeforderten ein leeres Resultset (keine Datenzeilen) zurück. Das generierte Resultset gibt an, dass die Spalten nur innerhalb dieses Bereichs gültig sind.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine Pseudospalten für Bezeichner. Die **SQLSpecialColumns** Resultset identifiziert alle Spalten als SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** kann in einem statischen Cursor ausgeführt werden. Der Versuch, auszuführen **SQLSpecialColumns** in einem aktualisierbaren (keysetgesteuerten oder dynamischen) SQL_SUCCESS_WITH_INFO, dass der Cursortyp geändert wurde.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns-Unterstützung für erweiterte Funktionen zu Datum und Uhrzeit  
 Weitere Informationen zu den Werten für die Spalten DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH und DECIMAL_DIGTS für Datum/Uhrzeit-Typen zurückgegeben, finden Sie unter [Katalogmetadaten](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>SQLSpecialColumns -Unterstützung für große CLR-UDTs  
 **SQLSpecialColumns** unterstützt große CLR-benutzerdefinierte Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSpecialColumns-Funktion](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
