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
ms.openlocfilehash: ab694a8ba3a1976207ad1d0c6505cc953f39ff94
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785147"
---
# <a name="bulk-copying-text-and-image-data"></a>Massenkopieren von Text- und Bilddaten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Große **Text**-, **ntext**-und **Image** -Werte werden mithilfe der [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) -Funktion Massen kopiert. Sie codieren [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für die **Text**-, **ntext**-oder **Image** -Spalte, wobei ein *pData* -Zeiger auf NULL festgelegt ist, um anzugeben, dass die Daten **bcp_moretext**bereitgestellt werden. Es ist wichtig, die genaue Länge der Daten anzugeben, die für jede **Text**-, **ntext**-oder **Image** -Spalte in jeder Massen kopierten Zeile angegeben werden. Wenn sich die Länge der Daten für eine Spalte von der in [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)angegebenen Spaltenlänge unterscheidet, verwenden Sie [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) , um die Länge auf den richtigen Wert festzulegen. Ein [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sendet alle nicht-**Text**-Daten, nicht-**ntext**-Daten und nicht-**Bilddaten** . Anschließend wird **bcp_moretext** aufgerufen, um die **Text**-, **ntext**-oder **Image** -Daten in separaten Einheiten zu senden. Massen Kopierfunktionen bestimmen, dass alle Daten für die aktuelle **Text**-, **ntext**-oder **Image** -Spalte gesendet wurden, wenn die Summe der Daten Längen, die über **bcp_moretext** gesendet werden, gleich der in der letzten angegebenen Länge ist **bcp_collen** oder **bcp_bind**.  
  
 **bcp_moretext** hat keinen Parameter, um eine Spalte zu identifizieren. Wenn mehrere **Text**-, **ntext**-oder **Image** -Spalten in einer Zeile vorhanden sind, werden **bcp_moretext** für die **Text**-, **ntext**-oder **Image** -Spalten gestartet, beginnend mit der Spalte mit der niedrigsten Ordinalzahl und Fortfahren mit der Spalte mit der höchsten Ordinalzahl. **bcp_moretext** wechselt von einer Spalte zur nächsten, wenn die Summe der gesendeten Daten gleich der im letzten **bcp_collen** oder **bcp_bind** für die aktuelle Spalte angegebenen Länge ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Massen Kopier &#40;Vorgängen (ODBC)&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
