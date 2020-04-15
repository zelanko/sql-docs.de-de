---
title: SET EXKLUSIVE Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d140c4be3ab850547ac82f9b954e7313b008dbf0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300860"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE-Befehl
Gibt an, ob Tabellendateien für die exklusive oder freigegebene Verwendung in einem Netzwerk geöffnet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 Beschränkt die Zugänglichkeit einer Tabelle, die in einem Netzwerk geöffnet wurde, für den Benutzer, der sie geöffnet hat. Auf die Tabelle können andere Benutzer im Netzwerk nicht zugreifen. SET EXCLUSIVE ON verhindert auch, dass alle anderen Benutzer schreibgeschützten Zugriff haben.  
  
 OFF  
 (Standard für den Treiber; die Standardeinstellungen für Visual FoxPro sind ON für die globale Datensitzung und OFF für eine private Datensitzung.) Ermöglicht die gemeinsame Freigabe und Änderung einer in einem Netzwerk geöffneten Tabelle durch einen beliebigen Benutzer im Netzwerk.  
  
## <a name="remarks"></a>Bemerkungen  
 Durch das Ändern der Einstellung von SET EXCLUSIVE wird der Status zuvor geöffneter Tabellen nicht geändert. Wenn z. B. eine Tabelle geöffnet wird, wobei SET EXCLUSIVE auf ON gesetzt ist und SET EXCLUSIVE später in OFF geändert wird, behält die Tabelle ihren Status für die ausschließliche Verwendung bei.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einrichten von ODBC-Visual FoxPro (Dialogfeld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
