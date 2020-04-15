---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69457daccbc7868e58f91c71a48b4b25f15f5318
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302717"
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Betrachten Sie in der Regel die Auswirkungen der Verwendung von **SQLBindCol,** um eine Datenkonvertierung zu verursachen. Bindungskonvertierungen sind Clientprozesse. Wenn Sie beispielsweise einen Gleitkommawert, der an eine Zeichenspalte gebunden ist, abrufen, führt der Treiber die Gleitkomma-in-Zeichen-Konvertierung lokal durch, wenn eine Zeile abgerufen wird. Die [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT-Funktion kann zum Übertragen der Kosten einer Datenkonvertierung auf den Server verwendet werden.  
  
 Eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann mehrere Sets an Ergebniszeilen bei einer einzelnen Anweisungsausführung zurückgeben. Jedes Resultset muss getrennt gebunden sein. Weitere Informationen zum Binden für mehrere Resultsets finden Sie unter [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Der Entwickler kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Spalten mithilfe des *TargetType-Werts* **SQL_C_BINARY**an -spezifische C-Datentypen binden. An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische Typen gebundene Spalten sind nicht übertragbar. Die definierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen ODBC-C-Datentypen entsprechen den Typdefinitionen für DB-Library, und DB-Library-Entwickler, die Anwendungen übertragen, können diese Funktion nutzen.  
  
 Das Melden von Datenabschneidungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist ein teurer Prozess für den Native Client ODBC-Treiber. Sie können das Abschneiden vermeiden, indem Sie sicherstellen, dass alle gebundenen Datenpuffer weit genug sind, um Daten zurückzugeben. Bei Zeichendaten sollte die Breite ausreichend Platz für ein Zeichenfolgeabschlusszeichen bieten, wenn das Standardtreiberverhalten für den Zeichenfolgenabschluss verwendet wird. Wenn Sie z. B. eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)-Spalte** an ein Array von fünf Zeichen binden, wird für jeden abgerufenen Wert abgeschnitten. Wenn Sie die gleiche Spalte an ein Array mit sechs Zeichen binden, wird die Abschneidung vermieden, indem ein Zeichenelement bereitgestellt wird, in dem das Null-Abschlusszeichen gespeichert werden soll. [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) kann verwendet werden, um lange Zeichen- und Binärdaten effizient ohne Abschneide abzurufen.  
  
 Wenn bei Datentypen mit großem Wert der vom Benutzer bereitgestellte Puffer nicht groß genug ist, um den gesamten Wert der Spalte zu enthalten, werden **SQL_SUCCESS_WITH_INFO** zurückgegeben und die "Zeichenfolgendaten; Rechte Abschneide" Warnung ausgegeben wird. Das **Argument StrLen_or_IndPtr** enthält die Anzahl der im Puffer gespeicherten Zeichen/Bytes.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>SQLBindCol-Unterstützung für verbesserte Funktionen für Datum/Uhrzeit  
 Ergebnisspaltenwerte von Datums-/Uhrzeittypen werden wie unter [Konvertierungen von SQL in C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)beschrieben konvertiert. Beachten Sie, dass *TargetType* als **SQL_C_DEFAULT** oder **SQL_C_BINARY**angegeben werden muss, um Zeit- und Datumszeitversatzspalten als entsprechende Strukturen (**SQL_SS_TIME2_STRUCT** und **SQL_SS_TIMESTAMPOFFSET_STRUCT**) abzurufen.  
  
 Weitere Informationen finden Sie unter [Datums- und Zeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>SQLBindCol-Unterstützung für große CLR-UDTs  
 **SQLBindCol** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Große benutzerdefinierte CLR-Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLBindCol-Funktion](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
