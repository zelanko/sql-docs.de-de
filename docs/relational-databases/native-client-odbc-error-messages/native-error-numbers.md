---
title: Systemeigene Fehlernummern | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b1bc1f9383ab615a24b0506b86cf0ec5e37b6c74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73783404"
---
# <a name="native-error-numbers"></a>Systemeigene Fehlernummern
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei Fehlern, die in der Datenquelle auftreten (von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gibt der Native Client-ODBC-Treiber die systemeigene Fehler [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Nummer zurück, die von zurückgegeben wird. Für Fehler, die vom Treiber erkannt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gibt der Native Client-ODBC-Treiber die systemeigene Fehlernummer 0 (null) zurück. Weitere Informationen zu einer Liste der systemeigenen Fehlernummern finden Sie in der Fehler Spalte der Systemtabelle " **sysmess** " in der **Master** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Datenbank in.  
  
 Informationen zu den Zustands Fehlercodes finden Sie unter [SQLSTATE &#40;ODBC-Fehlercodes&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Bei Fehlern, die von der Netzwerkbibliothek zurückgegeben werden, stammt die systemeigene Fehlernummer von der zugrunde liegenden Netzwerksoftware.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
