---
title: Massenkopieren von Text- und Image-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae3a9685acc5746bab3d4605fe674dd4133ae2af
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412977"
---
# <a name="bulk-copying-text-and-image-data"></a>Massenkopieren von Text- und Bilddaten
  Große **Text**, **Ntext**, und **Image** Werte sind beim Massenkopieren mit dem [Bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) Funktion. Code [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für die **Text**, **Ntext**, oder **Image** Spalte mit einem *pData* legen Sie den Zeiger auf NULL, der angibt, die Daten erfolgt mit **Bcp_moretext**. Es ist wichtig, geben Sie die genaue Länge der bereitgestellten Daten für jede **Text**, **Ntext**, oder **Image** Spalte in jeder Zeile massenkopiert. Wenn die Länge der Daten für eine Spalte im angegebenen Spaltenlänge unterscheidet [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), verwenden Sie [Bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) legt die Länge auf den richtigen Wert. Ein [Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sendet alle nicht-**Text**, nicht-**Ntext**, und nicht-**Image** Daten; Sie rufen dann **Bcp_moretext** zum Senden der **Text**, **Ntext**, oder **Image** Daten in separaten Einheiten. Massenkopierfunktionen erkennen, dass alle Daten für die aktuelle gesendet wurde **Text**, **Ntext**, oder **Image** Spalte, wenn die Summe der Längen der Daten über gesendet**Bcp_moretext** im neuesten angegebenen Länge entspricht **Bcp_collen** oder **Bcp_bind**.  
  
 **Bcp_moretext** verfügt über keinen Parameter, um eine Spalte zu identifizieren. Falls mehrere vorhanden sind **Text**, **Ntext**, oder **Image** Spalten in einer Zeile **Bcp_moretext** greift auf die **Text**, **Ntext**, oder **Image** Spalten, die mit der Spalte an, dass von der niedrigsten Ordnungszahl und in absteigender Reihenfolge auf die Spalte mit der höchsten Ordnungszahl ab. **Bcp_moretext** wechselt von einer Spalte zur nächsten, wenn die Summe der Längen der gesendeten Daten im neuesten angegebene Länge ist gleich **Bcp_collen** oder **Bcp_bind** für die aktuelle Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
