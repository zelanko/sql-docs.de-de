---
description: Installationskomponenten
title: Installationskomponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aac17b66b52b6d5b167f670302b8e1df14f8907a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499823"
---
# <a name="installation-components"></a>Installationskomponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Der Installationsvorgang wird gestartet, wenn der Benutzer das Setup Programm ausführt. Das Setup Programm wird zusammen mit der Installationsprogramm- *dll* und einer *Treiber-Setup-DLL* für jeden Treiber verwendet. Sowohl das Setup Programm als auch die Installer-DLL verwenden die Argumente in den **sqlinstalldriverex** -und **sqlinstalltranslatorex** -Funktionen, um zu bestimmen, welche Dateien für jede Komponente kopiert oder gelöscht werden sollen. Die folgende Abbildung zeigt die Beziehung zwischen diesen Installationskomponenten.  
  
 ![Beziehung zwischen Installationskomponenten](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Die ODBC. inf-Datei, die in ODBC *2. x* verwendet wurde, um die Dateien zu beschreiben, die für die einzelnen ODBC-Komponenten erforderlich sind, wird in ODBC *3. x*nicht verwendet. Treiber, die ODBC *3. x* -Komponenten liefern, müssen keine ODBC. inf-Datei erstellen. Beim Entfernen von **SQLInstallDriver** und **SQLInstallODBC**und der veralteten **sqlinstalltranslator**-Funktion wurde ODBC. inf nicht benötigt. Die Treiber Informationen, die in den Treiber Schlüsselwort Abschnitten von ODBC. inf verwendet wurden, werden jetzt im *lpszDriver* -Argument in **sqlinstalldriverex**bereitgestellt. Die Konvertierungs Informationen, die in den Abschnitten [ODBC Translator] und Übersetzer Spezifikation von ODBC. inf verwendet wurden, werden jetzt im *lpsztranslator* -Argument von **sqlinstalltranslatorex**bereitgestellt. Durch diese Änderungen kann das ODBC-Installationsprogramm plattformübergreifend besser portierbar sein.  
  
 Weitere Informationen zu diesen Komponenten finden Sie in den folgenden Themen am Ende dieses Abschnitts.  
  
-   [Setupprogramm](../../../odbc/reference/install/setup-program.md)  
  
-   [Installationsprogramm-DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [Setup-DLL für Treiber](../../../odbc/reference/install/driver-setup-dll.md)
