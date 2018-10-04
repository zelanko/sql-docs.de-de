---
title: Massenkopieren von Text- und Image-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c468ec3cf52526192893458055cde857aeaa864d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103830"
---
# <a name="bulk-copying-text-and-image-data"></a>Massenkopieren von Text- und Bilddaten
  Große **Text**, **Ntext**, und **Image** Werte sind beim Massenkopieren mit dem [Bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) Funktion. Code [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für die **Text**, **Ntext**, oder **Image** Spalte mit einem *pData* legen Sie den Zeiger auf NULL, der angibt, die Daten erfolgt mit **Bcp_moretext**. Es ist wichtig, geben Sie die genaue Länge der bereitgestellten Daten für jede **Text**, **Ntext**, oder **Image** Spalte in jeder Zeile massenkopiert. Wenn die Länge der Daten für eine Spalte im angegebenen Spaltenlänge unterscheidet [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), verwenden Sie [Bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) legt die Länge auf den richtigen Wert. Ein [Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sendet alle nicht-**Text**, nicht-**Ntext**, und nicht-**Image** Daten; Sie rufen dann **Bcp_moretext** zum Senden der **Text**, **Ntext**, oder **Image** Daten in separaten Einheiten. Massenkopierfunktionen erkennen, dass alle Daten für die aktuelle gesendet wurde **Text**, **Ntext**, oder **Image** Spalte, wenn die Summe der Längen der Daten über gesendet**Bcp_moretext** im neuesten angegebenen Länge entspricht **Bcp_collen** oder **Bcp_bind**.  
  
 **Bcp_moretext** verfügt über keinen Parameter, um eine Spalte zu identifizieren. Falls mehrere vorhanden sind **Text**, **Ntext**, oder **Image** Spalten in einer Zeile **Bcp_moretext** greift auf die **Text**, **Ntext**, oder **Image** Spalten, die mit der Spalte an, dass von der niedrigsten Ordnungszahl und in absteigender Reihenfolge auf die Spalte mit der höchsten Ordnungszahl ab. **Bcp_moretext** wechselt von einer Spalte zur nächsten, wenn die Summe der Längen der gesendeten Daten im neuesten angegebene Länge ist gleich **Bcp_collen** oder **Bcp_bind** für die aktuelle Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
