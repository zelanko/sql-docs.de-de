---
title: Protokollierte und nicht protokollierte Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6c6e4d9a0dc937f7f4dd41e1c2acb32354a5b8e0
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011205"
---
# <a name="logged-vs-unlogged-modifications"></a>Vergleich von protokollierten und nicht protokollierten Änderungen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Eine Anwendung kann anfordern, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber keine **Text**-, **ntext**-und **Image** -Änderungen protokolliert. Diese Option sollte jedoch mit Vorsicht eingesetzt werden. Er sollte nur für Situationen verwendet werden, in denen die **Text**-, **ntext**-oder **Image** -Daten nicht von entscheidender Bedeutung sind und Daten Besitzer bereit sind, die Fähigkeit zum Wiederherstellen von Daten für eine höhere Leistung abzuwägen.  
  
 Die Protokollierung von **Text**-, **ntext**-und **Image** -Änderungen wird gesteuert, indem [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) aufgerufen wird, wobei der- *Attribut* Parameter auf SQL_SOPT_SS_ TEXTPTR_LOGGING und *ValuePtr* auf SQL_TL_ON oder SQL_TL_OFF festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text und Imagespalten](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
