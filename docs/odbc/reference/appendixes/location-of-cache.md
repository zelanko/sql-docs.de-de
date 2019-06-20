---
title: Speicherort des Cachespeichers | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 4b1ffd8c56a6727a892cb518222c961bbb6c794c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181345"
---
# <a name="location-of-cache"></a>Speicherort des Caches
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die Cursorbibliothek speichert Daten im Arbeitsspeicher und in Windows® temporären Dateien. Dies schränkt die Größe des Resultsets, die die Cursorbibliothek nur nach verfügbarem Speicherplatz verarbeiten kann. Eine temporäre Datei wird verwendet, wenn die Daten zwischengespeichert werden die Segment-Grenze der anwendungsbinärschnittstelle würde, wenn am Ende der Cursorbibliothek-Cache eingefügt. Stattdessen werden die Daten zwischengespeichert werden anstelle der zuletzt gespeicherten Block von Daten im Cache hinzugefügt. Die zuletzt gespeicherten Block von Daten wird in einer temporären Datei gespeichert. Wenn die Cursorbibliothek fehlerbedingt beendet wird, z. B. wenn der Strom ausfällt, können sie Windows temporäre Dateien auf dem Datenträger lassen. Wird dies als ~ CTT*Nnnn*TMP und sind in das aktuelle Verzeichnis erstellt.  
  
> [!NOTE]  
>  Wenn die Cursorbibliothek in Microsoft® WindowsNT®/Windows 2000 zum Zwischenspeichern von Daten in einer temporären Datei im aktuellen Verzeichnis versucht, während der Ausführung der Anwendung aus einer schreibgeschützten Freigabe oder einem Compact Disk-(z. B. ein Microsoft Foundation Class Library-Beispiel), SQLSTATE HY000 (Allgemeine Error-Unable, erstellen Sie einen Dateipuffer) wird zurückgegeben.
