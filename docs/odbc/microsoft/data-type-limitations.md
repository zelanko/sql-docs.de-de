---
title: Einschränkungen des Datentyps | Microsoft-Dokumentation
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
ms.openlocfilehash: 64d16a9181c475427677371d1e6e180570225b7a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096464"
---
# <a name="data-type-limitations"></a>Einschränkungen für Datumstypen
Die Microsoft ODBC Desktop-Datenbanktreiber erzwingen die folgenden Einschränkungen für-Datentypen:  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Alle Datentypen|Typkonvertierungs Fehler können dazu führen, dass die betroffene Spalte auf NULL festgelegt wird.|  
|BINARY|Beim Erstellen einer binären Spalte der Länge 0 (null) wird tatsächlich eine 255-Byte-Binär Spalte zurückgegeben.|  
|DATE|Der Date-Datentyp kann von der Convert-Funktion nicht in einen anderen Datentyp (oder selbst) konvertiert werden.|  
|Decimal (genau numerisch)|Wird nicht unterstützt.|  
|Gleit Komma Datentypen|Die Anzahl der Dezimalstellen in einer Gleit Komma Zahl kann durch das Zahlenformat eingeschränkt werden, das im internationalen Abschnitt der Windows-Systemsteuerung festgelegt ist.|  
|NUMERIC|Unterstützt maximale Genauigkeit und eine Skala von 28.|  
|timestamp|Der timestamp-Datentyp kann von der Convert-Funktion nicht in sich selbst konvertiert werden.|  
|TINYINT|TINYINT-Werte sind immer unsigniert.|  
|Zeichen folgen der Länge 0|Wenn eine dBASE, Microsoft Excel, Paradox oder textdriver verwendet wird, fügt eine Zeichenfolge der Länge 0 (null) in eine Spalte ein, stattdessen wird stattdessen ein NULL-Wert eingefügt.|
