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
ms.openlocfilehash: 593f0b17ead284940d6f22b5983d284ddd37d7d4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760722"
---
# <a name="bulk-copying-text-and-image-data"></a>Massenkopieren von Text- und Bilddaten
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Große **Text**-, **ntext**-und **Image** -Werte werden mithilfe der [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) -Funktion Massen kopiert. Sie codieren [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für die **Text**-, **ntext**-oder **Image** -Spalte, wobei ein *pData* -Zeiger auf NULL festgelegt ist, um anzugeben, dass die Daten **bcp_moretext**bereitgestellt werden. Es ist wichtig, die genaue Länge der Daten anzugeben, die für jede **Text**-, **ntext**-oder **Image** -Spalte in jeder Massen kopierten Zeile angegeben werden. Wenn sich die Länge der Daten für eine Spalte von der in [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)angegebenen Spaltenlänge unterscheidet, verwenden Sie [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) , um die Länge auf den richtigen Wert festzulegen. Ein [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sendet alle nicht-**Text**-Daten, nicht-**ntext**-Daten und nicht-**Bilddaten** . Anschließend wird **bcp_moretext** aufgerufen, um die **Text**-, **ntext**-oder **Image** -Daten in separaten Einheiten zu senden. Massen Kopierfunktionen bestimmen, dass alle Daten für die aktuelle **Text**-, **ntext**-oder **Image** -Spalte gesendet wurden, wenn die Summe der Daten Längen, die über **bcp_moretext** gesendet werden, gleich der im letzten **bcp_collen** oder **bcp_bind**angegebenen Länge ist.  
  
 **bcp_moretext** hat keinen Parameter, um eine Spalte zu identifizieren. Wenn mehrere **Text**-, **ntext**-oder **Image** -Spalten in einer Zeile vorhanden sind, werden **bcp_moretext** für die **Text**-, **ntext**-oder **Image** -Spalten gestartet, beginnend mit der Spalte mit der niedrigsten Ordinalzahl und mit der Spalte mit der höchsten Ordinalzahl. **bcp_moretext** wechselt von einer Spalte zur nächsten, wenn die Summe der gesendeten Daten gleich der im letzten **bcp_collen** oder **bcp_bind** für die aktuelle Spalte angegebenen Länge ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
