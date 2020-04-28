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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 814fca7d48f50aab51b6b4f7e34835be8c412e9c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306205"
---
# <a name="keyset-driven-cursors"></a>Keysetgesteuerte Cursor
Ein keysetgesteuertes Cursor liegt zwischen einem statischen und einem dynamischen Cursor, um Änderungen zu erkennen. Wie ein statischer Cursor ermittelt er nicht immer Änderungen an der Mitgliedschaft und Reihenfolge des Resultsets. Ebenso wie ein dynamischer Cursor werden Änderungen an den Werten der Zeilen im Resultset erkannt (abhängig von der Isolationsstufe der Transaktion, wie vom SQL_ATTR_TXN_ISOLATION Verbindungs Attribut festgelegt).  
  
 Beim Öffnen eines keysetgesteuerten Cursors werden die Schlüssel für das gesamte Resultset gespeichert. Dadurch wird die offensichtliche Mitgliedschaft und Reihenfolge des Resultsets korrigiert. Während der Cursor einen Bildlauf durch das Resultset durchführt, werden die Schlüssel in diesem *Keyset* verwendet, um die aktuellen Datenwerte für jede Zeile abzurufen. Nehmen Sie z. b. an, ein keysetgesteuerte Cursor Ruft eine Zeile ab, und die Zeile wird dann von einer anderen Anwendung aktualisiert. Wenn der Cursor die Zeile erneut abruft, sind die Werte, die Sie sehen, die neuen, da Sie die Zeile mit Ihrem Schlüssel erneut abgerufen haben. Aus diesem Grund erkennen die keysetgesteuerten Cursor immer Änderungen, die von sich selbst und anderen Vorgängen vorgenommen wurden.  
  
 Wenn der Cursor versucht, eine gelöschte Zeile abzurufen, wird diese Zeile als "Loch" im Resultset angezeigt: der Schlüssel für die Zeile ist im Keyset vorhanden, aber die Zeile ist im Resultset nicht mehr vorhanden. Wenn die Schlüsselwerte in einer Zeile aktualisiert werden, wird die Zeile als gelöscht und dann eingefügt, sodass diese Zeilen auch als Löcher im Resultset angezeigt werden. Während ein keysetgesteuertes Cursor immer von anderen gelöschte Zeilen erkennen kann, kann er optional die Schlüssel für Zeilen entfernen, die er selbst aus dem Keyset löscht. Durch keysetgesteuerte Cursor können keine eigenen Löschvorgänge erkannt werden. Ob ein bestimmter keysetgesteuerte Cursor seine eigenen Löschvorgänge erkennt, wird über die SQL_STATIC_SENSITIVITY-Option in **SQLGetInfo**gemeldet.  
  
 Zeilen, die von anderen eingefügt werden, sind für einen keysetgesteuerten Cursor nie sichtbar, da keine Schlüssel für diese Zeilen im Keyset vorhanden sind. Ein keysetgesteuerender Cursor kann jedoch optional die Schlüssel für die Zeilen hinzufügen, die er in das Keyset einfügt. Keysetgesteuerte Cursor, die dies tun, können eigene Einfügungen erkennen. Ob ein bestimmter keysetgesteuerte Cursor eigene Einfügungen erkennt, wird über die SQL_STATIC_SENSITIVITY-Option in **SQLGetInfo**gemeldet.  
  
 Das vom SQL_ATTR_ROW_STATUS_PTR Statement-Attribut angegebene Zeilen Status Array kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO oder SQL_ROW_ERROR für jede Zeile enthalten. Sie gibt SQL_ROW_UPDATED, SQL_ROW_DELETED oder SQL_ROW_ADDED für Zeilen zurück, die als aktualisiert, gelöscht oder eingefügt erkannt werden.  
  
 Keysetgesteuerte Cursor werden häufig implementiert, indem eine temporäre Tabelle erstellt wird, die die Schlüssel für jede Zeile im Resultset enthält. Da der Cursor auch bestimmen muss, ob Zeilen aktualisiert wurden, enthält diese Tabelle häufig auch eine Spalte mit Informationen zur Zeilen Versionsverwaltung.  
  
 Um einen Bildlauf zum ursprünglichen Resultset durchzuführen, öffnet der keysetgesteuerte Cursor einen statischen Cursor über der temporären Tabelle. Zum Abrufen einer Zeile im ursprünglichen Resultset ruft der Cursor zuerst den entsprechenden Schlüssel aus der temporären Tabelle ab und ruft dann die aktuellen Werte für die Zeile ab. Wenn Blockcursorn verwendet werden, muss der Cursor mehrere Schlüssel und Zeilen abrufen.
