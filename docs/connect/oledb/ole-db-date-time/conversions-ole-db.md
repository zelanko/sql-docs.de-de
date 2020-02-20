---
title: Bindungen und Konvertierungen (OLE DB) | Microsoft-Dokumentation
description: Bindungen und Konvertierungen (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: dc86193f40474fc373c1b0e7dd48e579e8548821
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015844"
---
# <a name="conversions-ole-db"></a>Konvertierungen (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Abschnitt wird die Konvertierung zwischen **datetime**- und **datetimeoffset**-Werten beschrieben. Die in diesem Abschnitt beschriebenen Konvertierungen werden entweder von OLE DB bereitgestellt oder sind eine konsistente Erweiterung von OLE DB.  
  
 Das Format für Literale und Zeichenfolgen für Datums- und Zeitangaben in OLE DB entspricht normalerweise ISO und hängt nicht von der Gebietsschemaeinstellung des Clients ab. Eine Ausnahme ist DBTYPE_DATE, wo der Standard OLE-Automatisierung ist. Da der OLE DB-Treiber für SQL Server jedoch nur zwischen Typen konvertiert, wenn Daten vom oder zum Client übertragen werden, kann eine Anwendung nicht erzwingen, dass der OLE DB-Treiber für SQL Server zwischen DBTYPE_DATE und Zeichenfolgenformaten konvertiert. Andernfalls verwenden Zeichenfolgen die folgenden Formate (Text in Klammern gibt ein optionales Element an):  
  
-   Das Format der **datetime**- und **datetimeoffset**-Zeichenfolgen ist das folgende:  
  
     *yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ± *hh*:*mm*]]  
  
-   Das Format für **Uhrzeiten** lautet wie folgt:  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   Das Format von **date**-Zeichenfolgen ist das folgende:  
  
     *yyyy*-*mm*-*dd*  
  
> [!NOTE]  
>  Frühere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und SQLOLEDB haben OLE-Konvertierungen implementiert, falls Standardkonvertierungen fehlgeschlagen sind. Der OLE DB-Treiber für SQL Server verhält sich identisch mit dem nativen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Client. Als Ergebnis unterscheiden sich einige vom OLE DB-Treiber für SQL Server ausgeführte Konvertierungen von der OLE DB-Spezifikation.  
  
 Konvertierungen von Zeichenfolgen ermöglichen Flexibilität bei Leerstellen- und Feldbreite. Weitere Informationen finden Sie im Abschnitt „Datenformate: Zeichenfolgen und Literale“ des Artikels [Datentypunterstützung für Verbesserungen von Datum und Uhrzeit in OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
