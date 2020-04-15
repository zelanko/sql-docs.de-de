---
title: ODBC Jet Fehlermeldungen | Microsoft Docs
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
ms.openlocfilehash: e8fa6e672b69c7791e66dc3919e6fcd22b7c3de7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293110"
---
# <a name="odbc-jet-error-messages"></a>ODBC-Jet-Fehlermeldungen
Bei Fehlern, die in der Datenquelle auftreten, gibt der ODBC-Treiber eine Fehlermeldung zurück, die von der ODBC-Dateibibliothek zurückgegeben wird. Bei Fehlern, die im ODBC-Treiber oder im Treiber-Manager auftreten, gibt der Treiber eine Fehlermeldung zurück, die auf dem Text basiert, der dem SQLSTATE zugeordnet ist.  
  
 Fehlermeldungen haben das folgende Format:  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 Die Präfixe in Klammern ([ ]) identifizieren die Position des Fehlers. Wenn der Fehler im Treiber-Manager auftritt, wird keine *Datenquelle* angegeben. Wenn der Fehler in der Datenquelle auftritt, identifizieren die Präfixe [*Vendor*] und [*ODBC-component*] den Hersteller und den Namen der ODBC-Komponente, die den Fehler von der Datenquelle empfangen hat.  
  
 Die folgende Tabelle zeigt die Fehlermeldungen, die vom Treiber-Manager und treiber-ISAM zurückgegeben werden:  
  
|Fehlermeldung|Fehlerort|  
|-------------------|--------------------|  
|[Microsoft] [ODBC-Treiber-Manager] *Message-Text*|Treiber-Manager (Odbc32.dll)|  
|[Microsoft] *[ODBC-Treibername*] *Message-Text*|Treiber-ISAM (siehe Treiber-ISAMs)|
