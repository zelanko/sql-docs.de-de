---
title: Verwaltungsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 740a09d9a6bceb9d3f290faa71444df0d1e7c6c7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62629562"
---
# <a name="administration-program"></a>Verwaltungsprogramm
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Ein Verwaltungsprogramm, die ODBC-Administrator ist im Windows SDK/MDAC SDK enthalten. Dieses Programm und können von Benutzern des SDK weiterverteilt werden. Darüber hinaus können Entwickler ihre eigenen Verwaltungsprogrammen schreiben. Im Allgemeinen schreiben Entwickler ihre eigenen Verwaltungsprogrammen nur, wenn sie vollständige Kontrolle über das Konfigurieren von Datenquellen beibehalten möchten oder wenn sie Datenquellen direkt von einer Anwendung konfigurieren, die als ein Verwaltungsprogramm fungiert. Ein Tabellenkalkulationsprogramm kann z. B. Benutzer hinzufügen, und klicken Sie dann die Datenquellen zur Laufzeit verwenden können.  
  
 Das Verwaltungsprogramm lädt zunächst das Installationsprogramm-DLL. Es ruft dann die Funktionen im Installationsprogramm-DLL für die folgenden Aufgaben ausführen:  
  
-   **Hinzufügen, ändern oder Löschen von Datenquellen interaktiv.** Rufen Sie das Verwaltungsprogramm kann **SQLManageDataSources**, **SQLCreateDataSource**, oder **SQLConfigDataSource**.  
  
     **SQLManageDataSources** zeigt ein Dialogfeld, mit denen der Benutzer kann hinzufügen, ändern oder Löschen von Datenquellen und Ablaufverfolgungsoptionen angeben; diese Funktion wird aufgerufen, wenn das Installationsprogramm-DLL, direkt in der Systemsteuerung aufgerufen wird. **SQLCreateDataSource** zeigt ein Dialogfeld, mit denen der Benutzer nur von Datenquellen hinzufügen kann, an. **SQLConfigDataSource** übergibt den Aufruf direkt an den Setup-DLL für Treiber.  
  
     In allen Fällen aufruft, das Installationsprogramm-DLL **ConfigDSN** in der Setup-DLL Treiber tatsächlich hinzufügen, ändern oder löschen Sie die Datenquelle. Der Setup-DLL für Treiber möglicherweise zusätzliche Informationen vom Benutzer aufgefordert werden.  
  
-   **Hinzufügen, ändern oder Löschen von Datenquellen im Hintergrund.** Die Verwaltung Programmaufrufe **SQLConfigDataSource** im Installationsprogramm-DLL und übergibt es ein null-Fenster zu behandeln, den Namen einer Datenquelle hinzufügen, ändern oder löschen und eine Liste der Werte für die Registrierung. Die Installer-DLL-Aufrufe **ConfigDSN** in der Setup-DLL Treiber tatsächlich hinzufügen, ändern oder löschen Sie die Datenquelle.  
  
-   **Hinzufügen, ändern oder Löschen einer Standard-Datenquelle.** Die Standarddatenquelle ist eine beliebige andere Datenquelle identisch, außer dass der Standardwert ist der Anzeigename. Es wird hinzugefügt, geändert oder gelöscht werden, auf dieselbe Weise wie jede andere Datenquelle.
