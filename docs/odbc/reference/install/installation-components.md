---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a883377a17aa9e0c3426b4805263616375ea6215
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198386"
---
# <a name="installation-components"></a>Installationskomponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Der Installationsprozess wird gestartet, wenn der Benutzer das Setupprogramm ausführt. Das Setup-Programm funktioniert in Verbindung mit der *Installationsprogramm-DLL* und *Setup-DLL für Treiber* für jeden Treiber. Sowohl das Setup-Programm und das Installationsprogramm-DLL verwenden Sie die Argumente in der **SQLInstallDriverEx** und **SQLInstallTranslatorEx** Funktionen, um zu bestimmen, welche Dateien kopiert oder gelöscht werden, für die einzelnen Komponenten. Die folgende Abbildung zeigt die Beziehung zwischen diesen Installationskomponenten.  
  
 ![Beziehung zwischen Installationskomponenten](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Die Odbc.inf-Datei, die in ODBC 2. verwendet wurde. *x* zur Beschreibung der einzelnen ODBC erforderlichen Dateien Komponente nicht in ODBC 3. verwendet *.x*. Treiber, die ODBC 3. enthalten *.x* Komponenten müssen sich nicht um eine Odbc.inf-Datei zu erstellen. Das Entfernen der **SQLInstallDriver** und **SQLInstallODBC**, und die **SQLInstallTranslator**, Odbc.inf unnötig gerendert haben. Der Treiberinformationen, mit der in den Abschnitten Driver-Schlüsselwort Odbc.inf werden, jetzt finden Sie in der *LpszDriver* -Argument in **SQLInstallDriverEx**. Die Translator-Informationen, die in der [ODBC-Übersetzer] verwendet, und Abschnitte Odbc.inf Translator-Spezifikation wird nun bereitgestellt, der *LpszTranslator* Argument **SQLInstallTranslatorEx**. Diese Änderungen ermöglichen des ODBC-Installationsprogramms auf Plattformen besser portierbar sein.  
  
 Weitere Informationen zu diesen Komponenten finden Sie unter den folgenden Themen am Ende dieses Abschnitts.  
  
-   [Setupprogramm](../../../odbc/reference/install/setup-program.md)  
  
-   [Installationsprogramm-DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [Setup-DLL für Treiber](../../../odbc/reference/install/driver-setup-dll.md)
