---
title: Verwaltungsprogramm | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8a2a8363371d6f6c3644c2b7b49aa77644d496e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306641"
---
# <a name="administration-program"></a>Verwaltungsprogramm
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 Ein Verwaltungsprogramm, der ODBC-Administrator, ist im Windows SDK/MDAC SDK enthalten. Dieses Programm kann von Benutzern des SDK neu verteilt werden. Darüber hinaus können Entwickler ihre eigenen Verwaltungsprogramme schreiben. Im Allgemeinen schreiben Entwickler ihre eigenen Verwaltungsprogramme nur, wenn sie die vollständige Kontrolle über die Datenquellenkonfiguration behalten möchten oder wenn sie Datenquellen direkt aus einer Anwendung konfigurieren, die als Verwaltungsprogramm fungiert. Ein Tabellenkalkulationsprogramm kann es Benutzern beispielsweise ermöglichen, Datenquellen zur Laufzeit hinzuzufügen und dann zu verwenden.  
  
 Das Administrationsprogramm lädt zuerst die Installations-DLL. Anschließend werden Funktionen in der Installations-DLL auf, um die folgenden Aufgaben auszuführen:  
  
-   **Hinzufügen, Ändern oder Löschen von Datenquellen interaktiv.** Das Administrationsprogramm kann **SQLManageDataSources**, **SQLCreateDataSource**oder **SQLConfigDataSource**aufrufen.  
  
     **SQLManageDataSources** zeigt ein Dialogfeld an, mit dem der Benutzer Datenquellen hinzufügen, ändern oder löschen und Ablaufverfolgungsoptionen angeben kann. Diese Funktion wird aufgerufen, wenn die Installations-DLL direkt aus der Systemsteuerung aufgerufen wird. **SQLCreateDataSource** zeigt ein Dialogfeld an, mit dem der Benutzer nur Datenquellen hinzufügen kann. **SQLConfigDataSource** übergibt den Aufruf direkt an die Treiber-Setup-DLL.  
  
     In allen Fällen ruft die Installations-DLL **ConfigDSN** in der Treibereinrichtungs-DLL auf, um die Datenquelle tatsächlich hinzuzufügen, zu ändern oder zu löschen. Die Treibereinrichtungs-DLL fordert den Benutzer möglicherweise zur Eingabe zusätzlicher Informationen auf.  
  
-   **Hinzufügen, Ändern oder Löschen von Datenquellen im Hintergrund.** Das Administrationsprogramm ruft **SQLConfigDataSource** in der Installations-DLL auf und übergibt ihm ein NULL-Fensterhandle, den Namen einer Datenquelle zum Hinzufügen, Ändern oder Löschen und eine Liste von Werten für die Registrierung. Die Installations-DLL ruft **ConfigDSN** in der Treibereinrichtungs-DLL auf, um die Datenquelle tatsächlich hinzuzufügen, zu ändern oder zu löschen.  
  
-   **Hinzufügen, Ändern oder Löschen einer Standarddatenquelle.** Die Standarddatenquelle ist die gleiche wie jede andere Datenquelle, mit der Ausnahme, dass ihr Name Standard ist. Sie wird auf die gleiche Weise wie jede andere Datenquelle hinzugefügt, geändert oder gelöscht.
