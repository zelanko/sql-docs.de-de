---
description: Connect-Eigenschaft (RDS)
title: Connect-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: rothja
ms.author: jroth
ms.openlocfilehash: 5387745648b4aafa1db9964a8b82d8aa403e8473
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722511"
---
# <a name="connect-property-rds"></a>Connect-Eigenschaft (RDS)
Gibt den Datenbanknamen an, von dem die Abfrage-und Aktualisierungs Vorgänge ausgeführt werden.  
  
 Sie können die **Connect** -Eigenschaft zur Entwurfszeit in [RDS festlegen. Objekt Tags des DataControl](./datacontrol-object-rds.md) -Objekts oder zur Laufzeit im Skriptcode (z. b. VBScript).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine gültige Verbindungszeichenfolge. Weitere allgemeine Informationen zu Verbindungs Zeichenfolgen finden Sie in der [ConnectionString](../ado-api/connectionstring-property-ado.md) -Eigenschaft oder in der Provider-Dokumentation.  
  
> [!NOTE]
>  Angeben von MS Remote als Anbieter für **RDS. DataControl** würde ein Szenario mit vier Ebenen erstellen. Szenarios, die größer als drei Stufen sind, wurden nicht getestet und sollten nicht benötigt werden.  
  
 *DataControl*  
 Eine Objekt Variable, die einen **RDS darstellt. DataControl** -Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Verbindungs Eigenschaft (VBScript)](./connect-property-example-vbscript.md)   
 [Query-Methode (RDS)](./query-method-rds.md)   
 [Refresh-Methode (RDS)](./refresh-method-rds.md)   
 [SubmitChanges-Methode (RDS)](./submitchanges-method-rds.md)