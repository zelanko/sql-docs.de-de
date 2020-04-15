---
title: Verwalten von Text- und Bildspalten | Microsoft Docs
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
ms.openlocfilehash: d3ac58e59f66dd107a9523a42f5647c90b4fb737
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297713"
---
# <a name="managing-text-and-image-columns"></a>Verwalten von Text und Imagespalten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**text**- **ntext**und **image** data (auch als long data bezeichnet) sind Zeichen- oder Binärzeichenfolgendatentypen, die Datenwerte enthalten können, die zu groß sind, um in **char-,** **varchar-,** **binäre**oder **varbinarye** Spalten zu passen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Textdatentyp** wird dem ODBC-SQL_LONGVARCHAR-Datentyp zugeordnet. **ntext-Zuordnungen** zu SQL_WLONGVARCHAR; und **Bildkarten** zu SQL_LONGVARBINARY. Einige Datenelemente, wie z. B. lange Dokumente oder große Bitmaps, sind möglicherweise zu groß, um im Speicher gespeichert zu werden. Um lange Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus sequenziellen Teilen abzurufen, ermöglicht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client-ODBC-Treiber einer Anwendung den Aufruf von [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Um lange Daten in sequenziellen Teilen zu senden, kann die Anwendung [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md)aufrufen. Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als Data-at-Execution-Parameter bezeichnet.  
  
 Eine Anwendung kann tatsächlich jede Art von Daten (nicht nur lange Daten) mit **SQLPutData** oder **SQLGetData**schreiben oder abrufen, obwohl nur **Zeichen-** und **Binärdaten** in Teilen gesendet oder abgerufen werden können. Wenn die Daten jedoch klein genug sind, um in einen einzelnen Puffer zu passen, gibt es im Allgemeinen keinen Grund, **SQLPutData** oder **SQLGetData**zu verwenden. Es ist viel leichter, den einzelnen Puffer an den Parameter oder die Spalte zu binden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Vergleich von gebundenen und ungebundenen Text- und Image-Spalten](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Vergleich von protokollierten und nicht protokollierten Änderungen](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Data-at-Execution und Text-, ntext- oder Imagespalten](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
