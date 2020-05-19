---
title: FOR XML-Unterstützung für den timestamp-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type
ms.assetid: 4e1920e1-e7a4-4069-965e-3f6039a6099e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e20326c1f91711580e102bd28a705a628fc472dc
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716637"
---
# <a name="for-xml-support-for-the-timestamp-data-type"></a>FOR XML-Unterstützung für den timestamp-Datentyp
  In der FOR XML-Transformation werden **timestamp** -Typwerte als **varbinary(8)** -Daten behandelt und sind immer Base-64-codiert. Das XSD- oder XDR-Schema gibt, falls angefordert, diesen Typ wieder.  
  
```  
drop table t  
go  
create table t  
(c1 int,  
 c2 timestamp)  
go  
  
insert t values(1, null)  
go  
select * from t  
for xml auto, xmldata  
go  
```  
  
 Dies ist das Ergebnis:  
  
```  
<Schema name="Schema1"   
        xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="t" content="empty" model="closed">  
    <AttributeType name="c1" dt:type="i4" />  
    <AttributeType name="c2" dt:type="bin.base64" />  
    <attribute type="c1" />  
    <attribute type="c2" />  
  </ElementType>  
</Schema>  
<t xmlns="x-schema:#Schema1" c1="1" c2="AAAAAAAAH04=" />  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [FOR XML-Unterstützung für verschiedene SQL Server-Datentypen](for-xml-support-for-various-sql-server-data-types.md)  
  
  
