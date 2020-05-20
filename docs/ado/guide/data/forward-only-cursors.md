---
title: Vorwärts Cursor | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8943e97e8ce246732f0153a53f8be8d80d4fa88f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758196"
---
# <a name="forward-only-cursors"></a>Vorwärtscursor
Der typische Standardcursortyp, der als Vorwärts Cursor (oder nicht Bild lauffähigen Cursor) bezeichnet wird, kann nur durch das Resultset vorwärts verschoben werden. Ein Vorwärts Cursor unterstützt keinen Bildlauf (die Möglichkeit, vorwärts und rückwärts im Resultset zu bewegen); Es unterstützt nur das Abrufen von Zeilen vom Anfang bis zum Ende des Resultsets. Bei einigen Vorwärts Cursor (z. b. mit der SQL Server Cursor Bibliothek) werden alle INSERT-, Update-und DELETE-Anweisungen, die vom aktuellen Benutzer ausgeführt werden (oder von anderen Benutzern zugesichert wurden), die sich auf Zeilen im Resultset auswirken, beim Abrufen der Zeilen angezeigt. Da mit dem Cursor nicht zurück gescrollt werden kann, sind Änderungen, die an Zeilen in der Datenbank vorgenommen wurden, nachdem die jeweilige Zeile abgerufen wurde, über den Cursor nicht sichtbar.  
  
 Nachdem die Daten für die aktuelle Zeile verarbeitet wurden, gibt der Vorwärts Cursor die Ressourcen frei, die zum Speichern der Daten verwendet wurden. Vorwärtscursor sind standardmäßig dynamisch, d. h. dass alle Änderungen ermittelt werden, während die aktuelle Zeile verarbeitet wird. Damit kann der Cursor schneller gestartet werden, und Updates an den zugrunde liegenden Tabellen können im Resultset angezeigt werden.  
  
 Vorwärts Cursor werden von vorwärts Cursorn nicht unterstützt, indem der Cursor geschlossen und wieder geöffnet wird. Dies ist eine effektive Möglichkeit, mit kleinen Datenmengen zu arbeiten. Als Alternative könnte Ihre Anwendung das Resultset einmal lesen, die Daten lokal zwischenspeichern und dann den lokalen Daten Cache durchsuchen.  
  
 Wenn die Anwendung keinen Bildlauf durch das Resultset erfordert, ist der Vorwärts Cursor die beste Methode zum schnellen Abrufen von Daten mit dem geringsten Aufwand. Verwenden Sie die **cursortypeerum-Klasse von adOpenForwardOnly** , um anzugeben, dass Sie einen Vorwärts Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [Keysetcursor](../../../ado/guide/data/keyset-cursors.md)   
 [Dynamische Cursor](../../../ado/guide/data/dynamic-cursors.md)
