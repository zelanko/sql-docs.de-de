---
title: Installieren von ODBC-Komponenten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd0a6aeba8073ce14b08b8635396b1f231895fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298980"
---
# <a name="installing-odbc-components"></a>Installieren von ODBC-Komponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 In diesem Abschnitt wird beschrieben, wie ODBC-Komponenten installiert und entfernt werden. Da Treiberentwickler immer eine ODBC-Komponente (ihren Treiber) installieren, müssen sie diesen Abschnitt lesen. Anwendungsentwickler müssen diesen Abschnitt nur lesen, wenn sie ODBC-Komponenten mit ihren Anwendungen versenden. Zu den ODBC-Komponenten gehören der Treiber-Manager, Treiber, Übersetzer, die Installations-DLL, die Cursorbibliothek und alle zugehörigen Dateien. Für die Zwecke dieses Abschnitts werden ODBC-Anwendungen nicht als ODBC-Komponenten betrachtet.  
  
> [!NOTE]  
>  Dieser Abschnitt ist spezifisch für Microsoft Windows-Plattformen. Wie ODBC-Komponenten auf anderen Plattformen installiert werden, ist plattformspezifisch.  
  
 ODBC-Komponenten werden komponentenweise und nicht dateiweise installiert und entfernt. Wenn z. B. ein Übersetzer aus dem Übersetzer selbst und einer Reihe von Datendateien besteht, werden diese Dateien als Gruppe installiert und entfernt. Sie dürfen nicht dateiweise installiert und entfernt werden. Der Grund dafür ist, sicherzustellen, dass nur vollständige Komponenten auf dem System vorhanden sind.  
  
 Für die Installation und das Entfernen von Komponenten sind die folgenden ALS ODBC-Komponenten definiert:  
  
-   **Kernkomponenten.** Der Treiber-Manager, die Cursorbibliothek, die Installations-DLL und alle anderen zugehörigen Dateien bilden die Kernkomponenten und müssen als Gruppe installiert und entfernt werden.  
  
-   **Treiber.** Jeder Treiber ist eine separate Komponente.  
  
-   **Übersetzer.** Jeder Übersetzer ist eine separate Komponente.  
  
 Mit der Unterstützung von Unicode in ODBC 3.5 und höher muss die Verwendung von OLE DB-Komponenten mit ODBC berücksichtigt werden. Die Version 1.1 des OLE DB Provider für ODBC wurde in ODBC 3.0 auf bestimmte Unicode-Spezifikationen geschrieben. Da sich diese Spezifikationen in ODBC 3.5 geändert haben, ist es notwendig, Version 1.5 oder höher des Anbieters zu haben, wenn ODBC 3.5 und höher verwendet wird. In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Installationskomponenten](../../../odbc/reference/install/installation-components.md)  
  
-   [Zählen der Verwendung](../../../odbc/reference/install/usage-counting.md)
