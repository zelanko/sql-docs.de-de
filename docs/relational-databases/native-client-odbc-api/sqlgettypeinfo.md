---
title: Sqlgettypeingefo | Microsoft-Dokumentation
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
ms.openlocfilehash: c00f8e33ee36dadb7506af2433e2ed4aeca769b1
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000335"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber meldet den zusätzlichen usertype der Spalte im Resultset von **SQLGetTypeInfo**. USERTYPE gibt die DB-Library-Datentypdefinition aus und ist für Entwickler nützlich, die bestehende DB-Library-Anwendungen nach ODBC portieren.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behandelt die Identität als Attribut, wohingegen ODBC die Identität als Datentyp behandelt. Um diesen Konflikt zu beheben, gibt **SQLGetTypeInfo** die folgenden Datentypen zurück: " **intidentity**", " **smallintidentity**", " **tinyintidentity**", " **decimalidentity**" und " **numericidentity**". Die **SQLGetTypeInfo** -Resultsetspalte AUTO_UNIQUE_VALUE meldet den Wert true für diese Datentypen.  
  
 Für **varchar**, **nvarchar** und **varbinary**wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber weiterhin den Bericht 8000, 4000 und 8000 für den COLUMN_SIZE Wert, auch wenn er tatsächlich unbegrenzt ist. Damit soll die Rückwärtskompatibilität sichergestellt werden.  
  
 Für den **XML** -Datentyp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] meldet der Native Client-ODBC-Treiber SQL_SS_LENGTH_UNLIMITED für COLUMN_SIZE, um eine unbegrenzte Größe anzugeben.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo und Tabellenwertparameter  
 Der Tabellentyp für Tabellenwert Parameter ist praktisch ein Metatyp, d. h. ein Typ, mit dem andere Typen definiert werden. Daher muss Sie nicht über sqlgettypeingefo verfügbar gemacht werden. Anwendungen müssen SQLTables anstelle von SQLGetTypeInfo verwenden, um Metadaten für Tabellentypen abzurufen, die mit Tabellenwert Parametern verwendet werden.  
  
 Weitere Informationen zum Abrufen von Diensttyp für Tabellenwert Parameter finden Sie unter [Anweisungs Attribute, die sich auf Tabellenwert Parameter auswirken](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen zu den für Datums-/Uhrzeittypen zurückgegebenen Werten finden Sie unter [catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere allgemeine Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo-Unterstützung für große CLR-UDTs  
 **SQLGetTypeInfo** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlgettypeingefo-Funktion](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
