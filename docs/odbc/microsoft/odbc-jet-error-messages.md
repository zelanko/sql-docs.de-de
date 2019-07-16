---
title: ODBC Jet-Fehlermeldungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915816"
---
# <a name="odbc-jet-error-messages"></a>ODBC-Jet-Fehlermeldungen
Für Fehler, die in der Datenquelle auftreten, gibt der ODBC-Treiber eine Fehlermeldung zurückgegeben, von der ODBC-Datei-Bibliothek zurück. Für Fehler, die auftreten, in der ODBC-Treiber oder der Treiber-Manager, der Treiber gibt eine Fehlermeldung für den Text basierend, die mit den SQLSTATE verknüpft ist.  
  
 Fehlermeldungen weisen folgendes Format:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Die Präfixe in eckige Klammern ([]) Geben Sie den Speicherort des Fehlers. Beim Auftreten des Fehlers im Treiber-Manager, *Datenquelle* nicht angegeben wird. Beim Auftreten des Fehlers in der Datenquelle, die [*Hersteller*] und [*ODBC-Komponenten*] Präfixe zu identifizieren, den Hersteller und den Namen der ODBC-Komponente, die den Fehler aus der Datenquelle.  
  
 Die folgende Tabelle zeigt die vom Treiber-Manager und ISAM-Treiber zurückgegebenen Fehlermeldungen:  
  
|Fehlermeldung|: Fehlerort|  
|-------------------|--------------------|  
|[Microsoft] [ODBC-Treiber-Manager] *-Nachrichtentext*|Treiber-Manager (Odbc32.dll)|  
|[Microsoft] [ODBC *Treibername*] *-Nachrichtentext*|ISAM-Treiber (Siehe Driver ISAMs)|
