---
title: Bindungen und Konvertierungen (OLE DB) | Microsoft-Dokumentation
description: Bindungen und Konvertierungen (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 233c9e7e2aefbdae34f964e95dbeb7d10d55a63d
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105876"
---
# <a name="conversions-ole-db"></a>Konvertierungen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Beschreibt die Konvertierung zwischen datetime- und datetimeoffset-Werten. Die in diesem Abschnitt beschriebenen Konvertierungen werden entweder von OLE DB bereitgestellt oder sind eine konsistente Erweiterung von OLE DB.  
  
 Das Format für Literale und Zeichenfolgen für Datums- und Zeitangaben in OLE DB entspricht normalerweise ISO und hängt nicht von der Gebietsschemaeinstellung des Clients ab. Eine Ausnahme ist DBTYPE_DATE, wo der Standard OLE-Automatisierung ist. Da  Native Client allerdings nur zwischen Typen konvertiert, wenn Daten vom oder zum Client übertragen werden, kann eine Anwendung  Native Client nicht dazu zwingen, zwischen DBTYPE_DATE und Zeichenfolgenformaten zu konvertieren. Andernfalls verwenden Zeichenfolgen die folgenden Formate (Text in Klammern gibt ein optionales Element an):  
  
-   Das Format der **"DateTime"** und **Datetimeoffset** -Zeichenfolgen ist:  
  
     *Yyyy*-*mm*-*TT*[ *Hh*:*mm*:*ss*[. *9999999*] [± *Hh*:*mm*]]  
  
-   Das Format für **Uhrzeiten** lautet wie folgt:  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   Das Format von Datumszeichenfolgen ist 'yyyy-mm-dd'.  
  
     *yyyy*-*mm*-*dd*  
  
> [!NOTE]  
>  Frühere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und SQLOLEDB haben OLE-Konvertierungen implementiert, falls Standardkonvertierungen fehlgeschlagen sind. Der OLE DB-Treiber für SQL Server folgt das gleiche Verhalten wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Als Ergebnis unterscheiden sich einige von  Native Client 10.0 sowie höheren Versionen ausgeführte Konvertierungen von der OLE DB-Spezifikation.  
  
 Konvertierungen von Zeichenfolgen ermöglichen Flexibilität bei Leerstellen- und Feldbreite. Weitere Informationen finden Sie im Abschnitt "Datenformate: Zeichenfolgen und Literale" unter [Datentypunterstützung für OLE DB-Datum und Uhrzeit-Verbesserungen](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).  
  
 Folgende sind allgemeine Konvertierungsregeln:  
  
-   Wenn eine Zeichenfolge in einen date/time-Typ konvertiert wird, wird die Zeichenfolge zuerst als ISO-Literal analysiert. Wenn dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert, das über Zeitkomponenten verfügt.  
  
-   Wenn keine Zeit vorhanden ist, der Empfänger aber Zeit speichern kann, wird die Zeit auf 0 (null) festgelegt. Wenn kein Datum vorhanden ist, der Empfänger aber ein Datum speichern kann, wird das Datum auf das aktuelle Datum festgelegt, wenn ISO-Konvertierungen verwendet werden, und auf den 30.12.1899, wenn OLE-Konvertierungen verwendet werden.  
  
-   Wenn im vom Client verwendeten Datentyp keine Zeitzone vorhanden ist, der Server aber eine Zeitzone speichern kann, wird angenommen, dass sich die Daten auf dem Client in der Clientzeitzone befinden.  
  
-   Wenn auf dem Server keine Zeitzone vorhanden ist, der Client aber über Zeitzoneninformationen verfügt, wird die UTC-Zeitzone angenommen. Dieses Verhalten unterscheidet sich vom Serververhalten.  
  
-   Wenn die Zeit vorhanden ist, der Empfänger aber keine Zeit speichern kann, wird die Zeitkomponente ignoriert.  
  
-   Wenn das Datum vorhanden ist, der Empfänger aber kein Datum speichern kann, wird die Datumskomponente ignoriert.  
  
-   Wenn beim Konvertieren vom Client zum Server ein Abschneiden der Sekunden oder Sekundenbruchteile auftritt, wird DB_E_ERRORSOCCURRED zurückgegeben, und als Status wird DBSTATUS_E_DATAOVERFLOW festgelegt.  
  
-   Wenn beim Konvertieren von Server zu Client ein Abschneiden der Sekunden oder Sekundenbruchteile auftritt, wird DBSTATUS_S_TRUNCATED festgelegt  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Client-/Server-Konvertierungen](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md)  
 Beschreibt date/time-Konvertierungen, die für eine Clientanwendung durchgeführt werden, die mit dem OLE DB-Treiber für SQL Server und [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (oder höher) geschrieben wurde.  
  
 [Server/Client-Konvertierungen](../../oledb/ole-db-date-time/conversions-performed-from-server-to-client.md)  
 Beschreibt date/time-Konvertierungen, die zwischen [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (oder höher) und einer Clientanwendung durchgeführt werden, die mit dem OLE DB-Treiber für SQL Server geschrieben wurde.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
