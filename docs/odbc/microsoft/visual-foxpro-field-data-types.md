---
title: Visual FoxPro-Feld Datentypen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087954"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro-Felddatentypen
In der folgenden Tabelle sind die Werte für das *FieldType* -Argument in ALTER TABLE und CREATE TABLE aufgeführt. Außerdem wird angegeben, ob *nfieldwidth* -und *nprecision* -Argumente erforderlich sind.  
  
|*FieldType*|*Nfieldwidth*|*ngenauigkeit*|BESCHREIBUNG|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Zeichenfeld der Breite *n*|  
|D|-|-|Date|  
|F|N|d|Gleitendes numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|G|-|-|Allgemein|  
|I|-|-|Integer|  
|L|-|-|Logisch|  
|M|-|-|Anruf|  
|N|N|d|Numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|T|-|-|Datetime|  
|J|-|-|Currency|
