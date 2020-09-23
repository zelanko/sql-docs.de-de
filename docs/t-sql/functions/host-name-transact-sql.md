---
description: HOST_NAME (Transact-SQL)
title: HOST_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HOST_NAME_TSQL
- HOST_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- HOST_NAME function
- workstation names [SQL Server]
ms.assetid: 4b8b0705-c083-4b07-b954-c83ee73b2ebb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3dbd0179163a13989308f1c01ba350b37bf959ea
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116680"
---
# <a name="host_name-transact-sql"></a>HOST_NAME (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Gibt den Namen der Arbeitsstation zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
HOST_NAME ()  
```  

## <a name="return-types"></a>Rückgabetypen
 **nvarchar(128)**  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Parameter für eine Systemfunktion optional ist, wird von der aktuellen Datenbank, dem aktuellen Hostcomputer, dem aktuellen Serverbenutzer oder dem aktuellen Datenbankbenutzer ausgegangen. Auf integrierte Funktionen müssen immer runde Klammern folgen.  
  
 Systemfunktionen können in der SELECT-Liste, in einer WHERE-Klausel und überall dort verwendet werden, wo ein Ausdruck zulässig ist.  
  
> [!IMPORTANT]  
>  Die Clientanwendung stellt den Namen der Arbeitsstation bereit, und sie kann fehlerhafte Daten angeben. Verwenden Sie HOST_NAME nicht als Sicherheitsfunktion.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Tabelle erstellt, bei der `HOST_NAME()` in einer `DEFAULT` -Definition verwendet wird, um den Arbeitsstationsnamen von Computern aufzuzeichnen, die Zeilen in eine Tabelle zur Auftragsaufzeichnung einfügen.  
  
```sql  
CREATE TABLE Orders  
   (OrderID     INT        PRIMARY KEY,  
    CustomerID  NCHAR(5)   REFERENCES Customers(CustomerID),  
    Workstation NCHAR(30)  NOT NULL DEFAULT HOST_NAME(),  
    OrderDate   DATETIME   NOT NULL,  
    ShipDate    DATETIME   NULL,  
    ShipperID   INT        NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
