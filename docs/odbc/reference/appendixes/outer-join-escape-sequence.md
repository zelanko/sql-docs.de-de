---
title: Escapesequenz für äußere Joins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 576fe7268ccf71a8c926f6b1124ebbf8a8c711b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100641"
---
# <a name="outer-join-escape-sequence"></a>Escapesequenz für äußere Verknüpfungen
ODBC verwendet Escapesequenzen für äußere Joins. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Hinweise  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-outer-Joins-Escapesequenz* :: =  
  
 *Initiator der ODBC-esc* ABl. *inklusionsverknüpfungs ODBC-esc-Terminator*  
  
 *inklusionsverknüpfungs* :: = *Tabellenname* [*Korrelationsname*] {Links &#124; rechts &#124; vollständige}  
  
 ÄUßERER JOIN {*Tabellenname* [*Korrelationsname*] &#124; *äußere Join*} ON  
  
 *Suche:*  
  
 *condition*  
  
 *Korrelationsname* :: = *definiert-Benutzername*  
  
 *Initiator der ODBC-esc* :: = {  
  
 *ODBC-esc-Terminator* :: =}  
  
 Um zu bestimmen, welche Teile der diese Anweisung unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_OJ_CAPABILITIES-Informationen. Für äußere Joins *Suchbedingung* darf nur die Join-Bedingung zwischen den angegebenen *Tabellennamen*.
