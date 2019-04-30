---
title: Erstellen von komplexen Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 616e4241c6d28e846a56116a70e79254e13dd5fb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224553"
---
# <a name="constructing-searched-statements"></a>Erstellen von searched-Anweisungen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Um unterstützen positioniertes Update und delete-Anweisungen, die Cursorbibliothek erstellt eine gesuchte **aktualisieren** oder **löschen** der Anweisung positioniert. Um Aufrufe unterstützen **SQLGetData** in einen Block von Daten, die Cursorbibliothek wird erstellt, eine gesuchte **wählen** Anweisung, um ein Resultset erstellen festlegen, die die aktuelle Zeile der Daten enthält. In jeder von diesen Anweisungen wird die **, in denen** Klausel Listet die Werte, die im Cache für jede gebundene Spalte, die für die SQL_DESC_SEARCHABLE-Feld-ID in SQL_PRED_SEARCHABLE oder SQL_PRED_BASIC zurückgibt gespeicherten  **SQLColAttribute**.  
  
> [!CAUTION]  
>  Die **, in denen** Klausel erstellt, die von der Cursorbibliothek zum Identifizieren der aktuellen Zeile kann möglicherweise keine Zeilen zu identifizieren, identifizieren eine andere Zeile oder mehr als eine Zeile zu identifizieren.  
  
 Wenn ein positioniertes Update oder Delete-Anweisung mehrere Zeilen auswirkt, wird die Cursorbibliothek die zeilenstatusarray nur für die Zeile, auf der der Cursor positioniert ist, und gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01001 (Konflikt beim Cursorvorgang) aktualisiert. Wenn die Anweisung keine Zeilen identifiziert, wird die Cursorbibliothek die zeilenstatusarray nicht aktualisiert, und gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01001 (Konflikt beim Cursorvorgang). Kann eine Anwendung aufrufen **SQLRowCount** um die Anzahl der Zeilen zu bestimmen, die aktualisiert oder gelöscht wurden.  
  
 Wenn die **wählen** -Klausel, um die Positionierung des Cursors für einen Aufruf von **SQLGetData** mehr als eine Zeile identifiziert **SQLGetData** ist nicht unbedingt die richtigen Daten zurückgegeben. Wenn sie keine Zeilen identifiziert **SQLGetData** SQL_NO_DATA zurückgibt.  
  
 Wenn eine Anwendung die folgenden Richtlinien, entspricht die **, in denen** Klausel erstellt, die von der Cursorbibliothek sollte die aktuelle Zeile, es sei denn, dies nicht möglich, z. B. wenn die Datenquelle enthält, auf doppelte, eindeutig identifiziert Zeilen.  
  
-   **Binden von Spalten, die die Zeile eindeutig identifizieren.** Wenn die gebundenen Spalten die Zeile ist nicht eindeutig identifizieren die **, in denen** Klausel erstellt, die von der Cursorbibliothek kann mehr als eine Zeile zu identifizieren. In einem positioniertes Update oder Delete-Anweisung gibt möglicherweise eine solche Klausel mehr als eine Zeile aktualisiert oder gelöscht werden. In einem Aufruf von **SQLGetData**, diese Klausel kann dazu führen, dass den Treiber Daten für die falsche Zeile zurückgeben. Binden alle Spalten in einen eindeutigen Schlüssel wird sichergestellt, dass jede Zeile eindeutig identifiziert wird.  
  
-   **Zuordnen von Datenpuffern groß genug ist, die kein Abschneiden erfolgt.** Die Cursorbibliothek-Cache ist eine Kopie der Werte in die Rowset-Puffer gebunden werden, um das Resultset mit **SQLBindCol**. Wenn Daten abgeschnitten werden, wenn sie in diesen Puffern platziert wird, wird sie auch im Cache gekürzt. Ein **, in denen** Klausel abgeschnittene Werte erstellt möglicherweise nicht ordnungsgemäß die zugrunde liegenden Zeile in der Datenquelle identifiziert.  
  
-   **Geben Sie die Länge von nicht-Null-Puffer für die C-Binärdaten.** Die Cursorbibliothek weist die Länge von Puffern in der Cache nur, wenn die *StrLen_or_IndPtr* -Argument in **SQLBindCol** ungleich Null ist. Wenn die *TargetType* -Argument SQL_C_BINARY ist, die Cursorbibliothek muss die Länge der binären Daten zum Erstellen einer **, in dem** Klausel aus den Daten. Es ist kein Puffer der Länge für eine SQL_C_BINARY-Spalte und die Anwendung ruft **SQLGetData** versucht hat, führen Sie ein positioniertes Update oder delete-Anweisung die Cursor-Bibliothek gibt SQL_ERROR zurück, und SQLSTATE SL014 (eine positioniert Anforderung ausgestellt wurde, und nicht alle Spaltenfelder Anzahl gepuffert wurden).  
  
-   **Geben Sie die Länge von nicht-Null-Puffer für Spalten mit NULL-Werte zulässt.** Die Cursorbibliothek weist die Länge von Puffern in der Cache nur, wenn die *StrLen_or_IndPtr* -Argument in **SQLBindCol** ungleich Null ist. Da SQL_NULL_DATA im Puffer Länge gespeichert wird, die Cursorbibliothek wird vorausgesetzt, jede Spalte, die der Puffer für die keine, die Länge angegeben ist NULL-Werte zulässt. Wenn keine Spalte mit der Länge für eine auf NULL festlegbare Spalte angegeben wird, erstellt die Cursorbibliothek eine **, in denen** -Klausel, den Wert für die Spalte verwendet. Diese Klausel wird nicht ordnungsgemäß auf die Zeile identifizieren.
