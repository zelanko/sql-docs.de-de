---
title: ODBC-Jet-Fehlermeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85e0f9a8bc7015a0ad5b12ce46a6c94ab31ca43c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915816"
---
# <a name="odbc-jet-error-messages"></a>ODBC-Jet-Fehlermeldungen
Bei Fehlern, die in der Datenquelle auftreten, gibt der ODBC-Treiber eine Fehlermeldung zurück, die von der ODBC-Datei Bibliothek an ihn zurückgegeben wurde. Bei Fehlern, die im ODBC-Treiber oder Treiber-Manager auftreten, gibt der Treiber eine Fehlermeldung basierend auf dem Text zurück, der dem SQLSTATE-Typ zugeordnet ist.  
  
 Fehlermeldungen weisen das folgende Format auf:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Die Präfixe in eckigen Klammern ([]) identifizieren den Speicherort des Fehlers. Wenn der Fehler im Treiber-Manager auftritt, wird keine *Datenquelle* angegeben. Wenn der Fehler in der Datenquelle auftritt, identifizieren die Präfixe [*Vendor*] und [*ODBC-Component*] den Hersteller und den Namen der ODBC-Komponente, die den Fehler aus der Datenquelle erhalten hat.  
  
 In der folgenden Tabelle werden die vom Treiber-Manager und vom Treiber-ISAM zurückgegebenen Fehlermeldungen angezeigt:  
  
|Fehlermeldung|Fehler Speicherort|  
|-------------------|--------------------|  
|Microsoft [ODBC-Treiber-Manager] Meldungs *Text*|Treiber-Manager (odbc32. dll)|  
|Microsoft [Name des ODBC *-Treibers*] Meldungs *Text*|Treiber-ISAM (siehe Treiber-ISAMs)|
