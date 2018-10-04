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
manager: craigg
ms.openlocfilehash: a2ff246d01254ceb2b526b5118553d72cc499046
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726148"
---
# <a name="keyset-cursors"></a>KEYSET-Cursor
Der Keyset-Cursor bietet Funktionalität zwischen statischen und eines dynamischen Cursors in seiner Fähigkeit, Änderungen zu erkennen. Wie ein statischer Cursor erkennt es nicht immer Änderungen an die Mitgliedschaft und Reihenfolge des Resultsets. Wie einen dynamischen Cursor erkennt er Änderungen auf die Werte der Zeilen im Resultset.  
  
 Keysetgesteuerte Cursor werden von einem Satz von eindeutigen Bezeichnern (Schlüssel) als das Keyset bezeichnet gesteuert. Die Schlüssel werden anhand einer Reihe von Spalten erstellt, die die Zeilen im Resultset eindeutig identifizieren. Das Keyset ist die Menge der Schlüsselwerte aus allen Zeilen, die von der abfrageanweisung zurückgegeben.  
  
 Mit einem keysetgesteuerten Cursor ein Schlüssel erstellt und für jede Zeile im Cursor gespeichert und auf der Clientarbeitsstation oder auf dem Server gespeichert. Wenn Sie jede Zeile zugreifen, wird der gespeicherte Schlüssel verwendet, um die aktuellen Datenwerte aus der Datenquelle abzurufen. Resultset ist in einem keysetgesteuerten Cursor fixiert, wenn das Keyset vollständig gefüllt ist. Ergänzungen oder Updates, die Einfluss auf Mitgliedschaft sind danach nicht Teil des Resultsets, bis er erneut geöffnet wird.  
  
 Änderungen an Datenwerten (vorgenommen hat, entweder durch den Besitzer des Keyset oder andere Prozesse) sind sichtbar, wenn der Benutzer über das Resultset einen Bildlauf durchführt. Außerhalb des Cursors (durch andere Prozesse) vorgenommene einfügungen sind sichtbar, nur dann, wenn der Cursor geschlossen und erneut geöffnet wird. Einfügungen, die von innerhalb der Cursor werden am Ende des Resultsets angezeigt.  
  
 Wenn ein keysetgesteuerter Cursor versucht, eine Zeile abzurufen, die gelöscht wurde, wird die Zeile als einer "Lücke" im Resultset angezeigt. Der Schlüssel für die Zeile vorhanden ist, im Keyset, aber die Zeile im Resultset nicht mehr vorhanden ist. Wenn die Schlüsselwerte in einer Zeile aktualisiert werden, gilt die Zeile als gelöscht wurden und dann eingefügt werden, damit solche Zeilen auch als Lücken im Resultset angezeigt werden. Während ein keysetgesteuerten Cursors immer durch andere Prozesse gelöschte Zeilen erkennen kann, können sie optional die Schlüssel für die Zeilen entfernen, die er selbst löscht. Keysetgesteuerte Cursor, die dazu ihre eigenen Löschvorgänge nicht erkannt werden, da die Beweise entfernt wurde.  
  
 Ein Update für eine Schlüsselspalte funktioniert wie dem Löschen der den alten Schlüssel und einer Einfügung des neuen Schlüssels. Der neue Schlüsselwert ist nicht sichtbar, wenn das Update nicht über den Cursor erfolgte. Wenn das Update über den Cursor erstellt wurde, ist der neue Schlüssel-Wert am Ende des Resultsets sichtbar.  
  
 Es ist eine Abwandlung keysetgesteuerte Cursor keysetgesteuerte standard Cursor aufgerufen. In einem keysetgesteuerten standard Cursor die Mitgliedschaft der Zeilen im Resultset und die Reihenfolge der Zeilen auf Cursor Öffnungszeit, aber Änderungen an Werten, die vom cursorbesitzer vorgenommen werden und per Commit ausgeführte Änderungen, die von anderen Prozessen sichtbar sind. Wenn eine Änderung eine Zeile für die Mitgliedschaft ausschließt oder wirkt sich auf die Reihenfolge einer Zeile, die Zeile nicht entfernt oder verschoben werden, wenn der Cursor geschlossen und erneut geöffnet wird. Eingefügte Daten werden nicht angezeigt, aber Änderungen an vorhandenen Daten werden immer dann angezeigt, da die Zeilen abgerufen werden.  
  
 Der keysetgesteuerte Cursor ist schwierig, da die Sensitivität gegenüber datenänderungen, vielen unterschiedlichen Situationen abhängt ordnungsgemäß zu verwenden, wie oben beschrieben. Wenn Ihre Anwendung nicht das gleichzeitige Updates betrifft, programmgesteuerte der ungültigen Schlüssel Behandlung kann und muss bestimmte schlüsselgebundenen Zeilen direkt zugreifen, funktioniert jedoch möglicherweise der keysetgesteuerte Cursor für Sie. Verwenden Sie die **AdOpenKeyset CursorTypeEnum** um anzugeben, dass Sie einen Keyset-Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
