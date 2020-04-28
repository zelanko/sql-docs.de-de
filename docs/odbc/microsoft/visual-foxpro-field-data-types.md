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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72313e0269c93bca9cb2561d89604c3c88c8567b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304801"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro-Felddatentypen
In der folgenden Tabelle sind die Werte für das *FieldType* -Argument in ALTER TABLE und CREATE TABLE aufgeführt. Außerdem wird angegeben, ob *nfieldwidth* -und *nprecision* -Argumente erforderlich sind.  
  
|*FieldType*|*Nfieldwidth*|*ngenauigkeit*|BESCHREIBUNG|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|Zeichenfeld der Breite *n*|  
|D|-|-|Datum|  
|F|N|d|Gleitendes numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|G|-|-|Allgemein|  
|I|-|-|Integer|  
|L|-|-|Logisch|  
|M|-|-|Memo|  
|N|N|d|Numerisches Feld der Breite *n* mit *d* Dezimalstellen|  
|T|-|-|DateTime|  
|J|-|-|Währung|
