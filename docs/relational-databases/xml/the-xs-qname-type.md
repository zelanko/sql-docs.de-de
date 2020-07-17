---
title: Der xs:QName-Typ | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie den xs:QName-Typ als Beschränkungselement des XML-Schemas oder als Mitgliedstyp einer Union verwenden.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 879ec2e1e4aaebfde4b3597df3d244380f2b4165
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758517"
---
# <a name="the-xsqname-type"></a>Der xs:QName-Typ
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine von **xs:QName** abgeleiteten Typen, die ein Beschränkungselement des XML-Schemas verwenden. Außerdem unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktuell keine union-Typen mit **QName** als Elementtyp.  
  
## <a name="example"></a>Beispiel  
 Die folgende `CREATE XML SCHEMA COLLECTION` -Anweisungen kann das XML-Schema nicht laden, weil sie den `xs:QName` -Typ als Mitgliedstyp von union festlegen:  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 Beide Anweisungen führen zu einem Fehler.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anforderungen und Einschränkungen für XML-Schemaauflistungen auf dem Server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
