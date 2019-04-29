---
title: Ermitteln der Ziel-DBMS und Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- target DBMSs and drivers in interoperability [ODBC]
- interoperability [ODBC], target dbmss and drivers
ms.assetid: 23bee0f6-e12a-4598-b34e-df11a8086829
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92da788205213394edc75257d8266752a2a9d8df
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63034947"
---
# <a name="determining-the-target-dbmss-and-drivers"></a>Ermitteln der Ziel-DBMS und Zieltreiber
Ist die nächste Frage zu berücksichtigen, was das Ziel-DBMS-Systeme für die Anwendung sind, und welche Treiber zur Verfügung stehen unterstützen, die die DBMS-Systeme? Da generische Anwendungen sind hochgradig interoperabel tendenziell, ist die Frage der Ziel-DBMS-Systeme am besten geeignete benutzerdefinierte und vertikale Anwendungen. Gilt jedoch die Frage der Zieltreiber für alle Anwendungen, da der Treiber in der Geschwindigkeit, Qualität, Unterstützung von Funktionen und Verfügbarkeit variieren. Auch wenn die Treiber sind mit der Anwendung verteilt werden, die Kosten und die Verfügbarkeit von lizenzierungsplänen berücksichtigt werden müssen.  
  
 Bei vielen benutzerdefinierten Anwendungen sind das Ziel-DBMS offensichtlich: Sie vorhandene DBMS-Systeme, die die Anwendung, um entwickelt wurde Zugriff auf. DBMS-Systeme auf die Migration in der Zukunft geplant ist, sollten ebenfalls berücksichtigt werden. Allerdings ist die wesentliche Frage für diese Anwendungen welche Treiber oder Treiber für die Verwendung mit diesem Typ verwenden. Für andere benutzerdefinierten Anwendungen – diejenigen, bei denen nicht auf eine vorhandene DBMS entwickelt wurden – kann das Ziel-DBMS basierend auf Feature-Unterstützung, Unterstützung für gleichzeitige Benutzer, Verfügbarkeit von Gerätetreibern und kostengünstige ausgewählt werden.  
  
 Für vertikale Anwendungen auf Grundlage des Ziel-DBMS-Systeme in der Regel ausgewählt werden Feature-Unterstützung und Verfügbarkeit von Gerätetreibern Markt. Eine vertikale Anwendung, die für kleine Unternehmen konzipiert muss z. B. DBMS abzielen, die diesen Unternehmen kostengünstige sind; eine vertikale Anwendung, die als Add-on zu vorhandenen DBMS häufig beziehen muss konzipiert wird DBMS verwendet.  
  
 Beim Auswählen eines Ziel-DBMS sollten die Unterschiede zwischen Desktop und Server-Datenbanken berücksichtigt werden. Desktopdatenbanken wie z. B. Paradox, dBASE und Btrieve sind weniger leistungsfähig als die Server-Datenbanken. Da sie in der Regel über den weniger leistungsfähigen SQL-Engines finden Sie in der am häufigsten von dateibasierten Treibern zugegriffen werden, vollständige Transaktion unterstützen keine sie häufig, weniger gleichzeitige Benutzer unterstützen und SQL nur über begrenzte. Sie können jedoch kostengünstig und haben eine große Installationsbasis.  
  
 Wie Oracle, DB2 und SQL Server-Datenbanken bieten vollständige transaktionsunterstützung, viele gleichzeitige Benutzer unterstützen und umfangreichen SQL haben. Sie sind wesentlich teurer und haben eine kleinere Installationsbasis. Auf der anderen Seite tendenziell Software Preise höher Offsets etwas auf einen kleinere potenziellen Markt.  
  
 Ziel-DBMS-Systeme manchmal kann daher auch basierend auf die von der Anwendung und Zielmarkt der Anwendung erforderlichen Funktionen ausgewählt werden. Beispielsweise kann ein Auftragserfassungssystem für Großunternehmen Desktopdatenbanken nicht abzielen, da diese keine transaktionsunterstützung für die angemessene. Ein ähnliches System für kleine Unternehmen konzipiert, kann die meisten Serverdatenbanken auf Grundlage der Kosten ausschließen. Und Entwickler von generischen Anwendungen möglicherweise sowohl als Zielplattform verwenden Sie die erweiterten Features in Server-Datenbanken gefunden.
