---
title: Keyset-gesteuerte Cursor | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 814fca7d48f50aab51b6b4f7e34835be8c412e9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306205"
---
# <a name="keyset-driven-cursors"></a>Keysetgesteuerte Cursor
Ein keyset-gesteuerter Cursor liegt zwischen einem statischen und einem dynamischen Cursor in seiner Fähigkeit, Änderungen zu erkennen. Wie ein statischer Cursor ermittelt er nicht immer Änderungen an der Mitgliedschaft und Reihenfolge des Resultsets. Wie ein dynamischer Cursor erkennt er Änderungen an den Werten von Zeilen im Resultset (vorbehaltlich der Isolationsstufe der Transaktion, die durch das SQL_ATTR_TXN_ISOLATION Verbindungsattribut festgelegt wird).  
  
 Wenn ein Keyset-gesteuerter Cursor geöffnet wird, werden die Schlüssel für das gesamte Resultset speichert. Dadurch werden die scheinbare Mitgliedschaft und Reihenfolge des Resultsets behoben. Wenn der Cursor durch das Resultset scrollt, verwendet er die Schlüssel in diesem *Keyset,* um die aktuellen Datenwerte für jede Zeile abzurufen. Angenommen, ein keyset-gesteuerter Cursor ruft eine Zeile ab, und eine andere Anwendung aktualisiert diese Zeile. Wenn der Cursor die Zeile erneut abruft, werden die angezeigten Werte neu angezeigt, da die Zeile mit ihrem Schlüssel erneut abgerufen wurde. Aus diesem Grund erkennen die Keyset-gesteuerten Cursor immer Änderungen, die von sich selbst und anderen vorgenommen wurden.  
  
 Wenn der Cursor versucht, eine gelöschte Zeile abzurufen, wird diese Zeile als "Loch" im Resultset angezeigt: Der Schlüssel für die Zeile ist im Keyset vorhanden, aber die Zeile ist nicht mehr im Resultset vorhanden. Wenn die Schlüsselwerte in einer Zeile aktualisiert werden, wird die Zeile als gelöscht und dann eingefügt betrachtet, sodass solche Zeilen auch als Löcher in der Ergebnismenge angezeigt werden. Während ein keyset-gesteuerter Cursor immer zeilen erkennen kann, die von anderen gelöscht wurden, kann er optional die Schlüssel für Zeilen entfernen, die er selbst aus dem Keyset löscht. Keyset-gesteuerte Cursor, die dies tun, können ihre eigenen Löschungen nicht erkennen. Ob ein bestimmter Keyset-gesteuerter Cursor seine eigenen Löschungen erkennt, wird über die Option SQL_STATIC_SENSITIVITY in **SQLGetInfo**gemeldet.  
  
 Von anderen eingefügten Zeilen sind für einen keyset-gesteuerten Cursor nie sichtbar, da keine Schlüssel für diese Zeilen im Keyset vorhanden sind. Ein Keyset-gesteuerter Cursor kann jedoch optional die Schlüssel für Zeilen hinzufügen, die er selbst in das Keyset einfügt. Keyset-gesteuerte Cursor, die dies tun, können ihre eigenen Einfügungen erkennen. Ob ein bestimmter Keyset-gesteuerter Cursor seine eigenen Einfügungen erkennt, wird über die Option SQL_STATIC_SENSITIVITY in **SQLGetInfo**gemeldet.  
  
 Das vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegebene Zeilenstatusarray kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO oder SQL_ROW_ERROR für eine zeile enthalten. Es gibt SQL_ROW_UPDATED, SQL_ROW_DELETED oder SQL_ROW_ADDED für Zeilen zurück, die als aktualisiert, gelöscht oder eingefügt erkannt werden.  
  
 Keyset-gesteuerte Cursor werden häufig implementiert, indem eine temporäre Tabelle erstellt wird, die die Schlüssel für jede Zeile im Resultset enthält. Da der Cursor auch bestimmen muss, ob Zeilen aktualisiert wurden, enthält diese Tabelle häufig auch eine Spalte mit Zeilenversionsinformationen.  
  
 Um über das ursprüngliche Resultset zu scrollen, öffnet der mit Keyset gesteuerte Cursor einen statischen Cursor über der temporären Tabelle. Um eine Zeile im ursprünglichen Resultset abzurufen, ruft der Cursor zuerst den entsprechenden Schlüssel aus der temporären Tabelle und dann die aktuellen Werte für die Zeile ab. Wenn Blockcursor verwendet werden, muss der Cursor mehrere Schlüssel und Zeilen abrufen.
