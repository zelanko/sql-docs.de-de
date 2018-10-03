---
title: Visual FoxPro-Felddatentypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07aa06eae9f1e75a047bdd302754d884790436e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806120"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro-Felddatentypen
Die folgende Tabelle enthält die Werte für die *FieldType* -Argument in der ALTER TABLE und CREATE TABLE und gibt an, ob *nFieldWidth* und *nPrecision* Argumente sind Erforderlich.  
  
|*Feldtyp*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|c|N|-|Zeichenfeld der Breite *n*|  
|D|-|-|date|  
|V|N|d|Unverankerte numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|G|-|-|Allgemein|  
|I|-|-|Integer|  
|L|-|-|Logische Operatoren|  
|M|-|-|Memo|  
|N|N|d|Numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|T|-|-|datetime|  
|J|-|-|Währung|
