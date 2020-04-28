---
title: Verwenden von 16-Bit-und 32-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307611"
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>Verwenden von 16-Bit- und 32-Bit-Anwendungen mit 32-Bit-Treibern
> [!IMPORTANT]  
>  die Unterstützung von 16-Bit-Anwendungen wird in zukünftigen Versionen von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Entwickeln Sie stattdessen 32-Bit-oder 64-Bit-Anwendungen.  
  
 Mit der ODBC-Datenzugriffs Komponente können Sie 16-Bit-und 32-Bit-Anwendungen mit 32-Bit-Treibern verwenden. Die Betriebssysteme Microsoft® Windows® 95/98 und Microsoft Windows NT®/Windows 2000 unterstützen die folgenden Kombinationen von Anwendungen und Treibern:  
  
-   16-Bit-Anwendungen mit 32-Bit-Treibern  
  
-   32-Bit-Anwendungen mit 32-Bit-Treibern  
  
 Die Verwendung einer 32-Bit-Anwendung mit einem 16-Bit-Treiber wird nicht unterstützt.  
  
> [!NOTE]  
>  Ab Version 3,0 von ODBC wurde Windows NT 4,0 unterstützt.  
  
 ODBC enthält die ODBC-Komponenten, die zur Unterstützung der oben genannten Konfigurationen erforderlich sind, indem DLLs (Dynamic-Link Libraries) zum Konvertieren von 16-Bit-Adressen in 32-Bit-Adressen und umgekehrt. Das Setup Programm bestimmt, welches Betriebssystem Sie verwenden, und installiert für dieses System erforderliche ODBC-Komponenten. Sie können auch die ODBC-Komponenten installieren, die von allen Systemen verwendet werden.  
  
 In den meisten Fällen sind bei der Portierung einer Anwendung oder eines Treibers zwischen 16 Bit und 32 Bit fünf Arten von Änderungen beteiligt:  
  
-   Änderungen an Meldungs Behandlungs Code  
  
-   Änderungen, da ganze Zahlen und Handles 32 Bits sind  
  
-   Änderungen bei Aufrufen von Windows-Anwendungs Programmierschnittstellen (APIs)  
  
-   Änderungen, um den Treiber Thread sicher zu machen  
  
-   Änderungen an ODBC-Komponenten  
  
 Aus Sicht der Anwendungs-oder Treiberprogrammierung besteht der Hauptunterschied zwischen 16-Bit-und 32-Bit-ODBC-Komponenten darin, dass Sie unterschiedliche Dateinamen haben. Aus Sicht des Systems ist die Architektur der einzelnen Anwendungs-oder Treiber Verbindungen anders, und die Tools zum Verwalten von Datenquellen unterscheiden sich.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
