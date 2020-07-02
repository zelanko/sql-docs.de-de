---
title: Datentypen und XML-Massen Ladeverhalten (SQLXML)
description: Erfahren Sie mehr über Datentypen und XML-Massen Ladeverhalten in SQLXML 4,0.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4e247ae58867054a1051f58f8a17d0d1ef701b2e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790668"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Datentypen und XML-Massenladenverhalten (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Die Datentypen, die im Zuordnungsschema (XSD-oder XDR-Typ und **SQL: datatype**) angegeben sind, werden im Allgemeinen ignoriert, außer in den folgenden Fällen:  
  
 Bei XSD:  
  
-   Wenn der Typ **DateTime** oder **time**ist, müssen Sie den **SQL: datatype** angeben, da XML-Massen Laden vor dem Senden der Daten an Microsoft eine Datenkonvertierung durchführt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Wenn Sie ein Massen laden in eine Spalte vom Typ " **uniqueidentifier** " in Ausführen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und der XSD-Wert eine GUID mit geschweiften Klammern ({und}) ist, müssen Sie **SQL: datatype = "uniqueidentifier"** angeben, um die geschweiften Klammern zu entfernen, bevor der Wert in die Spalte eingefügt wird. Wenn **SQL: datatype** nicht angegeben wird, wird der Wert mit geschweiften Klammern gesendet, und die Einfügung schlägt fehl.  
  
 Weitere Informationen zu **SQL: datatype**finden Sie unter [Datentyp Umwandlungen und die SQL: datatype-Anmerkung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Bei XDR:  
  
-   Wenn **dt: Type** **DateTime**, **time**, **DateTime.TZ**oder **time.TZ**ist, müssen Sie die Datentypen " **dt: Type** " und " **SQL: datatype** " angeben, da XML-Massen laden eine Datenkonvertierung durchführt, bevor die Daten an gesendet werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Wenn Ihre XML-Daten den Typ **UUID**aufweisen, muss **SQL: datatype** angegeben werden. **dt: Type = "uuid"** ist auch erforderlich, es sei denn, die Daten sind Zeichen folgen Daten. Wenn Sie **dt: uuid**nicht angeben, akzeptiert XML-Massen laden Zeichen folgen mit geschweiften Klammern (und entfernt Sie bei Bedarf).  
  
-   Wenn die XML-Daten " **bin. base64** " oder " **bin. Hex**" sind, müssen Sie den XML-Datentyp mit " **dt: Type**" angeben. XML-Massenladen lädt die Daten dann als Hexadezimaldarstellung der Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
