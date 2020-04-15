---
title: SET DELETED Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b3302dc7eecca7135dab9dff5afa376169be0f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300880"
---
# <a name="set-deleted-command"></a>SET DELETED-Befehl
Gibt an, ob zum Löschen markierte Datensätze verarbeitet werden und ob sie für die Verwendung in anderen Befehlen verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 (Standard für den Treiber; die Standardeinstellung für Visual FoxPro ist AUS.) Gibt an, dass Befehle, die für Datensätze (einschließlich Datensätze in verknüpften Tabellen) mit einem Bereichs verwendet werden, Datensätze ignorieren, die zum Löschen markiert sind.  
  
 OFF  
 Gibt an, dass datensätze, die zum Löschen markiert sind, mithilfe eines Bereichs auf Befehle zugreifen können, die mit Datensätzen (einschließlich Datensätzen in verknüpften Tabellen) ausgeführt werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Abfragen, die DELETED( verwenden, um den Status von Datensätzen zu testen, können mit der Visual FoxPro Rushmore-Technologie optimiert werden, wenn die Tabelle auf DELETED( indiziert ist.  
  
> [!IMPORTANT]  
>  SET DELETED wird ignoriert, wenn der Standardbereich für den Befehl der aktuelle Datensatz ist oder wenn Sie einen Bereich eines einzelnen Datensatzes einschließen. INDEX ignoriert immer SET DELETED und indiziert alle Datensätze in der Tabelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DELETE (SQL-Befehl)](../../odbc/microsoft/delete-sql-command.md)
