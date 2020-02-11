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
ms.openlocfilehash: c2c229d31941d5cef0da253545cecd7d1496ee4a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076825"
---
# <a name="deferred-fields"></a>Zurückgestellte Felder
Die Werte von *verzögerten Feldern* werden nicht verwendet, wenn Sie festgelegt werden, aber der Treiber speichert die Adressen der Variablen für einen verzögerten Effekt. Für einen Anwendungsparameter Deskriptor verwendet der Treiber den Inhalt der Variablen zum Zeitpunkt des Aufrufens von **SQLExecDirect** oder **SQLExecute**. Bei einem Anwendungs Zeilen Deskriptor verwendet der Treiber den Inhalt der Variablen zum Zeitpunkt des Abruf Vorgangs.  
  
 Im folgenden werden verzögerte Felder aufgeführt:  
  
-   Die SQL_DESC_DATA_PTR-und SQL_DESC_INDICATOR_PTR Felder eines deskriptordaten Satzes.  
  
-   Das SQL_DESC_OCTET_LENGTH_PTR Feld eines Anwendungs deskriptordaten Satzes.  
  
-   Bei einem Abruf mehrerer Zeilen werden die Felder SQL_DESC_ARRAY_STATUS_PTR und SQL_DESC_ROWS_PROCESSED_PTR eines deskriptorheaders angezeigt.  
  
 Wenn ein Deskriptor zugeordnet ist, haben die zurück gestellten Felder der einzelnen deskriptordaten Sätze anfänglich einen NULL-Wert. Die Bedeutung des NULL-Werts lautet wie folgt:  
  
-   Wenn SQL_DESC_ARRAY_STATUS_PTR einen NULL-Wert aufweist, kann eine mehrzeilige Abruf Funktion diese Komponente der Diagnoseinformationen pro Zeile nicht zurückgeben.  
  
-   Wenn SQL_DESC_DATA_PTR einen NULL-Wert aufweist, wird der Datensatz nicht gebunden.  
  
-   Wenn das SQL_DESC_OCTET_LENGTH_PTR-Feld einer ARD einen NULL-Wert aufweist, gibt der Treiber keine Längen Informationen für diese Spalte zurück.  
  
-   Wenn das SQL_DESC_OCTET_LENGTH_PTR-Feld eines APD einen NULL-Wert aufweist und der-Parameter eine Zeichenfolge ist, geht der Treiber davon aus, dass die Zeichenfolge mit NULL endet. Für dynamische Ausgabeparameter verhindert ein NULL-Wert in diesem Feld, dass der Treiber keine Längen Informationen zurückgibt. (Wenn das SQL_DESC_TYPE Feld keinen Zeichen folgen Parameter angibt, wird das SQL_DESC_OCTET_LENGTH_PTR Feld ignoriert.)  
  
 Die Anwendung darf die Zuordnung von Variablen, die für verzögerte Felder verwendet werden, zwischen dem Zeitpunkt, zu dem Sie den Feldern zuordnet, und dem Zeitpunkt, zu dem der Treiber Sie liest oder schreibt, nicht aufgehoben
