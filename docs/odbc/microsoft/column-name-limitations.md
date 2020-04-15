---
title: Einschränkungen des Spaltennamens | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], column names
- ODBC desktop database drivers [ODBC], column names
ms.assetid: 5a339f61-c52f-40ad-8deb-d785f72753d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41d973afdac360af114da41620997cad23a2c740
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281380"
---
# <a name="column-name-limitations"></a>Einschränkungen für Spaltennamen
Spaltennamen können beliebige gültige Zeichen (z. B. Leerzeichen) enthalten. Wenn Spaltennamen Zeichen außer Buchstaben, Zahlen und Unterstrichen enthalten, muss der Name durch Einschließen in Anführungszeichen (') getrennt werden.  
  
 Wenn der Microsoft Access- oder Microsoft Excel-Treiber verwendet wird, sind Spaltennamen auf 64 Zeichen beschränkt, und längere Namen generieren einen Fehler. Wenn der Paradox-Treiber verwendet wird, beträgt der maximale Spaltenname 25 Zeichen. Wenn der Texttreiber verwendet wird, beträgt der maximale Spaltenname 64 Zeichen, und längere Namen werden abgeschnitten.  
  
 Wenn der dBASE-Treiber verwendet wird, werden Zeichen mit einem ASCII-Wert größer als 127 in Unterstriche konvertiert.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, müssen Spaltennamen in der ersten Zeile vorhanden sein. Ein Name, der in Microsoft Excel das Zeichen "!" verwenden würde, muss in Anführungszeichen (') eingeschlossen werden. Das Zeichen "!" wird in das Zeichen "A" konvertiert, da das Zeichen "!" in einem ODBC-Namen nicht legal ist, selbst wenn der Name in Rückzeichen eingeschlossen ist. Alle anderen gültigen Microsoft Excel-Zeichen (mit Ausnahme des &#124;) können in einem Spaltennamen verwendet werden, einschließlich Leerzeichen. Ein durch Trennzeichen getrennter Bezeichner muss für einen Microsoft Excel-Spaltennamen verwendet werden, um ein Leerzeichen einzuschließen. Nicht angegebene Spaltennamen werden durch vom Treiber generierte Namen ersetzt, z. B. "Col1" für die erste Spalte.  
  
 Das Rohrzeichen (&#124;) kann nicht in einem Spaltennamen verwendet werden, unabhängig davon, ob der Name in Rückzeichen eingeschlossen ist oder nicht.  
  
 Wenn der Texttreiber verwendet wird, gibt der Treiber einen Standardnamen an, wenn kein Spaltenname angegeben ist. Der Treiber ruft z. B. die erste Spalte F1, die zweite Spalte F2 usw. auf.
