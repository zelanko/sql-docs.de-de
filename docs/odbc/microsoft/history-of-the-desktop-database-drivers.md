---
title: Verlauf der Desktopdatenbanktreiber | Microsoft Docs
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
ms.openlocfilehash: 89434b397c07fdee751ca4272b65ac2eada94cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304981"
---
# <a name="history-of-the-desktop-database-drivers"></a>Versionsgeschichte der Desktop-Datenbanktreiber
Die folgende Tabelle zeigt den Versionsverlauf der Desktopdatenbanktreiber.  
  
|Version|Veröffentlichungsdatum|Beschreibung|  
|-------------|------------------|-----------------|  
|1.0|Januar 1993|Verwendet den SIMBA-Abfrageprozessor, der von PageAhead Software erstellt wurde. SIMBA hat ODBC-Aufrufe und SQL-Anweisungen empfangen, sie in microsoft Jet-installierbaren ISAM-Aufrufen verarbeitet und dann die Microsoft Jet ISAM-Dispatchschicht aufgerufen, um den entsprechenden installierbaren ISAM-Treiber zu laden und aufzurufen.|  
|2.0|Januar 1994|Wird mit ODBC 2.0 verwendet, was die ODBC-Funktionalität deutlich erweitert hat. Die wichtigste Änderung in Version 2.0 war, dass das Microsoft Jet-Datenbankmodul den SIMBA-Abfrageprozessor ersetzte. Mit dem Microsoft Jet-Datenbankmodul sind die Desktopdatenbanktreiber viel enger in die installierbaren ISAM-Treiber von Microsoft Jet und die Microsoft Access-Technologie integriert. Wesentliche Verbesserungen waren:<br /><br /> - Native Unterstützung für scrollbare Cursor.<br />- Native Unterstützung für äußere Verknüpfungen, aktualisierbare und heterogene Verknüpfungen und Transaktionen.<br />- 32-Bit-Versionen der Treiber für Microsoft Windows NT.|  
|3.0|Januar 1995|Unterstützung für Windows 95 und Windows NT Workstation oder NT Server 3.51. Nur 32-Bit-Treiber wurden in dieser Version enthalten; Die 16-Bit-Treiber für Windows Version 3.1 wurden entfernt.|  
|3,5|Januar 1996|Diese Treiber waren DBCS-fähig (Double-Byte Character Set), eigneten sich besser für die Verwendung mit Internetanwendungen als frühere Versionen und berücksichtigten die Verwendung von DSNs (File Data Source Names). Der Microsoft Access-Treiber wurde in einer RISC-Version für die Verwendung auf Alpha-Plattformen für Windows 95/98 und Windows NT 3.51 und neuere Betriebssysteme veröffentlicht.|  
|4,0|Ende 1998|Bietet Unterstützung für das Microsoft Jet Engine Unicode-Format sowie Kompatibilität für das ANSI-Format früherer Versionen.|  
  
> [!NOTE]  
>  Die Treiber version3.5 wurden für odBC2 entwickelt. *x*. Obwohl sie auch mit ODBC 3.0 funktionieren, unterstützen sie nicht alle ODBC 3.0-Funktionen. Weitere Informationen zur Funktionsweise dieser Treiber mit ODBC 3.0 finden Sie unter [Abwärtskompatibilität und Konformität von Standards](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
