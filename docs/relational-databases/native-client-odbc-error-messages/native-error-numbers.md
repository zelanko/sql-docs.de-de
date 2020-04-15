---
title: Native Fehlernummern | Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b5572ee784f47b0444e1d825de1b6dd53db8066
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291605"
---
# <a name="native-error-numbers"></a>Systemeigene Fehlernummern
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei Fehlern, die in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Datenquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auftreten (von zurückgegeben), gibt der native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Client-ODBC-Treiber die systemeigene Fehlernummer zurück, die von zurückgegeben wird. Bei Fehlern, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Treiber erkannt werden, gibt der native Client-ODBC-Treiber die systemeigene Fehlernummer 0 zurück. Weitere Informationen zu einer Liste systemeigener Fehlernummern finden Sie in der Fehlerspalte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]der **Systemtabelle sysmessages** in der **Masterdatenbank** in .  
  
 Informationen zu den Statusfehlercodes finden Sie unter [SQLSTATE &#40;ODBC-Fehlercodes&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Bei Fehlern, die von der Netzwerkbibliothek zurückgegeben werden, stammt die systemeigene Fehlernummer von der zugrunde liegenden Netzwerksoftware.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
