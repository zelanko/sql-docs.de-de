---
title: Große CLR-benutzerdefinierte Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 78928140c3aed95662535410501622e9554fc2d0
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245767"
---
# <a name="large-clr-user-defined-types-in-sql-server-native-client"></a>Große benutzerdefinierte CLR-Typen in SQL Server Native Client
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  In SQL Server 2005 waren benutzerdefinierte Typen (User-Defined Types, UDTs) in der Common Language Runtime (CLR) auf eine Größe von 8.000 Bytes beschränkt. Diese Einschränkung wurde in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höheren Versionen aufgehoben. CLR-UDTs werden jetzt auf eine ähnliche Weise wie große Objekttypen (LOB) behandelt. UDTs mit genau oder weniger als 8.000 Byte verhalten sich also genau wie in SQL Server 2005. Größere UDTs werden aber unterstützt und zeigen ihre Größe als "unbegrenzt" an.  
  
 Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md) und [große CLR-benutzerdefinierte Typen &#40;ODBC-&#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="use-cases"></a>Anwendungsfälle  
 Für ODBC umfasst die Unterstützung großer UDTs die Möglichkeit zum Versenden von UDT-Werten in Teilen als Data-at-Execution-Parameter. Dies erfolgt mithilfe von SQLPutData.  
  
 Für OLE DB umfasst die Unterstützung großer UDTs die Möglichkeit zum Streamen von UDT-Werten zum und vom Server mithilfe der ISequentialStream-Bindung.  
  
 UDTs kleiner oder gleich 8.000 Byte verhalten sich wie in SQL Server 2005. Für OLE DB können Sie immer noch kleine UDTs mithilfe einer ISequentialStream-Bindung streamen.  
  
 Manchmal muss systemeigener Code den Inhalt von CLR-UDTs verstehen, muss aber keine verwalteten Objekte instanziieren. In diesem Fall können Sie die benutzerdefinierte Serialisierung verwenden, um UDT-Werte auf dem Server in ein für die Clients bekanntes Format zu konvertieren.  
  
 Bei Anwendungen, die über einen vorhandenen Datenzugriffscode verfügen, können Sie das CLR-UDT-Verhalten auf dem Client nutzen, indem Sie UDTs über systemeigene APIs abrufen und sie mithilfe von C++ CLI Interop in Anwendungen des gemischten Modus instanziieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
