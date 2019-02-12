---
title: Zuordnen von XSD-Datentypen zu XPath-Datentypen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: MightyPen
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 158619cadcec1b0133b951bf2ce25445319d7ff4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034731"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Zuordnen von XSD-Datentypen zu XPath-Datentypen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn eine XPath-Abfrage für ein XSD-Schema ausgeführt wird und der XSD-Typ wird angegeben, der **xsd: Type** -Attribut, verwendet XPath den Datentyp, der bei der Verarbeitung der Abfrage angegeben.  
  
 Der XPath-Datentyp eines Knotens wird vom XSD-Datentyp in dem Schema abgeleitet, wie in der folgenden Tabelle dargestellt. (Der Knoten "EmployeeID" dient zur Veranschaulichung.)  
  
|XSD-Datentyp|XDR-Datentyp|Entsprechung<br /><br /> XPath-Datentyp|SQL Server<br /><br /> verwendete Konvertierung|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**Keine**<br /><br /> **bin.base64bin.hex**|**Nicht verfügbar**|None<br /><br /> EmployeeID|  
|**Boolean**|**boolean**|**boolean**|CONVERT(bit, EmployeeID)|  
|**Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong**|**Anzahl, Int, Float, i1, i2, i4, i8, r4, r8ui1, Anwenderschnittstelle: 2, UI4 sein, ui8**|**number**|CONVERT(float(53), EmployeeID)|  
|**id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI**|**id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid**|**Zeichenfolge**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**Nicht zutreffend (besteht kein Datentyp in XPath, der fixed14. 4 XDR-Datentyp entspricht.)**|CONVERT(money, EmployeeID)|  
|**Datum**|**Datum**|**Zeichenfolge**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**Uhrzeit**|**Uhrzeit**<br /><br /> **time.tz**|**Zeichenfolge**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
