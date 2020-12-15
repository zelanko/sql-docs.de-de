---
title: Systemeigene Fehlernummern | Microsoft-Dokumentation
description: Bei Fehlern gibt der SQL Server Native Client ODBC-Treiber die systemeigene Fehlernummer von SQL Server oder für vom Treiber erkannte Fehler zurück.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e336c5a85b61d0bff726efc5f3927ae3a1503880
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438482"
---
# <a name="native-error-numbers"></a>Systemeigene Fehlernummern
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Bei Fehlern, die in der Datenquelle auftreten (von zurückgegeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client-ODBC-Treiber die systemeigene Fehlernummer zurück, die von zurückgegeben wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Für Fehler, die vom Treiber erkannt werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client-ODBC-Treiber die systemeigene Fehlernummer 0 (null) zurück. Weitere Informationen zu einer Liste der systemeigenen Fehlernummern finden Sie in der Fehler Spalte der Systemtabelle " **sysmess** " in der **Master** -Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Informationen zu den Zustands Fehlercodes finden Sie unter [SQLSTATE &#40;ODBC-Fehlercodes&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Bei Fehlern, die von der Netzwerkbibliothek zurückgegeben werden, stammt die systemeigene Fehlernummer von der zugrunde liegenden Netzwerksoftware.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
