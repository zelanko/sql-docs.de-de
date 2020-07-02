---
title: Zuordnen eines Umgebungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2ec79644005e599fc17bada65c49d6f1516539fb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734920"
---
# <a name="allocating-an-environment-handle"></a>Zuordnen eines Umgebungshandles
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Bevor eine Anwendung eine ODBC-Funktion aufrufen kann, muss sie die ODBC-Umgebung initialisieren und ein Umgebungshandle zuordnen. Dies ist das globale Kontexthandle und der Platzhalter für die anderen Handles in ODBC. Dies geschieht durch Aufrufen von **sqlzuordchandle** , *wobei der Parameter* für den Parameter auf SQL_HANDLE_ENV und *InputHandle* auf SQL_NULL_HANDLE festgelegt ist.  
  
 Nachdem das Umgebungshandle zugewiesen wurde, muss die Anwendung Umgebungsattribute festlegen, um anzugeben, welche Version der ODBC-Funktionsaufrufe verwendet wird. Zur Verwendung von ODBC 3. *x* -Funktionen, Aufrufen von [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) , wobei der- *Attribut* Parameter auf SQL_ATTR_ODBC_VERSION und *ValuePtr* auf SQL_OV_ODBC3 festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
