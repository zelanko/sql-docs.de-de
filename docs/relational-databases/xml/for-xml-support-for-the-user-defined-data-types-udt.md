---
title: FOR XML-Unterstützung für die benutzerdefinierten Datentypen (User-Defined Data Types, UDT) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6731d73830fe4f79525e05110920c6a3e6c2a1e
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509857"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>FOR XML-Unterstützung für die benutzerdefinierten Datentypen (User-Defined Data Types, UDT)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  FOR XML unterstützt keine benutzerdefinierten Datentypen (UDT) in Common Language Runtime (CLR).  
  
 Um FOR XML mit benutzerdefinierten Datentypen in CLR verwenden zu können, stellen Sie sicher, dass der Datentyp eine XML-Serialisierung besitzt und in der FOR XML-Auswahlklausel explizit in XML umgewandelt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [FOR XML-Unterstützung für verschiedene SQL Server-Datentypen](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
