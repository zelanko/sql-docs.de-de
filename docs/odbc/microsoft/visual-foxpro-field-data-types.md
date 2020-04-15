---
title: Visuelle FoxPro-Felddatentypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72313e0269c93bca9cb2561d89604c3c88c8567b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304801"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro-Felddatentypen
In der folgenden Tabelle sind die Werte für das *FieldType-Argument* in ALTER TABLE und CREATE TABLE aufgeführt und angegeben, ob *nFieldWidth-* und *nPrecision-Argumente* erforderlich sind.  
  
|*Fieldtype*|*NFieldWidth*|*nPräzision*|Beschreibung|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Zeichenfeld der Breite *n*|  
|D|-|-|Date|  
|F|N|d|Schwebendes numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|G|-|-|Allgemein|  
|I|-|-|Integer|  
|L|-|-|Logisch|  
|M|-|-|Memo|  
|N|N|d|Numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|T|-|-|Datetime|  
|J|-|-|Währung|
