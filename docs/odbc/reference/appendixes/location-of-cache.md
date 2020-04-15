---
title: Speicherort des Cache | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 13510332ae8bfab07a13d7831f9f74a048551214
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288618"
---
# <a name="location-of-cache"></a>Speicherort des Caches
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Die Cursorbibliothek speichert Daten im Arbeitsspeicher und in Windows® temporären Dateien zwischen. Dadurch wird die Größe des Resultsets begrenzt, das die Cursorbibliothek nur über den verfügbaren Speicherplatz verarbeiten kann. Eine temporäre Datei wird verwendet, wenn die zwischenzuspeichernden Daten die Segmentgrenze überschreiten würden, wenn sie am Ende des Cursorbibliothekcache eingefügt werden. Stattdessen werden die zwischenzuspeichernden Daten anstelle des zuletzt gespeicherten Datenblocks im Cache hinzugefügt. Der zuletzt gespeicherte Datenblock wird in einer temporären Datei gespeichert. Wenn die Cursorbibliothek ungewöhnlich beendet wird, z. B. wenn die Stromversorgung ausfällt, kann windows temporäre Dateien auf dem Datenträger belassen. Diese heißen den Namen "CTT*nnnn*.tmp" und werden im aktuellen Verzeichnis erstellt.  
  
> [!NOTE]  
>  Wenn die Cursorbibliothek in Microsoft® WindowsNT®/Windows2000 versucht, Daten in einer temporären Datei im aktuellen Verzeichnis zwischenzuspeichern, während die Anwendung von einer schreibgeschützten Freigabe oder einer Cd -Festplatte (z. B. einem Microsoft Foundation-Klassenbibliotheksbeispiel) ausgeführt wird, wird SQLSTATE HY000 (General Error-Unable to create a file buffer) zurückgegeben.
