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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5f033ac12569c7de61af071930d6c8d58d8b611
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198231"
---
# <a name="installing-odbc-components"></a>Installieren von ODBC-Komponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 In diesem Abschnitt wird beschrieben, wie die ODBC-Komponenten installiert und entfernt werden. Da Treiberentwickler immer eine ODBC-Komponente (ihre Treiber) installieren, müssen sie diesen Abschnitt zu lesen. Entwickler müssen diesen Abschnitt zu lesen, nur dann, wenn sie ODBC-Komponenten mit ihren Anwendungen ausgeliefert werden. ODBC-Komponenten enthalten, der Treiber-Manager, Treiber, Konvertierer, das Installationsprogramm-DLL, die Cursorbibliothek und alle zugehörigen Dateien. Für die Zwecke dieses Artikels werden die ODBC-Anwendungen, die ODBC-Komponenten werden nicht berücksichtigt.  
  
> [!NOTE]  
>  Dieser Abschnitt bezieht sich auf Microsoft Windows-Plattformen. Wie die ODBC-Komponenten auf anderen Plattformen installiert werden, ist plattformspezifisch.  
  
 ODBC-Komponenten sind installiert und entfernt auf Basis von Komponente, nicht in einer Datei-für-Datei-Basis. Z. B. wenn Übersetzer des Übersetzers selbst und eine Anzahl von Datendateien besteht, diese Dateien sind installiert und als Gruppe entfernt; Sie müssen nicht installiert und pro Datei-für-Datei entfernt. Der Grund dafür ist, um sicherzustellen, dass Komponenten nur auf dem System vorhanden sind.  
  
 Rahmen installieren und Entfernen von Komponenten werden ODBC-Komponenten die folgenden so definiert:  
  
-   **Core-Komponenten.** Der Treiber-Manager, Cursor-Bibliothek, Installationsprogramm-DLL und alle anderen bezogene Dateien bilden die wichtigsten Komponenten und installiert und als Gruppe entfernt werden müssen.  
  
-   **Treiber.** Jeder Treiber ist eine separate Komponente.  
  
-   **Übersetzer.** Jede Translator ist eine separate Komponente.  
  
 Mit der Unterstützung von Unicode in ODBC 3.5 und höher muss einige Überlegungen zur Verwendung von OLE DB-Komponenten mithilfe von ODBC zugewiesen werden. Version 1.1 des OLE DB-Anbieter für ODBC wurde bestimmte Unicode-Spezifikationen in ODBC 3.0 geschrieben. Da diese Spezifikationen in ODBC 3.5 geändert wurde, ist es notwendig, Version 1.5 oder höher des Anbieters zu haben, bei Verwendung von ODBC 3.5 und höher. Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Installationskomponenten](../../../odbc/reference/install/installation-components.md)  
  
-   [Zählen der Verwendung](../../../odbc/reference/install/usage-counting.md)
