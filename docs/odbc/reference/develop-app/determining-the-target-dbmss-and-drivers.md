---
title: Bestimmen der Ziel-DBMS und -Treiber | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f8811e4d289a8fc89c2c3773aab973df523025f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305871"
---
# <a name="determining-the-target-dbmss-and-drivers"></a>Ermitteln der Ziel-DBMS und Zieltreiber
Die nächste zu berücksichtigende Frage lautet: Was sind die Ziel-DBMS für die Anwendung und welche Treiber stehen zur Verfügung, die diese DBMS unterstützen? Da generische Anwendungen in der Regel sehr interoperabel sind, ist die Frage der Ziel-DBMS am besten auf benutzerdefinierte und vertikale Anwendungen anwendbar. Die Frage der Zieltreiber gilt jedoch für alle Anwendungen, da die Treiber in Geschwindigkeit, Qualität, Funktionsunterstützung und Verfügbarkeit sehr unterschiedlich sind. Wenn die Treiber mit der Anwendung neu verteilt werden sollen, müssen auch die Kosten und die Verfügbarkeit von Lizenzplänen berücksichtigt werden.  
  
 Für viele benutzerdefinierte Anwendungen liegen die Ziel-DBMS auf der Hand: Es handelt sich um vorhandene DBMS, auf die die Anwendung zugreifen soll. Auch DBMS, in die eine zukünftige Migration geplant ist, sollten in Betracht gezogen werden. Die hauptfragestelle für diese Anwendungen ist jedoch, welcher Fahrer oder Welche Fahrer mit ihnen verwendet werden sollen. Für andere benutzerdefinierte Anwendungen , die nicht für den Zugriff auf ein vorhandenes DBMS ausgelegt sind, können die Ziel-DBMS basierend auf Feature-Unterstützung, gleichzeitiger Benutzerunterstützung, Treiberverfügbarkeit und Erschwinglichkeit ausgewählt werden.  
  
 Für vertikale Anwendungen werden die Ziel-DBMS in der Regel basierend auf Feature-Support, Treiberverfügbarkeit und Markt ausgewählt. Beispielsweise muss eine vertikale Anwendung, die für kleine Unternehmen entwickelt wurde, auf DBMS abzielen, die für diese Unternehmen erschwinglich sind; Eine vertikale Anwendung, die als Add-on zu vorhandenen DBMS entwickelt wurde, muss auf weit verbreitete DBMS ausgerichtet sein.  
  
 Bei der Auswahl von Ziel-DBMs sollten die Unterschiede zwischen Desktop- und Serverdatenbanken berücksichtigt werden. Desktopdatenbanken wie dBASE, Paradox und Btrieve sind weniger leistungsfähig als Serverdatenbanken. Da auf sie im Allgemeinen über die weniger leistungsfähigen SQL-Engines zugegriffen wird, die in den meisten dateibasierten Treibern zu finden sind, fehlt ihnen häufig die vollständige Transaktionsunterstützung, sie unterstützen weniger gleichzeitige Benutzer und verfügen über eingeschränkte SQL-Vorgänge. Sie sind jedoch kostengünstig und verfügen über eine große installierte Basis.  
  
 Serverdatenbanken wie Oracle, DB2 und SQL Server bieten vollständige Transaktionsunterstützung, unterstützen viele gleichzeitige Benutzer und verfügen über Rich SQL. Sie sind viel teurer und haben eine kleinere installierte Basis. Auf der anderen Seite sind die Softwarepreise tendenziell höher, was einen kleineren potenziellen Markt etwas ausgleichen wird.  
  
 Daher können Ziel-DBMS manchmal basierend auf den Funktionen ausgewählt werden, die von der Anwendung und dem Zielmarkt der Anwendung benötigt werden. Beispielsweise zielt ein Auftragserfassungssystem für große Unternehmen möglicherweise nicht auf Desktopdatenbanken ab, da diese keine angemessene Transaktionsunterstützung haben. Ein ähnliches System, das für kleine Unternehmen entwickelt wurde, kann die meisten Serverdatenbanken auf der Grundlage der Kosten ausschließen. Und Entwickler generischer Anwendungen können auf beide abzielen, aber vermeiden Sie die Verwendung der erweiterten Funktionen in Serverdatenbanken.
