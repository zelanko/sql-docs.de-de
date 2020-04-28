---
title: Einschränkungen für Tabellennamen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 738c563961eae56471f0238d9726a1ebb0bdc76e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81289216"
---
# <a name="table-name-limitations"></a>Einschränkungen für Tabellennamen
Tabellennamen können beliebige gültige Zeichen (z. b. Leerzeichen) enthalten. Wenn Tabellennamen Zeichen enthalten, ausgenommen Buchstaben, Ziffern und Unterstriche, muss der Name begrenzt werden, indem er in backanführungs Zeichen (') eingeschlossen wird.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird und ein Tabellenname nicht durch einen Daten Bank Verweis qualifiziert ist, wird die Standarddatenbank impliziert. Wenn ein Name in Microsoft Excel das Zeichen "!" enthält, wird er stattdessen automatisch in das Zeichen "$" übersetzt.  
  
 Der Microsoft Excel-Tabellenname, \<der auf filename verweist> wird für Microsoft Excel 3,0-und 4,0-Dateien unterstützt. Der Microsoft Excel-Tabellenname, \<der auf Arbeitsmappenname> verweist, wird für Microsoft Excel 5,0-, 7,0-oder 97-Dateien unterstützt.  
  
 Wenn der dBase-Treiber verwendet wird, werden Zeichen mit einem ASCII-Wert größer als 127 in Unterstriche konvertiert.  
  
 Wenn der Microsoft Access-Treiber verwendet wird, ist der Tabellenname auf 64 Zeichen beschränkt.  
  
 Wenn die dBASE-, Microsoft Excel 3,0-oder 4,0-, Paradox-oder Text-Treiber verwendet werden, sollten die speziellen MS-DOS-Schlüsselwörter con, AUX, LPT1 und LPT2 nicht als Tabellennamen verwendet werden.
