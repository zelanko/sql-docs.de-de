---
title: KEYSET-Cursor | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Keyset cursors [ADO]
- cursors [ADO], Keyset
ms.assetid: 14b51b17-6fd9-4146-af45-ca4b0fe6d48a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c7a12d1579af407bca77c9fa61d660a84a09f04e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924912"
---
# <a name="keyset-cursors"></a>KEYSET-Cursor
Der Keyset-Cursor bietet Funktionalität zwischen statischen und eines dynamischen Cursors in seiner Fähigkeit, Änderungen zu erkennen. Wie ein statischer Cursor ermittelt er nicht immer Änderungen an der Mitgliedschaft und Reihenfolge des Resultsets. Wie ein dynamischer Cursor ermittelt er Änderungen an den Werten der Zeilen im Resultset.  
  
 Keysetgesteuerte Cursor werden von einer Reihe von eindeutigen Bezeichnern (Schlüssel) gesteuert, die als das Keyset bezeichnet werden. Die Schlüssel werden anhand einer Reihe von Spalten erstellt, die die Zeilen im Resultset eindeutig identifizieren. Das Keyset besteht aus Schlüsselwerten aus allen Zeilen, die von der Abfrageanweisung zurückgegeben werden.  
  
 Mit einem keysetgesteuerten Cursor wird für jede Zeile im Cursor ein Schlüssel erstellt und gespeichert, der wiederum entweder auf der Clientarbeitsstation oder dem Server gespeichert wird. Wenn Sie auf eine beliebige Zeile zugreifen, wird der gespeicherte Schlüssel zum Abrufen der aktuellen Datenwerte aus der Datenquelle verwendet. In einem keysetgesteuerter Cursor wird die Mitgliedschaft des Resultsets fixiert, wenn das Keyset vollständig gefüllt wurde. Daher sind Ergänzungen und Updates, die die Mitgliedschaft betreffen, nicht Teil des Resultsets, bis dieses neu geöffnet wird.  
  
 Änderungen an Datenwerten (vorgenommen hat, entweder durch den Besitzer des Keyset oder andere Prozesse) sind sichtbar, wenn der Benutzer über das Resultset einen Bildlauf durchführt. INSERTs außerhalb des Cursors (durch andere Prozesse) sind nur sichtbar, wenn der Cursor beendet und neu gestartet wird. INSERTs innerhalb des Cursors werden am Ende des Resultsets angezeigt.  
  
 Wenn ein keysetgesteuerter Cursor versucht, eine Zeile abzurufen, die gelöscht wurde, wird die Zeile als einer "Lücke" im Resultset angezeigt. Der Schlüssel für die Zeile ist im Keyset enthalten, aber die Zeile ist nicht mehr im Resultset vorhanden. Wenn die Schlüsselwerte in einer Zeile aktualisiert werden, gilt die Zeile als gelöscht wurden und dann eingefügt werden, damit solche Zeilen auch als Lücken im Resultset angezeigt werden. Während ein keysetgesteuerten Cursors immer durch andere Prozesse gelöschte Zeilen erkennen kann, können sie optional die Schlüssel für die Zeilen entfernen, die er selbst löscht. Keysetgesteuerte Cursor, die dazu ihre eigenen Löschvorgänge nicht erkannt werden, da die Beweise entfernt wurde.  
  
 Ein Update für eine Schlüsselspalte funktioniert wie dem Löschen der den alten Schlüssel und einer Einfügung des neuen Schlüssels. Der neue Schlüsselwert ist nicht sichtbar, wenn das Update nicht über den Cursor erfolgte. Wenn das Update über den Cursor erstellt wurde, ist der neue Schlüssel-Wert am Ende des Resultsets sichtbar.  
  
 Es ist eine Abwandlung keysetgesteuerte Cursor keysetgesteuerte standard Cursor aufgerufen. In einem keysetgesteuerten standard Cursor die Mitgliedschaft der Zeilen im Resultset und die Reihenfolge der Zeilen auf Cursor Öffnungszeit, aber Änderungen an Werten, die vom cursorbesitzer vorgenommen werden und per Commit ausgeführte Änderungen, die von anderen Prozessen sichtbar sind. Wenn eine Änderung eine Zeile für die Mitgliedschaft ausschließt oder wirkt sich auf die Reihenfolge einer Zeile, die Zeile nicht entfernt oder verschoben werden, wenn der Cursor geschlossen und erneut geöffnet wird. Eingefügte Daten werden nicht angezeigt, aber Änderungen an vorhandenen Daten werden immer dann angezeigt, da die Zeilen abgerufen werden.  
  
 Der keysetgesteuerte Cursor ist schwierig, da die Sensitivität gegenüber datenänderungen, vielen unterschiedlichen Situationen abhängt ordnungsgemäß zu verwenden, wie oben beschrieben. Wenn Ihre Anwendung nicht das gleichzeitige Updates betrifft, programmgesteuerte der ungültigen Schlüssel Behandlung kann und muss bestimmte schlüsselgebundenen Zeilen direkt zugreifen, funktioniert jedoch möglicherweise der keysetgesteuerte Cursor für Sie. Verwenden Sie die **AdOpenKeyset CursorTypeEnum** um anzugeben, dass Sie einen Keyset-Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
