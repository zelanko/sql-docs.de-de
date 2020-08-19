---
description: Setupprogramm
title: Setup Programm | Microsoft-Dokumentation
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
ms.openlocfilehash: 4cd4858214ff084a037002abd3bd34035160496b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421324"
---
# <a name="setup-program"></a>Setupprogramm
> **Hinweis:** Ab Windows XP und Windows Server 2003 **ist ODBC im Windows-Betriebssystem enthalten**. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Der Benutzer führt das Setup Programm aus, um den Setup Vorgang zu starten. Das Setup Programm wird von der Anwendung oder dem Treiber Entwickler verfasst. Neben der Installation von ODBC-Komponenten kann auch andere Software installiert werden. Anwendungsentwickler können z. b. das gleiche Setup Programm verwenden, um ODBC-Komponenten zu installieren und ihre Anwendungen zu installieren.  
  
 Entwickler können das Setup Programm mit den Microsoft® Windows® SDK-Setup Dienstprogrammen oder von anderen Anbietern von Grund auf neu schreiben. Dadurch erhalten diese Entwickler eine umfassende Kontrolle über das Erscheinungsbild des Setup Programms. Das Setup Programm kann so geschrieben werden, dass zusätzliche Software installiert wird, z. b. eine ODBC-Anwendung. Weitere Informationen zu den Windows SDK-Setup Dienstprogrammen finden Sie in der Windows SDK-Dokumentation.  
  
 Der Umfang der Installation durch das Setup Programm ist von den Funktionen abhängig, die in der Installationsprogramm-dll aufgerufen werden. Die Installationsprogramm-dll enthält Funktionen zum Installieren einzelner ODBC-Komponenten. Das Setup Programm ruft einfach **sqlinstalldrivermanager**, **sqlinstalldriverex**oder **sqlinstalltranslatorex** in der installerdll auf, um den Pfad des Verzeichnisses abzurufen, in dem die Komponente installiert werden soll, und um der Registrierung Informationen zur Komponente hinzuzufügen. Mit diesen Funktionen werden Dateien nicht tatsächlich kopiert. Das Setup Programm führt dies mithilfe der Informationen in den Argumenten dieser Funktionen aus.  
  
 Die Installationsprogramm-dll enthält auch Funktionen zum Entfernen von ODBC-Komponenten. Das Setup Programm ruft **sqlremovedrivermanager**, **sqlremovedriver**oder **sqlremovetranslator** in der Installationsprogramm-dll auf, um die Verwendungs Anzahl einer Komponente in der Registrierung zu verringern. wenn die neue Verwendungs Anzahl der Komponente auf 0 fällt, entfernen Sie alle Informationen über die Komponente aus der Registrierung. Diese Funktionen entfernen nicht tatsächlich die Dateien für die Komponente. Dies wird vom Setup Programm durchführt, wenn die neue Verwendungs Anzahl auf 0 (null) fällt.
