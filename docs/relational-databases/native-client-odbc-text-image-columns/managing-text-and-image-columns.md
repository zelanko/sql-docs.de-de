---
title: Verwalten von Text-und image-Spalten | Microsoft-Dokumentation
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
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f94b7830d4912249f05c10a42c24ba05da2ad030
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007896"
---
# <a name="managing-text-and-image-columns"></a>Verwalten von Text und Imagespalten
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Text**- **, ntext**-und **Image** -Daten (auch als Long Data bezeichnet) sind Zeichen-oder Binär Zeichenfolgendatentypen, die Datenwerte enthalten können, die für die Spalten **char**, **varchar**, **Binary**oder **varbinary** zu groß sind. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** Datentyp wird dem ODBC-SQL_LONGVARCHAR-Datentyp zugeordnet. **ntext** wird SQL_WLONGVARCHAR zugeordnet. und **Image** wird SQL_LONGVARBINARY zugeordnet. Einige Datenelemente, wie z. B. lange Dokumente oder große Bitmaps, sind möglicherweise zu groß, um im Speicher gespeichert zu werden. Zum Abrufen von Long-Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sequenziellen Teilen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht der Native Client ODBC-Treiber einer Anwendung das Aufrufen von [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Um lange Daten in sequenziellen Teilen zu senden, kann die Anwendung [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md)abrufen. Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als Data-at-Execution-Parameter bezeichnet.  
  
 Eine Anwendung kann mit **SQLPutData** oder **SQLGetData**tatsächlich beliebige Datentypen (nicht nur mit langen Daten) schreiben oder abrufen, obwohl nur **Zeichen** -und **Binär** Daten in Teilen gesendet oder abgerufen werden können. Wenn die Daten jedoch klein genug für einen einzelnen Puffer sind, gibt es im Allgemeinen keinen Grund, **SQLPutData** oder **SQLGetData**zu verwenden. Es ist viel leichter, den einzelnen Puffer an den Parameter oder die Spalte zu binden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Vergleich von gebundenen und ungebundenen Text- und Image-Spalten](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Vergleich von protokollierten und nicht protokollierten Änderungen](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Data-at-Execution und Text-, ntext- oder Imagespalten](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
