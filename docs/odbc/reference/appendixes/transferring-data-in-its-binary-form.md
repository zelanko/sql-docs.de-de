---
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
ms.openlocfilehash: 53531ff4a3b2e1441fabf22ec7a3ce12b15540eb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301412"
---
# <a name="transferring-data-in-its-binary-form"></a>Übertragen von Daten in ihrer binären Form
Eine Anwendung kann Daten (in der internen Form, die von einem angegebenen DBMS verwendet wird) sicher zwischen zwei Datenquellen übertragen, die das gleiche DBMS und die gleiche Hardwareplattform verwenden. Für ein bestimmtes Datenelement müssen die SQL-Datentypen in den Quell-und Ziel Datenquellen identisch sein. Der C-Datentyp ist SQL_C_BINARY.  
  
 Wenn die Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** aufruft, um die Daten aus der Quelldaten Quelle abzurufen, ruft der Treiber die Daten aus der Datenquelle ab und überträgt sie ohne Konvertierung an einen Speicherort vom Typ SQL_C_BINARY. Wenn die Anwendung **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData oder SQLSetPos** aufruft, um die Daten an die Ziel Datenquelle zu senden, ruft der Treiber die Daten vom Speicherort ab und überträgt ihn ohne Konvertierung in die Ziel Datenquelle.  
  
> [!NOTE]  
>  Anwendungen, die auf diese Weise Daten (außer Binärdaten) übertragen, sind unter DBMSs nicht interoperabel.  
  
 **SQLCopyDesc** kann zum Kopieren von Zeilen Bindungen aus dem Quell-DBMS in Parameter Bindungen im Ziel-DBMS verwendet werden.
