---
title: Große benutzerdefinierte CLR-Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34a2320c5caf05ed1ce4909422bc5b340713125
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417639"
---
# <a name="large-clr-user-defined-types"></a>Große benutzerdefinierte CLR-Typen
  In SQL Server 2005 waren benutzerdefinierte Typen (User-Defined Types, UDTs) in der Common Language Runtime (CLR) auf eine Größe von 8.000 Bytes beschränkt. Diese Einschränkung wurde aufgehoben [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] und höhere Versionen. CLR-UDTs werden jetzt auf eine ähnliche Weise wie große Objekttypen (LOB) behandelt. UDTs mit genau oder weniger als 8.000 Byte verhalten sich also genau wie in SQL Server 2005. Größere UDTs werden aber unterstützt und zeigen ihre Größe als "unbegrenzt" an.  
  
 Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;OLE DB&#41; ](../ole-db/large-clr-user-defined-types-ole-db.md) und [Large CLR User-Defined Typen &#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="use-cases"></a>Einsatzgebiete  
 Für ODBC umfasst die Unterstützung großer UDTs die Möglichkeit zum Versenden von UDT-Werten in Teilen als Data-at-Execution-Parameter. Dies erfolgt mithilfe von SQLPutData.  
  
 Für OLE DB-Unterstützung für große UDTs die Möglichkeit zum Stream-UDT-Werte zu und vom Server enthält mithilfe von ISequentialStream-Bindung.  
  
 UDTs kleiner oder gleich 8.000 Byte verhalten sich wie in SQL Server 2005. Für OLE DB können Sie immer noch kleine UDTs streamen, mithilfe von ISequentialStream-Bindung.  
  
 Manchmal muss systemeigener Code den Inhalt von CLR-UDTs verstehen, muss aber keine verwalteten Objekte instanziieren. In diesem Fall können Sie die benutzerdefinierte Serialisierung verwenden, um UDT-Werte auf dem Server in ein für die Clients bekanntes Format zu konvertieren.  
  
 Bei Anwendungen, die über einen vorhandenen Datenzugriffscode verfügen, können Sie das CLR-UDT-Verhalten auf dem Client nutzen, indem Sie UDTs über systemeigene APIs abrufen und sie mithilfe von C++ CLI Interop in Anwendungen des gemischten Modus instanziieren.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](sql-server-native-client-features.md)  
  
  
