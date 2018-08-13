---
title: Zuordnen eines Umgebungshandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: deb6883d7323d5962559355af03e5b64466c3d46
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39556850"
---
# <a name="allocating-an-environment-handle"></a>Zuordnen eines Umgebungshandles
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Bevor eine Anwendung eine ODBC-Funktion aufrufen kann, muss sie die ODBC-Umgebung initialisieren und ein Umgebungshandle zuordnen. Dies ist das globale Kontexthandle und der Platzhalter für die anderen Handles in ODBC. Rufen Sie dazu **SQLAllocHandle** mit der *HandleType* Parametersatz auf SQL_HANDLE_ENV und *InputHandle* auf SQL_NULL_HANDLE festgelegt wird.  
  
 Nachdem das Umgebungshandle zugewiesen wurde, muss die Anwendung Umgebungsattribute festlegen, um anzugeben, welche Version der ODBC-Funktionsaufrufe verwendet wird. Die ODBC 3. verwenden zu können. *x* Aufrufen von Funktionen, [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) mit der *Attribut* Parametersatz auf SQL_ATTR_ODBC_VERSION und *ValuePtr* SQL_OV_ festgelegt ODBC3.  
  
## <a name="see-also"></a>Siehe auch  
 [Kommunikation mit SQLServer &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
