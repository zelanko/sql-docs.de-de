---
title: FOR XML-Unterstützung für benutzerdefinierte Datentypen (User-Defined Data Types, UDT) | Microsoft-Dokumentation
description: Informieren Sie sich über die Unterstützung für benutzerdefinierte Datentypen (User-Defined Data Types, UDT) bei Verwendung der FOR XML-Klausel.
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 53a70da583b55fa8d979aeaaee3782fd6551c6ea
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729916"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>FOR XML-Unterstützung für die benutzerdefinierten Datentypen (User-Defined Data Types, UDT)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  FOR XML unterstützt keine benutzerdefinierten Datentypen (UDT) in Common Language Runtime (CLR).  
  
 Um FOR XML mit benutzerdefinierten Datentypen in CLR verwenden zu können, stellen Sie sicher, dass der Datentyp eine XML-Serialisierung besitzt und in der FOR XML-Auswahlklausel explizit in XML umgewandelt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [FOR XML-Unterstützung für verschiedene SQL Server-Datentypen](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
