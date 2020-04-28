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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4beaf91a4ead743e3e8a2e32578796baba3c17be
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280670"
---
# <a name="data-type-limitations"></a>Einschränkungen für Datumstypen
Die Microsoft ODBC Desktop-Datenbanktreiber erzwingen die folgenden Einschränkungen für-Datentypen:  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Alle Datentypen|Typkonvertierungs Fehler können dazu führen, dass die betroffene Spalte auf NULL festgelegt wird.|  
|BINARY|Beim Erstellen einer binären Spalte der Länge 0 (null) wird tatsächlich eine 255-Byte-Binär Spalte zurückgegeben.|  
|DATE|Der Date-Datentyp kann von der Convert-Funktion nicht in einen anderen Datentyp (oder selbst) konvertiert werden.|  
|Decimal (genau numerisch)|Nicht unterstützt.|  
|Gleit Komma Datentypen|Die Anzahl der Dezimalstellen in einer Gleit Komma Zahl kann durch das Zahlenformat eingeschränkt werden, das im internationalen Abschnitt der Windows-Systemsteuerung festgelegt ist.|  
|NUMERIC|Unterstützt maximale Genauigkeit und eine Skala von 28.|  
|timestamp|Der timestamp-Datentyp kann von der Convert-Funktion nicht in sich selbst konvertiert werden.|  
|TINYINT|TINYINT-Werte sind immer unsigniert.|  
|Zeichen folgen der Länge 0|Wenn eine dBASE, Microsoft Excel, Paradox oder textdriver verwendet wird, fügt eine Zeichenfolge der Länge 0 (null) in eine Spalte ein, stattdessen wird stattdessen ein NULL-Wert eingefügt.|
