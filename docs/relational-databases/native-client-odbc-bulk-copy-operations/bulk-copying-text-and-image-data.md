---
title: Massen Kopieren von Text-und Bilddaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5243c862e07ad8b4f5a0b3b33ea292cecc1cb0a9
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707902"
---
# <a name="bulk-copying-text-and-image-data"></a>Massenkopieren von Text- und Bilddaten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Große **Text**-, **ntext**-und **Image** -Werte werden mithilfe der [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) -Funktion Massen kopiert. Sie codieren [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für die **Text**-, **ntext**-oder **Image** -Spalte, wobei ein *pData* -Zeiger auf NULL festgelegt ist, um anzugeben, dass die Daten mit **bcp_moretext**angegeben werden. Es ist wichtig, die genaue Länge der Daten anzugeben, die für jede **Text**-, **ntext**-oder **Image** -Spalte in jeder Massen kopierten Zeile angegeben werden. Wenn sich die Länge der Daten für eine Spalte von der in [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)angegebenen Spaltenlänge unterscheidet, verwenden Sie [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) , um die Länge auf den richtigen Wert festzulegen. Ein [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sendet alle nicht-**Text**-Daten, nicht-**ntext**-Daten und nicht-**Bilddaten** . Anschließend wird **bcp_moretext** aufgerufen, um die **Text**-, **ntext**-oder **Image** -Daten in separaten Einheiten zu senden. Massen Kopierfunktionen bestimmen, dass alle Daten für die aktuelle **Text**-, **ntext**-oder **Image** -Spalte gesendet wurden, wenn die Summe der Daten Längen, die über **bcp_moretext** gesendet werden, gleich der im letzten bcp_collen angegebenen Länge ist.oder **bcp_bind**.  
  
 **bcp_moretext** hat keinen Parameter, um eine Spalte zu identifizieren. Wenn in einer Zeile mehrere **Text**-, **ntext**-oder **Image** -Spalten vorhanden sind, werden in **bcp_moretext** die **Text**-, **ntext**-oder **Image** -Spalten beginnend mit der Spalte mit der niedrigsten Ordinalzahl und Fortfahren mit der Spalte mit der höchsten Ordinalzahl. **bcp_moretext** wechselt von einer Spalte zur nächsten, wenn die Summe der gesendeten Daten gleich der Länge ist, die in der letzten **bcp_collen** oder **bcp_bind** für die aktuelle Spalte angegeben ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Massen Kopier &#40;Vorgängen (ODBC)&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
