---
title: Multithreadanwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9c64c45331ec5f8efe11ee75abb065201cda0714
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009779"
---
# <a name="creating-a-driver-application---multithreaded-applications"></a>Erstellen einer Treiberanwendung – Multithreadanwendungen
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ist ein Multithreadtreiber. Das Schreiben einer Multithreadanwendung ist eine Alternative zum Verwenden von asynchronen Aufrufen zur Verarbeitung von mehreren ODBC-Aufrufen. Ein Thread kann einen synchronen ODBC-Aufruf erstellen, und andere Threads können verarbeitet werden, während der erste Thread blockiert wird und auf die Antwort auf seinen Aufruf wartet. Dieses Modell ist effizienter als asynchrone Aufrufe, da Verarbeitungsaufwand beseitigt wird, wie Netzwerkverkehr und die wiederholte Erstellung von ODBC-Funktionsaufrufen zum Überprüfen von SQL_STILL_EXECUTING.  
  
 Der asynchrone Modus ist immer noch eine effektive Methode der Verarbeitung. Die Leistungsverbesserungen eines Multithreadmodells genügen nicht, um das Umschreiben asynchroner Anwendungen zu rechtfertigen. Wenn Benutzer DB-Library-Anwendungen konvertieren, die das asynchrone DB-Library-Modell verwenden, empfiehlt sich die Konvertierung in das asynchrone ODBC-Modell.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
