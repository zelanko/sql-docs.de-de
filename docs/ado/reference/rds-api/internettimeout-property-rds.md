---
title: InternetTimeout-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebc5caa6ccdb3c14faf722f1ccc66c46befa6fbb
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606470"
---
# <a name="internettimeout-property-rds"></a>InternetTimeout-Eigenschaft (RDS)
Gibt die Anzahl der Millisekunden, die gewartet wird, bevor eine Anforderung ein auftritt Timeout.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** der Timeout-Wert, der die Anzahl der Millisekunden, bevor eine Anforderung darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft gilt nur für Anforderungen, die mit HTTP oder HTTPS gesendet.  
  
 Anforderungen in einer Umgebung mit drei Ebenen dauert mehrere Minuten ausgeführt. Verwenden Sie diese Eigenschaft, um zusätzliche Zeit für Anforderungen mit langer anzugeben.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [InternetTimeout-Eigenschaft – Beispiel (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [InternetTimeout-Eigenschaft – Beispiel (VC++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

