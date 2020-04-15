---
title: Übertragen von Daten in ihrer binären Form | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301412"
---
# <a name="transferring-data-in-its-binary-form"></a>Übertragen von Daten in ihrer binären Form
Eine Anwendung kann Daten (in der internen Form, die von einem angegebenen DBMS verwendet wird) sicher zwischen zwei Datenquellen übertragen, die dieselbe DBMS- und Hardwareplattform verwenden. Für ein bestimmtes Datenelement müssen die SQL-Datentypen in den Quell- und Zieldatenquellen identisch sein. Der C-Datentyp ist SQL_C_BINARY.  
  
 Wenn die Anwendung **SQLFetch**, **SQLFetchScroll**oder **SQLGetData** aufruft, um die Daten aus der Quelldatenquelle abzurufen, ruft der Treiber die Daten aus der Datenquelle ab und überträgt sie ohne Konvertierung an einen Speicherort vom Typ SQL_C_BINARY. Wenn die Anwendung **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData oder SQLSetPos aufruft,** um die Daten an die Zieldatenquelle zu senden, ruft der Treiber die Daten vom Speicherort ab und überträgt sie ohne Konvertierung an die Zieldatenquelle.  
  
> [!NOTE]  
>  Anwendungen, die Daten (außer Binärdaten) auf diese Weise übertragen, sind unter DBMS nicht interoperabel.  
  
 **SQLCopyDesc** kann verwendet werden, um Zeilenbindungen aus dem Quell-DBMS in Parameterbindungen im Ziel-DBMS zu kopieren.
