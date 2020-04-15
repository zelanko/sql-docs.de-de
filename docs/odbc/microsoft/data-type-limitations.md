---
title: Einschränkungen der Datenart | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280670"
---
# <a name="data-type-limitations"></a>Einschränkungen für Datumstypen
Die Microsoft ODBC-Desktopdatenbanktreiber setzen die folgenden Einschränkungen für Datentypen auf:  
  
|Datentyp|BESCHREIBUNG|  
|---------------|-----------------|  
|Alle Datentypen|Typkonvertierungsfehler können dazu führen, dass die betroffene Spalte auf NULL festgelegt wird.|  
|BINARY|Beim Erstellen einer BINARY-Spalte mit einer Länge von null wird tatsächlich eine BINARY-Spalte mit 255 Byte zurückgegeben.|  
|DATE|Der DATE-Datentyp kann nicht von der CONVERT-Funktion in einen anderen Datentyp (oder sich selbst) konvertiert werden.|  
|DECIMAL (Genau numerisch)|Wird nicht unterstützt.|  
|Gleitkommadatentypen|Die Anzahl der Dezimalstellen in einer Gleitkommazahl kann durch das ImBereich International der Windows-Systemsteuerung festgelegte Zahlenformat begrenzt werden.|  
|NUMERIC|Unterstützt maximale Präzision und eine Skala von 28.|  
|timestamp|Der TIMESTAMP-Datentyp kann von der CONVERT-Funktion nicht in sich selbst konvertiert werden.|  
|TINYINT|TINYINT-Werte sind immer nicht signiert.|  
|Null-Länge Strings|Wenn ein dBASE, Microsoft Excel, Paradox oder Textdriver verwendet wird, fügt das Einfügen einer Zeichenfolge mit null Länge in eine Spalte stattdessen einen NULL-Wert ein.|
