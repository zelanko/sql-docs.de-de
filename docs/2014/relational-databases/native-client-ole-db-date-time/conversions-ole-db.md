---
title: Bindungen und Konvertierungen (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b35583f18cbe590773c6661091186f669e012555
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62638207"
---
# <a name="bindings-and-conversions-ole-db"></a>Bindungen und Konvertierungen (OLE DB)
  In diesem Abschnitt wird erläutert, wie zwischen `datetime`- und `datetimeoffset`-Werten konvertiert wird. Die in diesem Abschnitt beschriebenen Konvertierungen werden entweder von OLE DB bereitgestellt oder sind eine konsistente Erweiterung von OLE DB.  
  
 Das Format für Literale und Zeichenfolgen für Datums- und Zeitangaben in OLE DB entspricht normalerweise ISO und hängt nicht von der Gebietsschemaeinstellung des Clients ab. Eine Ausnahme ist DBTYPE_DATE, wo der Standard OLE-Automatisierung ist. Da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client allerdings nur zwischen Typen konvertiert, wenn Daten vom oder zum Client übertragen werden, kann eine Anwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client nicht dazu zwingen, zwischen DBTYPE_DATE und Zeichenfolgenformaten zu konvertieren. Andernfalls verwenden Zeichenfolgen die folgenden Formate (Text in Klammern gibt ein optionales Element an):  
  
-   Das Format von `datetime`- und `datetimeoffset`-Zeichenfolgen ist:  
  
     *JJJJ*-*mm*-*DD*[ *HH*:*mm*:*SS*[.* 9999999*] [?? *HH*:*mm*]]  
  
-   Das Format von `time`-Zeichenfolgen ist:  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   Das Format von `date`-Zeichenfolgen ist:  
  
     *yyyy*-*mm*-*dd*  
  
> [!NOTE]  
>  Frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client und SQLOLEDB haben OLE-Konvertierungen implementiert, falls Standardkonvertierungen fehlgeschlagen sind. Als Ergebnis unterscheiden sich einige von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 sowie höheren Versionen ausgeführte Konvertierungen von der OLE DB-Spezifikation.  
  
 Konvertierungen von Zeichenfolgen ermöglichen Flexibilität bei Leerstellen- und Feldbreite. Weitere Informationen finden Sie im Abschnitt "Datenformate: Zeichen folgen und Literale" unter [Datentyp Unterstützung für OLE DB Datums-und Uhrzeit Verbesserungen](data-type-support-for-ole-db-date-and-time-improvements.md).  
  
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
 [Client-/Server-Konvertierungen](conversions-performed-from-client-to-server.md)  
 Beschreibt date/time-Konvertierungen, die für eine Clientanwendung durchgeführt werden, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) geschrieben wurde.  
  
 [Server/Client-Konvertierungen](conversions-performed-from-server-to-client.md)  
 Beschreibt date/time-Konvertierungen, die zwischen [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) und einer Clientanwendung durchgeführt werden, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB geschrieben wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Date and Time Improvements &#40;OLE DB&#41; (Verbesserungen bei Datum und Uhrzeit &#40;OLE DB&#41;)](date-and-time-improvements-ole-db.md)  
  
  
