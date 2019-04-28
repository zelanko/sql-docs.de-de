---
title: Übertragen von Daten in seiner binären Form | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44bf8de8ea4c33a20a6159c5702db0b7eaee9eed
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62735046"
---
# <a name="transferring-data-in-its-binary-form"></a>Übertragen von Daten in ihrer binären Form
Eine Anwendung kann problemlos Daten (im internen Format, die von einem angegebenen DBMS verwendet) zwischen zwei Datenquellen übertragen, die das gleiche DBMS und die Hardware-Plattformen verwenden. Für einen bestimmten Daten müssen die SQL-Datentypen in den Quell- und Datenquellen identisch sein. Die C-Datentyp ist SQL_C_BINARY.  
  
 Wenn die Anwendung ruft **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData** zum Abrufen der Daten aus der Datenquelle für die Quelle, ruft der Treiber die Daten aus den Daten Datenquelle aus, und übertragen, ohne Konvertierung in einen Speicherort vom Typ SQL_C_BINARY. Wenn die Anwendung ruft **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData oder SQLSetPos** zum Senden der Daten an die Datenquelle, der Treiber Ruft die Daten aus dem Speicherort ab und überträgt sie, ohne Konvertierung auf die Datenquelle.  
  
> [!NOTE]  
>  Anwendungen, die für die Übertragung von Daten (mit Ausnahme der binären Daten) auf diese Weise können nicht zusammen verwendet, für die DBMS-Systeme.  
  
 **SQLCopyDesc** können verwendet werden, um die zeilenbindungen aus der Quell-DBMS in parameterbindungen in das Ziel-DBMS zu kopieren.
