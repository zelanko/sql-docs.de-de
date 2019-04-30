---
title: Einschränkungen von Spaltennamen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a80ed397ae494bc686ef76aaeeef10b61662f19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301811"
---
# <a name="column-name-limitations"></a>Einschränkungen für Spaltennamen
Spaltennamen können keine gültigen Zeichen (z. B. Leerzeichen) enthalten. Wenn Spaltennamen alle Zeichen mit Ausnahme von Buchstaben, Zahlen und Unterstriche enthalten, muss der Namen getrennt werden, indem Sie es in Back Anführungszeichen (') einschließen.  
  
 Wenn der Microsoft Access oder Microsoft Excel-Treiber verwendet wird, Spaltennamen sind auf 64 Zeichen beschränkt und längere Namen generiert einen Fehler. Wenn die Paradox-Treiber verwendet wird, ist der Spaltenname für die maximal 25 Zeichen. Wenn der Text-Treiber verwendet wird, wird der maximale Spaltenname beträgt 64 Zeichen, und längere Namen werden abgeschnitten.  
  
 Wenn die dBASE-Treiber verwendet wird, werden Zeichen mit ASCII-Wert größer als 127 zu unterstrichen konvertiert.  
  
 Wenn der Microsoft Excel-Treiber, verwendet wird wenn Spaltennamen vorhanden sind, müssen sie in der ersten Zeile sein. Ein Name, der in Microsoft Excel verwenden, würde die "!" Zeichen in Back Anführungszeichen (') eingeschlossen werden muss. Die "!" wird auf das Zeichen "$" Zeichen konvertiert, da die "!" Zeichen ist nicht zulässig, in einem ODBC-Namen, selbst wenn der Name in Back Anführungszeichen eingeschlossen ist. Alle anderen gültigen Microsoft Excel-Zeichen (mit Ausnahme von den senkrechten Strich (&#124;)) in einem Spaltennamen, einschließlich Leerzeichen verwendet werden können. Für den Namen einer Microsoft Excel-Spalte muss ein Begrenzungsbezeichner verwendet werden, ein Leerzeichen ein. Unbekannter Spaltennamen werden vom Treiber generierten Namen, z. B. "Col1" für die erste Spalte ersetzt.  
  
 Das Pipezeichen (&#124;) kann nicht in einem Spaltennamen verwendet werden, ob der Name in Back Anführungszeichen oder nicht eingeschlossen ist.  
  
 Wenn der Text-Treiber verwendet wird, umfasst der Treiber einen Standardnamen aus, wenn ein Spaltenname nicht angegeben ist. Beispielsweise ruft der Treiber der ersten Spalte F1, die zweite Spalte F2 und So weiter.
