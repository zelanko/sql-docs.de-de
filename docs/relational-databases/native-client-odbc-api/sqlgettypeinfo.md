---
title: SQLGetTypeInfo | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81ba57c6e66f156f13055ff5ec941fa8f0c86381
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298439"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC-Treiber für den systemeigenen Client meldet die zusätzliche Spalte USERTYPE im Resultset von **SQLGetTypeInfo**. USERTYPE gibt die DB-Library-Datentypdefinition aus und ist für Entwickler nützlich, die bestehende DB-Library-Anwendungen nach ODBC portieren.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behandelt die Identität als Attribut, wohingegen ODBC die Identität als Datentyp behandelt. Um diese Nichtübereinstimmung zu beheben, gibt **SQLGetTypeInfo** die Datentypen **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity**und **numericidentity**zurück. Die **SQLGetTypeInfo-Ergebnissatzspalte** AUTO_UNIQUE_VALUE meldet den Wert TRUE für diese Datentypen.  
  
 Für **varchar**, **nvarchar** und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varbinary**meldet der Native Client ODBC-Treiber weiterhin 8000, 4000 bzw. 8000 für den COLUMN_SIZE-Wert, obwohl er eigentlich unbegrenzt ist. Damit soll die Rückwärtskompatibilität sichergestellt werden.  
  
 Für den **XML-Datentyp** meldet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ODBC-Treiber SQL_SS_LENGTH_UNLIMITED für COLUMN_SIZE, um unbegrenzte Größe zu bezeichnen.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo und Tabellenwertparameter  
 Der Tabellentyp für Tabellenwertparameter ist effektiv ein Metatyp, d. h. ein Typ, der zum Definieren anderer Typen verwendet wird. Daher muss es nicht über SQLGetTypeInfo verfügbar gemacht werden. Anwendungen müssen SQLTables anstelle von SQLGetTypeInfo verwenden, um Metadaten für Tabellentypen abzurufen, die mit Tabellenwertparametern verwendet werden.  
  
 Weitere Informationen zum Abrufen von metdata für Tabellenwertparameter finden Sie unter [Anweisungsattribute, die tabellenbewertete Parameter beeinflussen.](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen zu den Werten, die für Datums-/Uhrzeittypen zurückgegeben werden, finden Sie unter [Katalogmetadaten](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Allgemeinere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo-Unterstützung für große CLR-UDTs  
 **SQLGetTypeInfo** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLGetTypeInfo-Funktion](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
