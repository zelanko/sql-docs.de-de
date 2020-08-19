---
description: RDS gibt &quot; Fehler Datenstrom nicht gelesen &quot;
title: RDS gibt &quot; Fehler Datenstrom nicht gelesen &quot; | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 039a881d0d38e6dc58661c92f59ba74bd9ea2bb3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452102"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS gibt &quot; Fehler Datenstrom nicht gelesen &quot;
"Das Datenstrom Objekt konnte nicht gelesen werden, weil es leer ist, oder die aktuelle Position befindet sich am Ende des Streams. Für nicht leere Streams legen Sie die aktuelle Position mit der Positions Eigenschaft fest. Überprüfen Sie die Size-Eigenschaft, um zu bestimmen, ob ein Datenstrom leer ist. "  
  
 Wenn diese Fehlermeldung angezeigt wird, haben Sie möglicherweise versucht, eine parametrisierte hierarchische Abfrage über HTTP zu verwenden. RDS gestattet Ihnen nicht die Verwendung von Remote parametrisierten Hierarchien.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


