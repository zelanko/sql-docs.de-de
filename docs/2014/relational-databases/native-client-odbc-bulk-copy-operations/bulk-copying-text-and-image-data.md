---
title: Massenkopieren von Text- und Image-Daten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c674c24b4000ada4651dfb44ed2d49e9fd5bde83
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048501"
---
# <a name="bulk-copying-text-and-image-data"></a>Massenkopieren von Text- und Bilddaten
  Große **Text**, **Ntext**, und **Image** Werte werden beim Massenkopieren mithilfe der [Bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) Funktion. Sie code [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) für die **Text**, **Ntext**, oder **Image** Spalte mit einem *pData* Zeiger festgelegt NULL, der angibt, die Daten mit bereitgestellt werden **Bcp_moretext**. Es ist wichtig, geben Sie die genaue Länge der bereitgestellten Daten für jede **Text**, **Ntext**, oder **Image** Spalte in jeder Zeile massenkopiert. Wenn die Länge der Daten für eine Spalte der Länge der Spalte im angegebenen unterscheidet [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), verwenden Sie [Bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) auf die Länge auf den richtigen Wert festgelegt. Ein [Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sendet alle nicht-**Text**, nicht-**Ntext**, und nicht-**Image** Daten, sondern entwerfen die rufen dann **Bcp_moretext** zum Senden der **Text**, **Ntext**, oder **Image** Daten in separaten Einheiten. Massenkopierfunktionen erkennen, dass alle Daten für die aktuelle gesendet wurde **Text**, **Ntext**, oder **Image** Spalte, wenn die Summe der Längen der Daten das Versenden von **Bcp_moretext** entspricht der Länge, angegeben in der neuesten **Bcp_collen** oder **Bcp_bind**.  
  
 **Bcp_moretext** verfügt über keinen Parameter, um eine Spalte zu identifizieren. Wenn mehrere **Text**, **Ntext**, oder **Image** Spalten in einer Zeile **Bcp_moretext** arbeitet mit der **Text**, **Ntext**, oder **Image** Spalten, die mit der Spalte an, dass von der niedrigsten Ordnungszahl, und es wird auf die Spalte mit der höchsten Ordnungszahl ab. **Bcp_moretext** wechselt von einer Spalte zur nächsten, wenn die Summe der Längen der gesendeten Daten im aktuellen angegebene Länge ist gleich **Bcp_collen** oder **Bcp_bind** für die aktuelle Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  