---
title: Installationskomponenten | Microsoft Docs
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
ms.openlocfilehash: 0a196e9b935229fa03c6dd0eda92b8e99e69f0ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285250"
---
# <a name="installation-components"></a>Installationskomponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 Der Installationsvorgang wird gestartet, wenn der Benutzer das Setupprogramm ausführt. Das Setupprogramm arbeitet in Verbindung mit der *Installations-DLL* und einer *Treiber-Setup-DLL* für jeden Treiber. Sowohl das Setupprogramm als auch die Installations-DLL verwenden die Argumente in den Funktionen **SQLInstallDriverEx** und **SQLInstallTranslatorEx,** um zu bestimmen, welche Dateien für jede Komponente kopiert oder gelöscht werden sollen. Die folgende Abbildung zeigt die Beziehung zwischen diesen Installationskomponenten.  
  
 ![Beziehung zwischen Installationskomponenten](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Die Odbc.inf-Datei, die in ODBC *2.x* verwendet wurde, um die von jeder ODBC-Komponente benötigten Dateien zu beschreiben, wird in ODBC *3.x*nicht verwendet. Treiber, die ODBC *3.x-Komponenten* versenden, müssen keine Odbc.inf-Datei erstellen. Das Entfernen von **SQLInstallDriver** und **SQLInstallODBC**und die Veraltung von **SQLInstallTranslator**haben Odbc.inf überflüssig gemacht. Die Treiberinformationen, die sich früher in den Abschnitten "Treiberschlüsselwort" von Odbc.inf befänden, werden jetzt im *Argument lpszDriver* in **SQLInstallDriverEx**bereitgestellt. Die Übersetzerinformationen, die sich früher in den Abschnitten [ODBC Translator] und Translator Specification von Odbc.inf befänden, finden Sie jetzt im *argument lpszTranslator* von **SQLInstallTranslatorEx**. Diese Änderungen ermöglichen es dem ODBC Installer, plattformübergreifend tragbarer zu sein.  
  
 Weitere Informationen zu diesen Komponenten finden Sie in den folgenden Themen am Ende dieses Abschnitts.  
  
-   [Setupprogramm](../../../odbc/reference/install/setup-program.md)  
  
-   [Installationsprogramm-DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [Setup-DLL für Treiber](../../../odbc/reference/install/driver-setup-dll.md)
