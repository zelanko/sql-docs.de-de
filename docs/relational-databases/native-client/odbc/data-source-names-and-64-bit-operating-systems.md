---
title: Datenquellen Namen und 64-Bit-Betriebssysteme | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Anwendung als 32-Bit-Anwendung auf einem 64-Bit-Betriebssystem erstellen und ausführen, indem Sie die ODBC-Datenquelle mit dem ODBC-Administrator erstellen.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 416cd9e812cabccacc710f2b23c506702fae1778
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475971"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Datenquellennamen und 64-Bit-Betriebssysteme
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Wenn Sie eine Anwendung als 32-Bit-Anwendung entwickeln und unter einem 64-Bit-Betriebssystem ausführen möchten, müssen Sie die ODBC-Datenquelle mit dem ODBC-Administrator in %windir%\SysWOW64\odbcad32.exe erstellen.  
  
## <a name="remarks"></a>Hinweise  
 Ein 64-Bit-Windows-Betriebssystem verfügt über zwei odbcad32.exe-Dateien:  
  
-   %SystemRoot%\system32\odbcad32.exe wird verwendet, um Datenquellennamen für 64-Bit-Anwendungen zu erstellen und zu warten.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe wird verwendet, um Datenquellennamen für 32-Bit-Anwendungen, einschließlich 32-Bit-Anwendungen, die auf 64-Bit-Betriebssystemen ausgeführt werden, zu erstellen und zu warten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
