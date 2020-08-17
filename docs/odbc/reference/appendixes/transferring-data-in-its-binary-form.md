---
description: Übertragen von Daten in ihrer binären Form
title: Übertragen von Daten in der Binär Form | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec858729e76c1e360ec0933eca3a29ab17542f4f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386326"
---
# <a name="transferring-data-in-its-binary-form"></a>Übertragen von Daten in ihrer binären Form
Eine Anwendung kann Daten (in der internen Form, die von einem angegebenen DBMS verwendet wird) sicher zwischen zwei Datenquellen übertragen, die das gleiche DBMS und die gleiche Hardwareplattform verwenden. Für ein bestimmtes Datenelement müssen die SQL-Datentypen in den Quell-und Ziel Datenquellen identisch sein. Der C-Datentyp ist SQL_C_BINARY.  
  
 Wenn die Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** aufruft, um die Daten aus der Quelldaten Quelle abzurufen, ruft der Treiber die Daten aus der Datenquelle ab und überträgt sie ohne Konvertierung an einen Speicherort vom Typ SQL_C_BINARY. Wenn die Anwendung **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData oder SQLSetPos** aufruft, um die Daten an die Ziel Datenquelle zu senden, ruft der Treiber die Daten vom Speicherort ab und überträgt ihn ohne Konvertierung in die Ziel Datenquelle.  
  
> [!NOTE]  
>  Anwendungen, die auf diese Weise Daten (außer Binärdaten) übertragen, sind unter DBMSs nicht interoperabel.  
  
 **SQLCopyDesc** kann zum Kopieren von Zeilen Bindungen aus dem Quell-DBMS in Parameter Bindungen im Ziel-DBMS verwendet werden.
