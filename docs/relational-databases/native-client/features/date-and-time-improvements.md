---
title: Datums- / Uhrzeitverbesserungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9b1d0d9d-1f6e-4399-8f61-e23f9a486a7a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 96a507d4dd3a5f7baa38a87e39073e7aa82a08a7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43103300"
---
# <a name="date-and-time-improvements"></a>Verbesserungen bei Datum und Uhrzeit
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Dieses Thema beschreibt die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Unterstützung der neuen Datums- und Uhrzeitdatentypen, die in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] hinzugefügt wurden.  
  
 Weitere Informationen zu Datum/Uhrzeit-Verbesserungen, finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;OLE DB&#41; ](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md) und [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Programmierbeispiele für SQL Server-Daten](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Verwendung  
 In den folgenden Abschnitten werden verschiedene Methoden zur Verwendung der neuen Datums- und Uhrzeittypen beschrieben.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Verwenden von 'Date' als eindeutigen Datentyp  
 Beginnend mit [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], verbesserte Unterstützung für Datum-/Uhrzeittypen ist es effizienter, die SQL_TYPE_DATE ODBC-Typs (SQL_DATE für ODBC 2.0-Anwendungen) und den DBTYPE_DBDATE OLE DB-Typ verwenden.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Verwenden von 'Time' als eindeutigen Datentyp  
 OLE DB verfügt bereits über einen Datentyp, der nur die Zeit enthält: DBTYPE_DBTIME, der die Zeit mit einer Genauigkeit von 1 Sekunde angibt. In ODBC ist der entsprechende Typ SQL_TYPE_TIME (SQL_TIME für ODBC 2.0-Anwendungen).  
  
 Der neue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Zeitdatentyp verfügt über eine Genauigkeit in Sekundenbruchteilen von bis zu 100 Nanosekunden. Dies erfordert neue Typen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client: DBTYPE_DBTIME2 (OLE DB) und SQL_SS_TIME2 (ODBC). Vorhandene Anwendungen, in denen Zeitdaten nicht in Sekundenbruchteilen angegeben werden, können time(0)-Spalten verwenden. Die vorhandenen OLE DB DBTYPE_TIME- und ODBC SQL_TYPE_TIME-Typen und ihre entsprechenden Strukturen sollten richtig funktionieren, es sei denn, die Anwendungen verlassen sich auf den in den Metadaten zurückgegebenen Typ.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Verwenden von 'Time' als eindeutigen Datentyp mit einer Genauigkeit in Sekundenbruchteilen  
 Einige Anwendungen, z. B. in der Fertigung und Prozesssteuerung, erfordern die Fähigkeit, Zeitdaten mit einer Genauigkeit von bis zu 100 Nanosekunden zu verarbeiten. Neue Typen für diesen Zweck sind DBTYPE_DBTIME2 (OLE DB) und SQL_SS_TIME2 (ODBC).  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Verwenden von 'Datetime' mit einer Genauigkeit in Sekundenbruchteilen  
 OLE DB definiert bereits einen Typ mit einer Genauigkeit von bis zu 1 Nanosekunde. Dieser Typ wird jedoch bereits von vorhandenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anwendungen verwendet, die eine Genauigkeit von lediglich 1/300 Sekunde erwarten. Der neue **datetime2(3)** -Typ ist nicht direkt kompatibel mit dem vorhandenen datetime-Typ. Wenn das Risiko besteht, dass sich dies auf das Verhalten der Anwendung auswirkt, müssen Anwendungen das neue DBCOLUMN-Flag zur Bestimmung des tatsächlichen Servertyps verwenden.  
  
 ODBC definiert auch einen Typ mit einer Genauigkeit von bis zu 1 Nanosekunde. Dieser Typ wird jedoch bereits verwendet, von vorhandenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Anwendungen diese Anwendungen erwarten eine Genauigkeit in nur 3 Millisekunden. Der neue **datetime2(3)** -Typ ist nicht direkt kompatibel mit dem vorhandenen **datetime** -Typ. **datetime2(3)** hat eine Genauigkeit von einer Millisekunde, und **datetime** hat eine Genauigkeit von 1/300 Sekunde. In ODBC können Anwendungen bestimmen, welcher Servertyp mit dem Deskriptorfeld SQL_DESC_TYPE_NAME verwendet wird. Deshalb kann der vorhandene SQL_TYPE_TIMESTAMP-Typ (SQL_TIMESTAMP für ODBC 2.0-Anwendungen) für beide Typen verwendet werden.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Verwenden von 'Datetime' mit einer Genauigkeit in Sekundenbruchteilen und Zeitzoneninformationen  
 Einige Anwendungen erfordern datetime-Werte mit Zeitzoneninformationen. Dies wird von den neuen Typen DBTYPE_DBTIMESTAMPOFFSET (OLE DB) und SQL_SS_TIMESTAMPOFFSET (ODBC) unterstützt.  
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Verwenden von 'Date'-/'Time'-/'Datetime'-/'Datetimeoffset'-Daten mit clientseitigen Konvertierungen in Übereinstimmung mit vorhandenen Konvertierungen  
 Der ODBC-Standard beschreibt, wie Konvertierungen zwischen vorhandenen Datum-, Zeit- und Timestamp-Typen funktionieren. Diese wurden erweitert, konsistent, enthalten Konvertierungen zwischen allen Datums- und Uhrzeittypen in eingeführt [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
