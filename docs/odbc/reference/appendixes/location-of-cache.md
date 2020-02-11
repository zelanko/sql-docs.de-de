---
title: Speicherort des Caches | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a925b66b0d09a9beb32e4441d62bc4fa9296313
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990737"
---
# <a name="location-of-cache"></a>Speicherort des Caches
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Die Cursor Bibliothek speichert Daten im Arbeitsspeicher und in Windows® temporären Dateien. Dadurch wird die Größe des Resultsets beschränkt, das von der Cursor Bibliothek nur durch den verfügbaren Speicherplatz behandelt werden kann. Eine temporäre Datei wird verwendet, wenn die Daten, die zwischengespeichert werden sollen, die Segment Grenze überschreiten würden, wenn Sie am Ende des Cursor-Bibliotheks Caches eingefügt werden. Stattdessen werden die zwischengespeicherten Daten anstelle des zuletzt gespeicherten Datenblocks im Cache hinzugefügt. Der zuletzt gespeicherte Datenblock wird in einer temporären Datei gespeichert. Wenn die Cursor Bibliothek nicht ordnungsgemäß beendet wird, z. b. wenn der Strom ausfällt, können temporäre Windows-Dateien auf dem Datenträger belassen werden. Diese werden mit dem Namen ~ CTT*nnnn*. tmp benannt und im aktuellen Verzeichnis erstellt.  
  
> [!NOTE]  
>  Wenn die Cursor Bibliothek in Microsoft® WindowsNT®/Windows2000 versucht, Daten in einer temporären Datei im aktuellen Verzeichnis zwischenzuspeichern, während die Anwendung von einer schreibgeschützten Freigabe oder einem Compact Disk (z. b. einem Microsoft Foundation Class-Bibliothek Beispiel) ausgeführt wird, wird SQLSTATE HY000 (allgemeiner Fehler: kein Erstellen eines Datei Puffers) zurückgegeben.
