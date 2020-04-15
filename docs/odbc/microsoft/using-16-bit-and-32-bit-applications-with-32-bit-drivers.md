---
title: Verwenden von 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ce996a7c4816d4d14491e226f891904b6cf8c02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307611"
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>Verwenden von 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treibern
> [!IMPORTANT]  
>  16-Bit-Anwendungsunterstützung wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Entwickeln Sie stattdessen 32-Bit- oder 64-Bit-Anwendungen.  
  
 Mit der ODBC-Datenzugriffskomponente können Sie 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treibern verwenden. Die Betriebssysteme Microsoft® Windows® 95/98 und Microsoft Windows NT®/Windows 2000 unterstützen die folgenden Kombinationen von Anwendungen und Treibern:  
  
-   16-Bit-Anwendungen mit 32-Bit-Treibern  
  
-   32-Bit-Anwendungen mit 32-Bit-Treibern  
  
 Die Verwendung einer 32-Bit-Anwendung mit einem 16-Bit-Treiber wird nicht unterstützt.  
  
> [!NOTE]  
>  Ab der Veröffentlichung von ODBC Version 3.0 wurde Windows NT 4.0 unterstützt.  
  
 ODBC enthält die ODBC-Komponenten, die erforderlich sind, um die oben genannten Konfigurationen zu unterstützen, indem Dynamic-Link-Bibliotheken (DLLs) "thunking" werden, um 16-Bit-Adressen in 32-Bit-Adressen zu konvertieren und umgekehrt. Das Setup-Programm bestimmt, welches Betriebssystem Sie verwenden, und installiert ODBC-Komponenten, die für dieses System erforderlich sind. Sie können auch die ODBC-Komponenten installieren, die von allen Systemen verwendet werden.  
  
 In den meisten Fällen umfasst das Portieren einer Anwendung oder eines Treibers von 16 bit auf 32 Bit fünf Arten von Änderungen:  
  
-   Änderungen am Nachrichtenbehandlungscode  
  
-   Änderungen, da ganze Zahlen und Griffe 32 Bit sind  
  
-   Änderungen bei Aufrufen von Windows-Anwendungsprogrammierschnittstellen (APIs)  
  
-   Änderungen, um den Treiber threadsicher zu machen  
  
-   Änderungen an ODBC-Komponenten  
  
 Aus Sicht der Anwendungs- oder Treiberprogrammierung besteht der Hauptunterschied zwischen 16-Bit- und 32-Bit-ODBC-Komponenten darin, dass sie unterschiedliche Dateinamen haben. Vom Systemstandpunkt aus ist die Architektur jeder Anwendungs- oder Treiberverbindung unterschiedlich, und die Tools, die zum Verwalten von Datenquellen verwendet werden, sind unterschiedlich.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
