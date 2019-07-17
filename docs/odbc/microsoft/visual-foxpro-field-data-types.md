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
ms.openlocfilehash: 217058bf328677bf375d346ae7201c6eb81efa4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087954"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro-Felddatentypen
Die folgende Tabelle enthält die Werte für die *FieldType* -Argument in der ALTER TABLE und CREATE TABLE und gibt an, ob *nFieldWidth* und *nPrecision* Argumente sind Erforderlich.  
  
|*Feldtyp*|*NFieldWidth*|*nPrecision*|Beschreibung|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|T|Double|  
|c|N|-|Zeichenfeld der Breite *n*|  
|D|-|-|date|  
|V|N|T|Unverankerte numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|G|-|-|Allgemein|  
|I|-|-|Integer|  
|L|-|-|Logische Operatoren|  
|M|-|-|Memo|  
|N|N|T|Numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|T|-|-|DateTime|  
|J|-|-|Währung|
