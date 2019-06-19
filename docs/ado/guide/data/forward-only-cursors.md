---
title: Vorwärtscursor | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 15d11b8882e8e39a03ffb7509526a4f66b6553b3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700704"
---
# <a name="forward-only-cursors"></a>Vorwärtscursor
Die typische Standardcursortyp, bezeichnet einen Cursor vorwärts-(oder nicht bildlauffähige), kann über das Resultset nur vorwärts bewegen. Ein Vorwärtscursor unterstützt nicht das Durchführen eines Bildlaufs (die Möglichkeit zum Verschieben von vorwärts und rückwärts im Resultset); Es unterstützt nur das Abrufen von Zeilen vom Anfang bis zum Ende des Resultsets. Mit einigen Vorwärtscursor (z. B. mit der SQL Server-Cursor Library), werden alle INSERT-, Update- und Delete-Anweisungen wird hergestellt, indem der aktuelle Benutzer (oder anderer Benutzer ausgeführt werden), dass die Auswirkungen von Zeilen im Resultset angezeigt werden, wie die Zeilen abgerufen werden. Da mit dem Cursor nicht zurück gescrollt werden kann, sind Änderungen, die an Zeilen in der Datenbank vorgenommen wurden, nachdem die jeweilige Zeile abgerufen wurde, über den Cursor nicht sichtbar.  
  
 Nachdem die Daten für die aktuelle Zeile verarbeitet wurde, gibt die Vorwärtscursor die Ressourcen, die verwendet wurden, zum Speichern dieser Daten frei. Vorwärtscursor sind standardmäßig dynamisch, d. h. dass alle Änderungen ermittelt werden, während die aktuelle Zeile verarbeitet wird. Damit kann der Cursor schneller gestartet werden, und Updates an den zugrunde liegenden Tabellen können im Resultset angezeigt werden.  
  
 Während Vorwärtscursor rückwärts-scrollen nicht unterstützen, kann Ihre Anwendung auf den Anfang des Resultsets durch Schließen und erneuten Öffnen des Cursors zurück. Dies ist ein effektives Verfahren zum Arbeiten mit kleinen Datenmengen. Als Alternative können kann Ihre Anwendung das Resultset auf einmal lesen, Daten lokal zwischengespeichert und navigieren Sie dann auf den lokalen Datencache.  
  
 Wenn Ihre Anwendung einen Bildlauf durch die Ergebnisse nicht erforderlich ist, ist der Vorwärtscursor die beste Möglichkeit zum Abrufen von Daten schnell mit minimalem Aufwand. Verwenden Sie die **AdOpenForwardOnly CursorTypeEnum** um anzugeben, dass Sie einen Vorwärtscursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
