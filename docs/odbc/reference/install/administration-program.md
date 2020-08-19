---
description: Verwaltungsprogramm
title: Verwaltungs Programm | Microsoft-Dokumentation
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
ms.openlocfilehash: 5aef5e00fa69fd1f699228b2c0ac82b2a8041962
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429032"
---
# <a name="administration-program"></a>Verwaltungsprogramm
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Ein Verwaltungs Programm, der ODBC-Administrator, ist im Windows SDK/MDAC SDK enthalten. Dieses Programm kann von Benutzern des SDK neu verteilt werden. Außerdem können Entwickler ihre eigenen Verwaltungsprogramme schreiben. Im allgemeinen schreiben Entwickler ihre eigenen Verwaltungsprogramme nur dann, wenn Sie die komplette Kontrolle über die Datenquellen Konfiguration behalten möchten, oder wenn Sie Datenquellen direkt von einer Anwendung konfigurieren, die als Verwaltungs Programm fungiert. Beispielsweise kann es vorkommen, dass Benutzer mit einem Tabellen Programm zur Laufzeit Datenquellen hinzufügen und anschließend verwenden können.  
  
 Das Verwaltungs Programm lädt zuerst die Installationsprogramm-dll. Anschließend werden Funktionen in der Installationsprogramm-dll aufgerufen, um die folgenden Aufgaben auszuführen:  
  
-   **Sie können Datenquellen interaktiv hinzufügen, ändern oder löschen.** Das Verwaltungs Programm kann **sqlmanagedatasources**, **sqlkreatedatasource**oder **SQLConfigDataSource**aufrufen.  
  
     **Sqlmanagedatasources** zeigt ein Dialogfeld an, mit dem der Benutzerdaten Quellen hinzufügen, ändern oder löschen und Ablauf Verfolgungs Optionen angeben kann. Diese Funktion wird aufgerufen, wenn die Installationsprogramm-dll direkt in der Systemsteuerung aufgerufen wird. **Sqlkreatedatasource** zeigt ein Dialogfeld an, mit dem der Benutzer nur Datenquellen hinzufügen kann. **SQLConfigDataSource** übergibt den-Befehl direkt an die Treiber-Setup-DLL.  
  
     In allen Fällen ruft die Installer-DLL **ConfigDSN** in der Treiber-Setup-DLL auf, um die Datenquelle tatsächlich hinzuzufügen, zu ändern oder zu löschen. Die Treiber-Setup-DLL könnte den Benutzer zur Eingabe zusätzlicher Informationen auffordern.  
  
-   **Datenquellen können im Hintergrund hinzugefügt, geändert oder gelöscht werden.** Das Verwaltungs Programm ruft **SQLConfigDataSource** in der Installer-dll auf und übergibt ihm ein null-Fenster Handle, den Namen einer Datenquelle, die hinzugefügt, geändert oder gelöscht werden soll, und eine Liste mit Werten für die Registrierung. Die Installationsprogramm-dll ruft **ConfigDSN** in der Treiber-Setup-DLL auf, um die Datenquelle tatsächlich hinzuzufügen, zu ändern oder zu löschen.  
  
-   **Hiermit wird eine Standarddaten Quelle hinzugefügt, geändert oder gelöscht.** Die Standarddaten Quelle ist mit jeder anderen Datenquelle identisch, mit dem Unterschied, dass der Name default lautet. Es wird auf die gleiche Weise wie jede andere Datenquelle hinzugefügt, geändert oder gelöscht.
