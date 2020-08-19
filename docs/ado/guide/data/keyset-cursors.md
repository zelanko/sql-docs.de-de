---
description: KEYSET-Cursor
title: Keysetcursor | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ea25d5c85969b71836fec30085dd9a626a18d40a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453172"
---
# <a name="keyset-cursors"></a>KEYSET-Cursor
Der Keysetcursor bietet Funktionen zwischen einem statischen und einem dynamischen Cursor, um Änderungen zu erkennen. Wie ein statischer Cursor ermittelt er nicht immer Änderungen an der Mitgliedschaft und Reihenfolge des Resultsets. Wie ein dynamischer Cursor ermittelt er Änderungen an den Werten der Zeilen im Resultset.  
  
 Keysetgesteuerte Cursor werden von einer Reihe von eindeutigen Bezeichnern (Schlüssel) gesteuert, die als das Keyset bezeichnet werden. Die Schlüssel werden anhand einer Reihe von Spalten erstellt, die die Zeilen im Resultset eindeutig identifizieren. Das Keyset besteht aus Schlüsselwerten aus allen Zeilen, die von der Abfrageanweisung zurückgegeben werden.  
  
 Mit einem keysetgesteuerten Cursor wird für jede Zeile im Cursor ein Schlüssel erstellt und gespeichert, der wiederum entweder auf der Clientarbeitsstation oder dem Server gespeichert wird. Wenn Sie auf eine beliebige Zeile zugreifen, wird der gespeicherte Schlüssel zum Abrufen der aktuellen Datenwerte aus der Datenquelle verwendet. In einem keysetgesteuerter Cursor wird die Mitgliedschaft des Resultsets fixiert, wenn das Keyset vollständig gefüllt wurde. Daher sind Ergänzungen und Updates, die die Mitgliedschaft betreffen, nicht Teil des Resultsets, bis dieses neu geöffnet wird.  
  
 Änderungen an Datenwerten (entweder durch den keysetbesitzer oder andere Prozesse) werden angezeigt, wenn der Benutzer einen Bildlauf durch das Resultset durchführt. INSERTs außerhalb des Cursors (durch andere Prozesse) sind nur sichtbar, wenn der Cursor beendet und neu gestartet wird. INSERTs innerhalb des Cursors werden am Ende des Resultsets angezeigt.  
  
 Wenn ein keysetgesteuerte Cursor versucht, eine gelöschte Zeile abzurufen, wird die Zeile als "Loch" im Resultset angezeigt. Der Schlüssel für die Zeile ist im Keyset enthalten, aber die Zeile ist nicht mehr im Resultset vorhanden. Wenn die Schlüsselwerte in einer Zeile aktualisiert werden, wird die Zeile als gelöscht und dann eingefügt, sodass diese Zeilen auch als Löcher im Resultset angezeigt werden. Während ein keysetgesteuertes Cursor immer Zeilen erkennen kann, die von anderen Prozessen gelöscht wurden, kann er optional die Schlüssel für die Zeilen entfernen, die er löscht. Durch keysetgesteuerte Cursor können keine eigenen Löschvorgänge erkannt werden, da der Beweis entfernt wurde.  
  
 Ein Update für eine Schlüssel Spalte verhält sich wie eine Löschung des alten Schlüssels, gefolgt von einer Einfügung des neuen Schlüssels. Der neue Schlüsselwert ist nicht sichtbar, wenn das Update nicht über den Cursor durchgeführt wurde. Wenn das Update über den Cursor durchgeführt wurde, wird der neue Schlüsselwert am Ende des Resultsets angezeigt.  
  
 Es gibt eine Variation von keysetgesteuerten Cursorn, die als keysetgesteuerte Standard Cursor bezeichnet werden. In einem keysetgesteuerten Standard Cursor werden die Mitgliedschaften von Zeilen im Resultset und die Reihenfolge der Zeilen beim Öffnen des Cursors festgelegt. Änderungen an den Werten, die vom Cursor Besitzer vorgenommen werden, und von Änderungen, die von anderen Prozessen vorgenommen wurden, sind jedoch sichtbar. Wenn eine Änderung eine Zeile für die Mitgliedschaft disqualifiziert oder die Reihenfolge einer Zeile beeinflusst, wird die Zeile nicht ausgeblendet oder verschoben, es sei denn, der Cursor wird geschlossen und erneut geöffnet. Eingefügte Daten werden nicht angezeigt, aber Änderungen an vorhandenen Daten werden beim Abrufen der Zeilen angezeigt.  
  
 Der keysetgesteuerte Cursor ist schwierig zu verwenden, da die Vertraulichkeit von Datenänderungen von vielen unterschiedlichen Bedingungen abhängig ist, wie oben beschrieben. Wenn sich Ihre Anwendung jedoch nicht um gleichzeitige Updates handelt, kann ungültige Schlüsselprogramm gesteuert verarbeiten und direkt auf bestimmte Schlüssel gebundene Zeilen zugreifen, kann der keysetgesteuerte Cursor möglicherweise für Sie funktionieren. Verwenden Sie das " **adOpenKeyset" CursorTypeEnum** , um anzugeben, dass Sie einen Keyset-Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorwärts Cursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
