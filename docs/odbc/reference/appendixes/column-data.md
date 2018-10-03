---
title: Spaltendaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 0425818c-9469-493f-9e3c-fc03d9411c5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95f80c82d3804e31d5ea29d55af0fbedd4184e6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695149"
---
# <a name="column-data"></a>Spaltendaten
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die Cursorbibliothek erstellt einen Puffer im Cache für jeden Datenpuffer gebunden werden, um das Resultset mit **SQLBindCol**. Er verwendet die Werte in diesen Puffern zum Erstellen einer **, in denen** -Klausel, wenn es eine positionierte emuliert update oder delete-Anweisung. Diese Puffer von den Puffern Rowset aktualisiert, wenn er ruft Daten aus der Datenquelle und die Ausführung der positionierte Update-Anweisungen ab.  
  
 Wenn die Cursorbibliothek seinem Cache in den Puffern Rowset aktualisiert wird, erfolgt die Übertragung der Daten gemäß dem C-Datentyp, der im angegebenen **SQLBindCol**. Beispielsweise ist der C-Datentyp, der ein Rowset Puffer SQL_C_SLONG, überträgt die Cursorbibliothek vier Byte an Daten; ist dies SQL_C_CHAR und *Pufferlänge* 10, die Cursorbibliothek werden 10 Byte an Daten übertragen. Die Cursorbibliothek führt kein typüberprüfung oder Konvertierungen für die Daten aus, die es überträgt.  
  
> [!NOTE]  
>  Die Cursorbibliothek nicht seinem Cache nach einer Spalte aktualisiert, wenn **StrLen_or_IndPtr* in das entsprechende Rowset Puffer SQL_DATA_AT_EXEC oder das Ergebnis des Makros SQL_LEN_DATA_AT_EXEC ist.  
  
 Wenn sie eine Spalte, eine leere-Pads Zeichen mit fester Länge Datenquellendaten und 0 (null)-Pads fester Länge, binäre Daten nach Bedarf aktualisiert. Eine Datenquelle speichert z. B. "Smith" in einer char(10)-Spalte vom Datentyp als "Smith". Die Cursorbibliothek ist nicht mit Leerzeichen aufgefüllt oder 0 (null)-Pad-Daten in den Puffern Rowset, wenn sie diese Daten in seinem Cache kopiert, nach der Ausführung einer positioniertes Update-Anweisung. Aus diesem Grund, wenn eine Anwendung erfordert, dass die Werte in die Cursorbibliothek-Cache mit Leerzeichen aufgefüllt oder mit Nullen aufgefüllt sind, muss er mit Leerzeichen aufgefüllt oder mit Nullen aufgefüllt die Werte in den Puffern Rowsets vor der Ausführung einer positioniertes Update-Anweisung.
