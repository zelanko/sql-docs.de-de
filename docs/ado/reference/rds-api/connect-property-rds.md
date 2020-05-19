---
title: Connect-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 0f89e1097565c5b9841db69ac44e13c8d7138e64
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755588"
---
# <a name="connect-property-rds"></a>Connect-Eigenschaft (RDS)
Gibt den Datenbanknamen an, von dem die Abfrage-und Aktualisierungs Vorgänge ausgeführt werden.  
  
 Sie können die **Connect** -Eigenschaft zur Entwurfszeit in [RDS festlegen. Objekt Tags des DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekts oder zur Laufzeit im Skriptcode (z. b. VBScript).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine gültige Verbindungszeichenfolge. Weitere allgemeine Informationen zu Verbindungs Zeichenfolgen finden Sie in der [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft oder in der Provider-Dokumentation.  
  
> [!NOTE]
>  Angeben von MS Remote als Anbieter für **RDS. DataControl** würde ein Szenario mit vier Ebenen erstellen. Szenarios, die größer als drei Stufen sind, wurden nicht getestet und sollten nicht benötigt werden.  
  
 *DataControl*  
 Eine Objekt Variable, die einen **RDS darstellt. DataControl** -Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Verbindungs Eigenschaft (VBScript)](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Query-Methode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges-Methode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


