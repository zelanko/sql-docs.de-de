---
title: Keysetgesteuerte Cursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- keyset-driven cursors [ODBC]
- cursors [ODBC], key-set driven
ms.assetid: 01769f43-1d9c-4685-84fa-15a6465335e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be6dc5a164220befb534368eace4f51f4dbd84e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719438"
---
# <a name="keyset-driven-cursors"></a>Keysetgesteuerte Cursor
Ein keysetgesteuerter Cursor befindet sich zwischen einer statischen und eines dynamischen Cursors in seiner Fähigkeit, Änderungen zu erkennen. Wie ein statischer Cursor erkennt es nicht immer Änderungen an die Mitgliedschaft und Reihenfolge des Resultsets. Wie einen dynamischen Cursor erkennt er Änderungen auf die Werte der Zeilen im Resultset (je nach die Isolationsstufe der Transaktion, wie durch das Verbindungsattribut SQL_ATTR_TXN_ISOLATION festgelegt).  
  
 Wenn ein keysetgesteuerter Cursor geöffnet wird, werden die Schlüssel für das gesamte Resultset gespeichert; Dies behebt die scheinbare Mitgliedschaft und Reihenfolge des Resultsets. Wenn der Cursor über das Resultset einen Bildlauf durchführt, verwendet es die Schlüssel in diesem *Keyset* zum Abrufen der aktuellen Datenwerte für jede Zeile. Nehmen wir beispielsweise an ein keysetgesteuerter Cursor abruft, eine Zeile und eine andere Anwendung wird diese Zeile aktualisiert. Wenn der Cursor die Zeile refetches, sind die Werte, die erkennt neue, da sie die Zeile mit dem Schlüssel erneut abgerufen. Aus diesem Grund erkennen die keysetgesteuerte Cursor immer von sich selbst und anderen Benutzern vorgenommene Änderungen.  
  
 Wenn der Cursor versucht, eine Zeile abzurufen, das gelöscht wurde, wird diese Zeile als einer "Lücke" im Resultset angezeigt: der Schlüssel für die Zeile vorhanden ist, im Keyset, aber die Zeile im Resultset nicht mehr vorhanden ist. Wenn die Schlüsselwerte in einer Zeile aktualisiert werden, gilt die Zeile als gelöscht wurden und dann eingefügt werden, damit solche Zeilen auch als Lücken im Resultset angezeigt werden. Während ein keysetgesteuerten Cursors immer von anderen Benutzern gelöschte Zeilen erkennen kann, können sie optional entfernen, auf die Schlüssel für die Zeilen löscht selbst über das Keyset. Keysetgesteuerte Cursor, die dazu ihre eigenen Löschvorgänge nicht erkannt werden. Gibt an, ob ein bestimmter keysetgesteuerter Cursor einen eigenen Löschvorgänge erkennt wird gemeldet, über die Feedbackoption im SQL_STATIC_SENSITIVITY in **SQLGetInfo**.  
  
 Zeilen, die von anderen Benutzern eingefügt sind nie in einen Keyset-gesteuerten Cursor sichtbar, da keine Schlüssel für diese Zeilen im Keyset vorhanden sind. Ein keysetgesteuerter Cursor kann jedoch optional hinzufügen, die Schlüssel für die Zeilen fügt sich selbst um das Keyset. Keysetgesteuerte Cursor, die diesem Zweck können eigene einfügungen ermittelt werden. Gibt an, ob ein bestimmter keysetgesteuerter Cursor eine eigene einfügungen erkennt, wird gemeldet, über die Feedbackoption im SQL_STATIC_SENSITIVITY in **SQLGetInfo**.  
  
 Die vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegebenen zeilenstatusarray kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO oder SQL_ROW_ERROR für jede Zeile enthalten. SQL_ROW_UPDATED, SQL_ROW_DELETED, SQL_ROW_ADDED für Zeilen, die erkannt wird als aktualisiert, gelöscht oder eingefügt wird.  
  
 Keysetgesteuerte Cursor werden häufig implementiert, durch das Erstellen einer temporären Tabelle, die die Schlüssel für jede Zeile im Resultset enthält. Da auch der Cursor festlegen muss, ob die Zeilen aktualisiert wurden, enthält diese Tabelle auch eine Spalte mit zeilenversionsverwaltungs-Informationen.  
  
 Über die ursprünglichen Resultset einen Bildlauf durchführen, öffnet der keysetgesteuerte Cursor einen statischen Cursor für die temporäre Tabelle. Um eine Zeile im ursprünglichen Resultset abzurufen, wird der Cursor zuerst den entsprechenden Schlüssel aus der temporären Tabelle abruft, und ruft dann die aktuellen Werte für die Zeile ab. Wenn Blockcursor verwendet werden, muss der Cursor mehrere Schlüssel und Zeilen abrufen.
