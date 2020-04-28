---
title: Installieren von ODBC-Komponenten | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298980"
---
# <a name="installing-odbc-components"></a>Installieren von ODBC-Komponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 In diesem Abschnitt wird beschrieben, wie ODBC-Komponenten installiert und entfernt werden. Da Treiber Entwickler immer eine ODBC-Komponente (ihren Treiber) installieren, müssen Sie diesen Abschnitt lesen. Anwendungsentwickler müssen diesen Abschnitt nur lesen, wenn Sie ODBC-Komponenten mit Ihren Anwendungen bereitgestellt werden. Zu den ODBC-Komponenten gehören der Treiber-Manager, Treiber, Konvertierer, die Installationsprogramm-dll, die Cursor Bibliothek und zugehörige Dateien. In diesem Abschnitt werden ODBC-Anwendungen nicht als ODBC-Komponenten betrachtet.  
  
> [!NOTE]  
>  Dieser Abschnitt ist spezifisch für Microsoft Windows-Plattformen. Die Installation von ODBC-Komponenten auf anderen Plattformen ist plattformspezifisch.  
  
 ODBC-Komponenten werden Komponenten Weise installiert und entfernt, nicht Datei-für-Datei-Basis. Wenn ein Übersetzer z. b. aus dem Konvertierer selbst und einer Reihe von Datendateien besteht, werden diese Dateien als Gruppe installiert und entfernt. Sie dürfen nicht Datei Weise installiert und entfernt werden. Der Grund hierfür ist, sicherzustellen, dass nur komplette Komponenten auf dem System vorhanden sind.  
  
 Zum Installieren und Entfernen von-Komponenten werden die folgenden als ODBC-Komponenten definiert:  
  
-   **Kernkomponenten.** Der Treiber-Manager, die Cursor Bibliothek, die Installationsprogramm-dll und alle anderen verwandten Dateien bilden die Kernkomponenten und müssen als Gruppe installiert und entfernt werden.  
  
-   **Zieher.** Jeder Treiber ist eine separate Komponente.  
  
-   **Dolmetscher.** Jeder Translator ist eine separate Komponente.  
  
 Mit der Unterstützung von Unicode in ODBC 3,5 und höher muss bei der Verwendung OLE DB Komponenten mit ODBC ein gewisser Aspekt berücksichtigt werden. Die Version 1,1 des OLE DB Anbieters für ODBC wurde in bestimmte Unicode-Spezifikationen innerhalb von ODBC 3,0 geschrieben. Da diese Spezifikationen in ODBC 3,5 geändert wurden, ist es erforderlich, die Version 1,5 oder höher des Anbieters zu verwenden, wenn Sie ODBC 3,5 und höher verwenden. In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Installationskomponenten](../../../odbc/reference/install/installation-components.md)  
  
-   [Zählen der Verwendung](../../../odbc/reference/install/usage-counting.md)
