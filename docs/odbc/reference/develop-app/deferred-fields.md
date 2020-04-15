---
title: Verzögerte Felder | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 094aba353e10ed568e1959b1d655109296507dee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305971"
---
# <a name="deferred-fields"></a>Zurückgestellte Felder
Die Werte der *verzögerten Felder* werden nicht verwendet, wenn sie festgelegt werden, aber der Treiber speichert die Adressen der Variablen für einen verzögerten Effekt. Für einen Anwendungsparameterdeskriptor verwendet der Treiber den Inhalt der Variablen zum Zeitpunkt des Aufrufs von **SQLExecDirect** oder **SQLExecute**. Für einen Anwendungszeilendeskriptor verwendet der Treiber den Inhalt der Variablen zum Zeitpunkt des Abrufs.  
  
 Folgende Felder sind zurückgestellt:  
  
-   Die SQL_DESC_DATA_PTR und SQL_DESC_INDICATOR_PTR Felder eines Deskriptordatensatzes.  
  
-   Das SQL_DESC_OCTET_LENGTH_PTR Feld eines Anwendungsdeskriptordatensatzes.  
  
-   Bei einem mehrzeiligen Abruf werden die Felder SQL_DESC_ARRAY_STATUS_PTR und SQL_DESC_ROWS_PROCESSED_PTR eines Deskriptorheaders.  
  
 Wenn ein Deskriptor zugewiesen wird, haben die verzögerten Felder jedes Deskriptordatensatzes zunächst einen NULL-Wert. Die Bedeutung des NULL-Werts ist wie folgt:  
  
-   Wenn SQL_DESC_ARRAY_STATUS_PTR einen NULL-Wert hat, kann ein mehrreihiges Abruf diese Komponente der Diagnoseinformationen pro Zeile nicht zurückgeben.  
  
-   Wenn SQL_DESC_DATA_PTR einen NULL-Wert hat, ist der Datensatz ungebunden.  
  
-   Wenn das SQL_DESC_OCTET_LENGTH_PTR Feld einer ARD einen Nullwert hat, gibt der Treiber keine Längeninformationen für diese Spalte zurück.  
  
-   Wenn das SQL_DESC_OCTET_LENGTH_PTR Feld einer APD einen NULL-Wert hat und der Parameter eine Zeichenfolge ist, geht der Treiber davon aus, dass die Zeichenfolge null-terminiert ist. Bei dynamischen Ausgabeparametern verhindert ein Nullwert in diesem Feld, dass der Treiber Längeninformationen zurückgibt. (Wenn das Feld SQL_DESC_TYPE keinen Zeichenzeichenfolgenparameter angibt, wird das SQL_DESC_OCTET_LENGTH_PTR Feld ignoriert.)  
  
 Die Anwendung darf Variablen, die für verzögerte Felder verwendet werden, nicht zwischen dem Zeitpunkt, zu dem sie den Feldern zugeordnet werden, und dem Zeitpunkt, zu dem der Treiber sie liest oder schreibt, aballocateen oder verwerfen.
