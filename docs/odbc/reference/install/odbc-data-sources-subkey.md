---
title: Unterschlüssel für ODBC-Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9867946ce84163a504582c8a9575100c3c9aacd3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600868"
---
# <a name="odbc-data-sources-subkey"></a>Unterschlüssel für ODBC-Datenquellen
Die Werte unter dem Unterschlüssel für ODBC-Datenquellen aufgelistet, die Datenquellen. Das Format dieser Werte ist, wie in der folgenden Tabelle gezeigt.  
  
|Name|Datentyp|data|  
|----------|---------------|----------|  
|*Datenquellenname:*|REG_SZ|*Treiber-Beschreibung*|  
  
 Die *Datenquellenname* Wert durch die Verwaltung-Anwendung (die den Benutzer in der Regel dafür-eingabeaufforderungen), definiert ist und *treiberbeschreibung* vom Treiber Entwickler definiert ist (Dies ist normalerweise der Name des der DBMS der Treiber zugeordnet).  
  
 Nehmen wir beispielsweise an, die drei Datenquellen definiert wurden: Inventar, die SQL Server verwendet Gehaltsabrechnungen, das die dBASE verwendet; und Mitarbeiter, verwendet Format-Text-Dateien. Die Werte unter dem Unterschlüssel für ODBC-Datenquellen könnte folgendermaßen aussehen:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
