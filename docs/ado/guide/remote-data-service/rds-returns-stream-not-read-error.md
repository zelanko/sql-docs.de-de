---
title: RDS gibt &quot;Stream nicht lesen&quot; Fehler | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c89756e86a702217d5d9d8495bf62b0d27f52321
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922467"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS gibt &quot;Stream nicht lesen&quot; Fehler
"Das Stream-Objekt konnte nicht gelesen werden, da es leer ist oder die aktuelle Position am Ende der Stream ist. Legen Sie für nicht leere Datenströme die aktuelle Position mit der Eigenschaft "Position" ein. Um festzustellen, ob ein Stream leer ist, überprüfen Sie die Size-Eigenschaft."  
  
 Wenn Sie diese Fehlermeldung wird angezeigt, Sie haben möglicherweise versucht eine parametrisierte Abfrage für die hierarchische über http zu verwenden. RDS lässt nicht zu, dass Sie remote parametrisierte Hierarchien zu verwenden.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


