---
title: Befehl SET EXCLUSIVE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d1a37043d332b54d0d5c5ebb7b2ba9f3acce000
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071758"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE-Befehl
Gibt an, ob die Tabellendateien für exklusive oder gemeinsame Nutzung in einem Netzwerk geöffnet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 ON  
 Schränkt ein Zugriff auf eine Tabelle in einem Netzwerk, dem Benutzer, die sie geöffnet geöffnet. In der Tabelle kann nicht für andere Benutzer für das Netzwerk zugegriffen werden. SET exklusive ON verhindert, dass alle anderen Benutzer schreibgeschützten Zugriff verfügen.  
  
 OFF  
 (Standard für den Treiber, die Standardeinstellungen für Visual FoxPro sind ON oder OFF die globalen Daten für eine private Daten-Sitzung.) Kann eine Tabelle in einem Netzwerk gemeinsam verwendet und geändert werden, von jedem Benutzer im Netzwerk geöffnet.  
  
## <a name="remarks"></a>Hinweise  
 Ändern der Einstellung der exklusive festgelegt ändert nicht den Status des zuvor geöffneten Tabellen. Wenn eine Tabelle mit EXKLUSIVEN festgelegt auf ON festgelegt geöffnet wird, und exklusive festgelegt wird später auf OFF geändert, behält die Tabelle den Exklusivmodus-Status.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten von ODBC-Visual FoxPro (Dialogfeld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
