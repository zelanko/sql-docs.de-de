---
title: Datentyp-Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4ce0eb96832f4a6b9c1953b0a9a9d0af65cb3b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687978"
---
# <a name="data-type-limitations"></a>Einschränkungen für Datumstypen
Der Microsoft ODBC Desktop-Datenbanktreiber verursachen die folgenden Einschränkungen für Datentypen:  
  
|Datentyp|Description|  
|---------------|-----------------|  
|Alle Datentypen|Konvertierungsfehler Typ können dazu führen, dass die betreffende Spalte auf NULL festgelegt wird.|  
|BINARY|Erstellen eine BINÄRE Zeichenfolge der Länge Null-Spalte gibt tatsächlich eine BINÄRE 255-Byte-Spalte zurück.|  
|DATE|Der DATE-Datentyp kann nicht auf einen anderen Datentyp (oder selbst) durch die CONVERT-Funktion konvertiert werden.|  
|DECIMAL (genauer numerischer Wert)|Wird nicht unterstützt.|  
|Gleitkomma-Datentypen|Die Anzahl der Dezimalstellen in eine Gleitkommazahl kann durch das Zahlenformat, legen Sie im Abschnitt der Windows-Systemsteuerung internationale eingeschränkt werden.|  
|NUMERIC|Unterstützt die maximale Genauigkeit und Dezimalstellen des 28.|  
|timestamp|Der TIMESTAMP-Datentyp kann nicht auf sich selbst von der CONVERT-Funktion konvertiert werden.|  
|TINYINT|TINYINT-Werte sind immer ohne Vorzeichen.|  
|Leere Zeichenfolgen|Wenn eine dBASE, Microsoft Excel, Paradox oder Textdriver verwendet wird, fügt eine Zeichenfolge der Länge 0 (null) in eine Spalte einfügen tatsächlich ein NULL-Wert stattdessen.|
