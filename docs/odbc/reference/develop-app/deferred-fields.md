---
title: Verzögerte Felder | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c7800e7da867b4eb0c34fa3feeba5edb2d41cd6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721038"
---
# <a name="deferred-fields"></a>Zurückgestellte Felder
Die Werte der *verzögert Felder* werden nicht verwendet werden, werden die Werte festgelegt, aber der Treiber speichert die Adressen der mit den Variablen für einen verzögerten Effekt. Für eine Anwendung Parameter Descriptor, verwendet der Treiber den Inhalt der Variablen zum Zeitpunkt des Aufrufs von **SQLExecDirect** oder **SQLExecute**. Für einen Anwendungsdienst-Zeile-Deskriptor verwendet der Treiber den Inhalt der Variablen zum Zeitpunkt des Abrufs.  
  
 Im folgenden sind die zurückgestellte Felder:  
  
-   Die SQL_DESC_DATA_PTR und SQL_DESC_INDICATOR_PTR Felder von einem anwendungsparameterdeskriptor-Datensatz.  
  
-   Das von einer Anwendung anwendungsparameterdeskriptor-Datensatz SQL_DESC_OCTET_LENGTH_PTR-Feld.  
  
-   Bei einer Einfügung mehrerer Zeilen abrufen die SQL_DESC_ARRAY_STATUS_PTR und SQL_DESC_ROWS_PROCESSED_PTR Felder für einen Deskriptor-Header.  
  
 Wenn ein Deskriptor zugeordnet ist, haben die zurückgestellte Felder jedes Datensatzes Deskriptor zunächst einen null-Wert. Die Bedeutung des null-Werts lautet wie folgt aus:  
  
-   Wenn SQL_DESC_ARRAY_STATUS_PTR einen null-Wert verfügt, kann eine Falls Fetch diese Komponente Diagnoseinformationen pro Zeile zurück.  
  
-   Wenn SQL_DESC_DATA_PTR einen null-Wert verfügt, wird der Datensatz aufgehoben.  
  
-   Wenn das Feld SQL_DESC_OCTET_LENGTH_PTR ein ARD einen null-Wert verfügt, gibt der Treiber nicht Längeninformationen für diese Spalte zurück.  
  
-   Wenn das Feld SQL_DESC_OCTET_LENGTH_PTR ein APD einen null-Wert hat, und der Parameter eine Zeichenfolge ist, wird der Treiber davon ausgegangen, dass Null-terminierte Zeichenfolge ist. Für dynamische Output-Parameter wird verhindert, dass ein null-Wert in diesem Feld den Treiber Längeninformationen zurückgeben. (Wenn das SQL_DESC_TYPE-Feld einen Zeichenfolge Parameter nicht angegeben, wird das Feld "SQL_DESC_OCTET_LENGTH_PTR" ignoriert.)  
  
 Die Anwendung muss nicht aufheben der Zuordnung oder verwerfen von Variablen, die für die zurückgestellte Felder zwischen dem Zeitpunkt, die sie mit den Feldern wird und die Uhrzeit, die der Treiber liest oder schreibt sie, verwendet werden.
