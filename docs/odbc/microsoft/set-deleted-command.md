---
title: Befehl SET DELETED | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5efbd7e98b430128e52634f5c7d71597afc89ace
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806068"
---
# <a name="set-deleted-command"></a>SET DELETED-Befehl
Gibt an, ob zum Löschen markierte Datensätze verarbeitet wurden und ob sie für die Verwendung in anderen Befehlen verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 ON  
 (Standard für den Treiber; der Standardwert für Visual FoxPro ist OFF). Gibt an, die Befehle, die ausgeführt werden (einschließlich der Datensätze in verknüpften Tabellen) Datensätze mit einem Bereich zum Löschen markierte Einträge ignoriert.  
  
 OFF  
 Gibt an, dass Datensätze markiert, für das Löschen von Befehlen zugegriffen werden kann, die auf Datensätze (einschließlich der Datensätze in verknüpften Tabellen) verwendet werden. verwenden einen Bereich.  
  
## <a name="remarks"></a>Hinweise  
 Fragt, dass verwenden (gelöscht), zum Testen des Status von Datensätzen mithilfe von Visual FoxPro-Rushmore-Technologie, wenn die Tabelle indiziert ist, auf die gelöschte () optimiert werden kann.  
  
> [!IMPORTANT]  
>  Legen Sie gelöscht wird ignoriert, wenn der Standardbereich für den Befehl des aktuellen Datensatzes ist oder wenn Sie einen Bereich eines einzelnen Datensatzes einschließen. INDEX wird immer ignoriert wird, legen Sie gelöscht und alle Datensätze in der Tabelle indiziert.  
  
## <a name="see-also"></a>Siehe auch  
 [DELETE (SQL-Befehl)](../../odbc/microsoft/delete-sql-command.md)
