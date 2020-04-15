---
title: Setup-Programm | Microsoft Docs
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b89cae70db65bd2aa54b8e9789a5c2b35696923e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296150"
---
# <a name="setup-program"></a>Setupprogramm
> **HINWEIS:** Ab Windows XP und Windows Server 2003 **ist ODBC im Windows-Betriebssystem enthalten.** Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 Der Benutzer führt das Setupprogramm aus, um den Setup-Vorgang zu starten. Das Setup-Programm wird vom Anwendungs- oder Treiberentwickler geschrieben. Neben der Installation von ODBC-Komponenten kann es auch andere Software installieren. Anwendungsentwickler können z. B. dasselbe Setupprogramm verwenden, um ODBC-Komponenten zu installieren und ihre Anwendungen zu installieren.  
  
 Entwickler können das Setupprogramm von Grund auf neu schreiben, indem sie die Einrichtungsprogramme Microsoft® Windows® SDK oder Setupsoftware anderer Anbieter verwenden. Dies gibt diesen Entwicklern die vollständige Kontrolle über das Aussehen und das Gefühl des Setup-Programms. Das Setup-Programm kann geschrieben werden, um zusätzliche Software zu installieren, z. B. eine ODBC-Anwendung. Weitere Informationen zu den Windows SDK-Setupprogrammen finden Sie in der Windows SDK-Dokumentation.  
  
 Wie viel der Installation tatsächlich vom Setup-Programm durchgeführt wird, hängt davon ab, welche Funktionen es in der Installations-DLL aufruft. Die Installations-DLL enthält Funktionen zum Installieren einzelner ODBC-Komponenten. Das Setupprogramm ruft einfach **SQLInstallDriverManager**, **SQLInstallDriverEx**oder **SQLInstallTranslatorEx** in der Installations-DLL auf, um den Pfad des Verzeichnisses abzurufen, in dem die Komponente installiert werden soll, und um Informationen über die Komponente zur Registrierung hinzuzufügen. Diese Funktionen kopieren keine Dateien. Das Setup-Programm tut dies mit den Informationen in den Argumenten dieser Funktionen.  
  
 Die Installations-DLL enthält auch Funktionen zum Entfernen von ODBC-Komponenten. Das Setupprogramm ruft **SQLRemoveDriver ,** **SQLRemoveDriver**oder **SQLRemoveTranslator** in der Installations-DLL auf, um die Verwendungsanzahl einer Komponente in der Registrierung zu reduzieren und, wenn die neue Verwendungsanzahl der Komponente auf 0 fällt, alle Informationen über die Komponente aus der Registrierung zu entfernen. Diese Funktionen entfernen die Dateien für die Komponente nicht. Das Setupprogramm tut dies, wenn die neue Nutzungsanzahl auf 0 fällt.
