---
title: Verbesserungen bei Datum und Uhrzeit | Microsoft-Dokumentation
description: Verbesserungen bei Datum und Uhrzeit im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4ad635d32571bcf79b9280df7c18a2ff2b77fda4
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006945"
---
# <a name="date-and-time-improvements"></a>Verbesserungen bei Datum und Uhrzeit
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dieses Thema beschreibt die Unterstützung der neuen Datums- und Uhrzeitdatentypen, die in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] hinzugefügt wurden, durch den OLE DB-Treiber für SQL Server.  
  
 Weitere Informationen zu Verbesserungen hinsichtlich Datum und Zeit finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md).  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Verwendung  
 In den folgenden Abschnitten werden verschiedene Methoden zur Verwendung der neuen Datums- und Uhrzeittypen beschrieben.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Verwenden von 'Date' als eindeutigen Datentyp  
 Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ist die Verwendung des Typs DBTYPE_DBDATE OLE DB durch die verbesserte Unterstützung von Datums- und Zeittypen effizienter geworden.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Verwenden von 'Time' als eindeutigen Datentyp  
 OLE DB verfügt bereits über einen Datentyp, der nur die Zeit enthält: DBTYPE_DBTIME, der die Zeit mit einer Genauigkeit von 1 Sekunde angibt.
  
 Der neue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Zeitdatentyp verfügt über eine Genauigkeit in Sekundenbruchteilen von bis zu 100 Nanosekunden. Hierfür ist im OLE DB-Treiber für SQL Server ein neuer Typ erforderlich: DBTYPE_DBTIME2 Vorhandene Anwendungen, in denen Zeitdaten nicht in Sekundenbruchteilen angegeben werden, können time(0)-Spalten verwenden. Der vorhandene OLE DB DBTYPE_TIME-Typ und seine entsprechenden Strukturen sollten richtig funktionieren, sofern sich die Anwendungen nicht auf den in den Metadaten zurückgegebenen Typ verlassen.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Verwenden von 'Time' als eindeutigen Datentyp mit einer Genauigkeit in Sekundenbruchteilen  
 Einige Anwendungen, z. B. in der Fertigung und Prozesssteuerung, erfordern die Fähigkeit, Zeitdaten mit einer Genauigkeit von bis zu 100 Nanosekunden zu verarbeiten. Der neue Typ für diesen Zweck in OLE DB ist DBTYPE_DBTIME2.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Verwenden von 'Datetime' mit einer Genauigkeit in Sekundenbruchteilen  
 OLE DB definiert bereits einen Typ mit einer Genauigkeit von bis zu 1 Nanosekunde. Dieser Typ wird jedoch bereits von vorhandenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anwendungen verwendet, die eine Genauigkeit von lediglich 1/300 Sekunde erwarten. Der neue **datetime2(3)** -Typ ist nicht direkt kompatibel mit dem vorhandenen datetime-Typ. Wenn das Risiko besteht, dass sich dies auf das Verhalten der Anwendung auswirkt, müssen Anwendungen das neue DBCOLUMN-Flag zur Bestimmung des tatsächlichen Servertyps verwenden.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Verwenden von 'Datetime' mit einer Genauigkeit in Sekundenbruchteilen und Zeitzoneninformationen  
 Einige Anwendungen erfordern datetime-Werte mit Zeitzoneninformationen. Dies wird im neuen Typ DBTYPE_DBTIMESTAMPOFFSET unterstützt.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Verwenden von 'Date'-/'Time'-/'Datetime'-/'Datetimeoffset'-Daten mit clientseitigen Konvertierungen in Übereinstimmung mit vorhandenen Konvertierungen  
 Die Konvertierungen wurden auf einheitliche Weise erweitert, um alle in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführte Konvertierungen zwischen Datums- und Zeittypen einzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
