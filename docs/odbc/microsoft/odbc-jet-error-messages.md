---
description: ODBC-Jet-Fehlermeldungen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19f7d4b00c9e6b206ecd563083c0fcf16ced55e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340716"
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
|Microsoft [ODBC-Treiber-Manager] Meldungs *Text*|Treiber-Manager (Odbc32.dll)|  
|Microsoft [Name des ODBC *-Treibers*] Meldungs *Text*|Treiber-ISAM (siehe Treiber-ISAMs)|
