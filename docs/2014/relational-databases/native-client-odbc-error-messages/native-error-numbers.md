---
title: Systemeigene Fehlernummern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 7e7cd24a3eb1ccdeea1b6e6cbb97e2d0f222193f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63223502"
---
# <a name="native-error-numbers"></a>Systemeigene Fehlernummern
  Bei Fehlern, die in der Datenquelle auftreten (von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gibt der Native Client-ODBC-Treiber die systemeigene Fehler [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Nummer zurück, die von zurückgegeben wird. Für Fehler, die vom Treiber erkannt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gibt der Native Client-ODBC-Treiber die systemeigene Fehlernummer 0 (null) zurück. Weitere Informationen zu einer Liste der systemeigenen Fehlernummern finden Sie in der Fehler Spalte der Systemtabelle " **sysmess** " in der **Master** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Datenbank in.  
  
 Informationen zu den Zustands Fehlercodes finden Sie unter [SQLSTATE &#40;ODBC-Fehlercodes&#41;](sqlstate-odbc-error-codes.md). Bei Fehlern, die von der Netzwerkbibliothek zurückgegeben werden, stammt die systemeigene Fehlernummer von der zugrunde liegenden Netzwerksoftware.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Behandlung von Fehlern und Meldungen](handling-errors-and-messages.md)  
  
  
