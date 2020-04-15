---
title: SQLColAttributes-Zuordnung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c2c8386d6771141eaa0145a5d5964d70d6084d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305416"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes-Zuordnung
Wenn eine Anwendung **SQLColAttributes** über einen ODBC *3.x-Treiber* aufruft, wird der Aufruf von **SQLColAttributes** **SQLColAttributes** wie folgt zugeordnet:  
  
> [!NOTE]
>  Das präfix, das in *FieldIdentifier-Werten* in ODBC *3.x* verwendet wird, wurde von dem in ODBC *2.x*verwendeten Präfix geändert. Das neue Präfix lautet "SQL_DESC"; das alte Präfix war "SQL_COLUMN".  
  
1.  Wenn es sich bei der Anwendung um eine ODBC *2.x-Anwendung* handelt, *fDescType* SQL_COLUMN_TYPE ist und der zurückgegebene Typ ein prägnanter DATETIME-Typ ist, ordnet der Treiber-Manager die Rückgabewerte für Datums-, Uhrzeit- und Zeitstempelcodes zu.  
  
2.  Wenn *fDescType* SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE oder SQL_COLUMN_COUNT ist, ruft der Treiber-Manager **SQLColAttribute** im Treiber auf, wobei das *FieldIdentifier-Argument* SQL_DESC_NAME, SQL_DESC_NULLABLE oder SQL_DESC_COUNT zugeordnet*ist.* Alle anderen Werte von *fDescType* werden an den Treiber übergeben.  
  
 Ein ODBC *3.x-Treiber* muss alle ODBC *3.x* *FieldIdentifiers* unterstützen, die für **SQLColAttribute**aufgeführt sind.  
  
 Ein ODBC *3.x-Treiber* muss SQL_COLUMN_PRECISION und SQL_DESC_PRECISION, SQL_COLUMN_SCALE und SQL_DESC_SCALE sowie SQL_COLUMN_LENGTH und SQL_DESC_LENGTH unterstützen. Diese Werte unterscheiden sich, da Genauigkeit, Skalierung und Länge in ODBC *3.x* anders definiert sind als in ODBC *2.x*. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.
