---
description: Versionsgeschichte der Desktop-Datenbanktreiber
title: Verlauf der Desktop-Datenbanktreiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80e8f1b52abac92ba09b97d35d45dfe0506963ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500323"
---
# <a name="history-of-the-desktop-database-drivers"></a>Versionsgeschichte der Desktop-Datenbanktreiber
Die folgende Tabelle zeigt den Versionsverlauf der Desktop-Datenbanktreiber.  
  
|Version|Veröffentlichungsdatum|Beschreibung|  
|-------------|------------------|-----------------|  
|1.0|1993. August|Der von der pageahead-Software erzeugte Simba-Abfrage Prozessor wurde verwendet. Simba hat ODBC-Aufrufe und SQL-Anweisungen empfangen, Sie in Microsoft Jet installierbare ISAM-aufrufen verarbeitet und dann die Microsoft Jet ISAM Dispatch-Schicht aufgerufen, um den entsprechenden installierbaren ISAM-Treiber zu laden und aufzurufen.|  
|2.0|Dezember 1994|Wird mit ODBC 2,0 verwendet, das die ODBC-Funktionalität erheblich erweitert hat. Die wesentliche Änderung in Version 2,0 war, dass das Microsoft Jet-Datenbankmodul den Simba-Abfrage Prozessor ersetzt hat. Mit der Microsoft Jet-Datenbank-Engine wurden die Desktop-Datenbanktreiber viel enger in die Microsoft Jet installierbaren ISAM-Treiber und die Microsoft Access-Technologie integriert. Bedeutende Verbesserungen:<br /><br /> -Native Unterstützung für scrollbare Cursor.<br />-Native Unterstützung für äußere Joins, aktualisierbare und heterogene Joins und Transaktionen.<br />-32-Bit-Versionen der Treiber für Microsoft Windows NT.|  
|3.0|Oktober 1995|Unterstützung für Windows 95 und Windows NT-Arbeitsstation oder NT Server 3,51 bereitgestellt. In dieser Version sind nur 32-Bit-Treiber enthalten. die 16-Bit-Treiber für Windows-Version 3,1 wurden entfernt.|  
|3,5|Oktober 1996|Diese Treiber waren als Double-Byte-Zeichensatz (Double-Byte Character Set, DBCS) aktiviert, eignen sich besser für die Verwendung mit Internet Anwendungen als frühere Versionen und stellten die Verwendung von Datei Datenquellen Namen (DSNs) in Rechnung. Der Microsoft Access-Treiber wurde in einer RISC-Version für die Verwendung auf Alpha Plattformen für Windows 95/98 und Windows NT 3,51 und spätere Betriebssysteme veröffentlicht.|  
|4,0|Späterer 1998|Bietet Unterstützung für das Unicode-Format des Microsoft Jet-Moduls sowie Kompatibilität für das ANSI-Format früherer Versionen.|  
  
> [!NOTE]  
>  Die Treiber der Version 3.5 wurden für die Verwendung mit ODBC2 entworfen. *x*. Obwohl Sie auch mit ODBC 3,0 funktionieren, unterstützen Sie nicht alle ODBC 3,0-Features. Weitere Informationen zur Funktionsweise dieser Treiber mit ODBC 3,0 finden Sie unter abwärts [Kompatibilität und Einhaltung von Standards](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
