---
title: Invokeservice (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86ebb27ebdc5de5a045304afe45cd8653e491827
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963864"
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Gibt einen Zeiger auf die angeforderte Schnittstelle für eine leistungsfähigere Version des-Objekts zurück.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Parameter  
 *riid*  
  
 in Der Bezeichner der angeforderten Schnittstelle.  
  
 *punkNotSoFunctionalInterface*  
  
 in Das weniger fähige Quell Objekt.  
  
 *ppunkMoreFunctionalInterface*  
  
 vorgenommen Die Adresse der Zeiger Variablen, die den in *riid*angeforderten Schnittstellen Zeiger empfängt. Nach erfolgreicher Rückgabe enthält der *ppunkmorefunctionalinterface* -Parameter den angeforderten Schnittstellen Zeiger auf das-Objekt. Wenn das Objekt die in *riid*angegebene Schnittstelle nicht unterstützt, wird *ppunkmorefunctionalinterface* auf NULL festgelegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob der Aufruf der **invokeservice** -Methode erfolgreich war.  
  
## <a name="remarks"></a>Bemerkungen  
 Die RDS-Cursor-Engine-Implementierung von **invokeservice** nimmt das Eingaberowset (oder mehrere Ergebnis Objekte), füllt die Cursor-Engine aus dem Eingaberowset auf und gibt dann einen Zeiger auf sich selbst zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [IRDSService-Schnittstelle (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [RDS-Methoden](../../../ado/reference/rds-api/rds-methods.md)


