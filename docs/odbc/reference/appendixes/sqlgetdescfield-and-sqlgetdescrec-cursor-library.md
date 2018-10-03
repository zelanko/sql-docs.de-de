---
title: SQLGetDescField und SQLGetDescRec (Cursorbibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66361572427c3264a1b25fe1c851685a07b2e029
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765018"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField und SQLGetDescRec (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLGetDescField** und **SQLGetDescRec** Funktionen in der Cursorbibliothek. Allgemeine Informationen zu diesen Funktionen finden Sie unter [SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md) und [SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 Führt die Cursorbibliothek **SQLGetDescRec** Lesezeichenspalten Metadaten zurückgegeben. Führt die Cursorbibliothek **SQLGetDescField** zurückzugebenden die gleichen Felder, die vom **SQLGetDescRec**, welche sind SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_ Länge, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_NULLABLE. Aus Gründen der Konsistenz **SQLGetDescField** sql_desc_unnamed darf auch zurück.  
  
 Führt die Cursorbibliothek **SQLGetDescField** wenn er aufgerufen wird, zurückgeben, der Wert der folgenden Felder, die zum Binden von Lesezeichenspalten festgelegt sind: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR, und SQL_DESC_LENGTH.  
  
 Führt die Cursorbibliothek **SQLGetDescField** wenn er aufgerufen wird, um den Wert des Felds SQL_DESC_BIND_OFFSET_PTR SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE oder SQL_DESC_ROW_STATUS_PTR zurückzugeben. Diese Felder können für jede Zeile wird nicht nur die Lesezeichen-Zeile zurückgegeben werden.  
  
 Wenn eine Anwendung ruft **SQLGetDescField** um den Wert eines Felds nicht erwähnten zurückzugeben, die Cursorbibliothek den Aufruf an den Treiber übergeben.
