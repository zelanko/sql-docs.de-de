---
title: Ausführen von Transaktionen mit der JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d18f5c550bbf60446ac47961d16c1bbdb7cb2e4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770344"
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Ausführen von Transaktionen mit dem JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die Transaktionsverarbeitung bildet eine unverzichtbare Anforderung aller Anwendungen, die die Konsistenz der permanenten Daten garantieren müssen. Mit [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ist eine lokale oder verteilte Transaktionsverarbeitung möglich. Bei Transaktionen handelt es sich um unteilbare, konsistente, isolierte und dauerhafte Module der Ausführung.  
  
 Die Themen in diesem Abschnitt beschreiben die Unterstützung von Transaktionen durch den JDBC-Treiber, wie z. B. Isolationsstufen, Sicherungspunkte für Transaktionen und Holdability für Resultsets.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Grundlegendes zu Transaktionen](../../connect/jdbc/understanding-transactions.md)|Enthält eine Übersicht über die Verwendung von Transaktionen mit dem JDBC-Treiber.|  
|[Grundlegendes zu XA-Transaktionen](../../connect/jdbc/understanding-xa-transactions.md)|Enthält eine Übersicht über die Verwendung von XA-Transaktionen mit dem JDBC-Treiber.|  
|[Grundlegendes zu Isolationsstufen](../../connect/jdbc/understanding-isolation-levels.md)|Beschreibt die verschiedenen Isolationsstufen, die vom JDBC-Treiber unterstützt werden.|  
|[Verwenden von Sicherungspunkten](../../connect/jdbc/using-savepoints.md)|Beschreibt die Verwendung des JDBC-Treibers für Sicherungspunkte für Transaktionen.|  
|[Verwenden der Haltbarkeit](../../connect/jdbc/using-holdability.md)|Beschreibt die Verwendung des JDBC-Treibers für die Holdability für Resultsets.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
