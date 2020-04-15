---
title: Verwenden von Autofetch mit ODBC-Cursorn | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 812f4742dfe8273c4e96fc5205626fe1f6c07347
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298412"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Verwenden von Autofetch mit ODBC-Cursorn
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Wenn der Treiber [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einer Instanz von verbunden ist, unterstützt er eine Autofetch-Option, wenn ein Servercursortyp verwendet wird. Bei Autofetch verfügt die **SQLExecute-** oder **SQLExecDirect-Funktion,** die den Cursor öffnet, auch über eine implizite [SQLFetchScroll-Funktion](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST). Die Zeilen des ersten Rowsets werden während der Ausführung der Anweisung an die gebundenen Anwendungsvariablen zurückgegeben, wodurch ein weiterer Roundtrip über das Netzwerk bis zum Server vermieden wird. [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt, wenn die Autofetch-Option aktiviert ist. die Ergebnissatzspalten müssen an Programmvariablen gebunden sein.  
  
 Autofetch wird von Anwendungen angefordert, wenn für das treiberspezifische SQL_SOPT_SS_CURSOR_OPTIONS-Anweisungsattribut SQL_CO_AF festgelegt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur Cursorprogrammierung &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
