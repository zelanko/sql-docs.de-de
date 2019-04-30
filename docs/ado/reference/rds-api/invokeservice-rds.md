---
title: InvokeService (RDS) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: efcb67792eed98caebd541ab7dab3a3fef4cd626
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308772"
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Gibt einen Zeiger auf eine leistungsfähigere Version des Objekts auf die angeforderte Schnittstelle zurück.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Parameter  
 *riid*  
  
 [in] Der Bezeichner der angeforderten Schnittstelle.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] Das weniger leistungsstarken Quellobjekt.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] Die Adresse der Zeigervariablen, die die im angeforderten Schnittstellenzeiger empfängt *Riid*. Bei erfolgreicher Rückgabe die *PpunkMoreFunctionalInterface* Parameter enthält, den angeforderten Schnittstellenzeiger auf das Objekt. Wenn das Objekt im angegebenen Schnittstelle nicht unterstützt *Riid*, *PpunkMoreFunctionalInterface* auf NULL festgelegt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der gibt an, wenn der Aufruf der **InvokeService** Methode war erfolgreich.  
  
## <a name="remarks"></a>Hinweise  
 Die RDS-Cursor-Engine-Implementierung von **InvokeService** übernimmt das Eingaberowset (oder mehrere "Results"-Objekt), füllt die Cursor-Engine aus dem Eingaberowset und gibt dann einen Zeiger auf sich selbst zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [IRDSService-Schnittstelle (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [RDS-Methoden](../../../ado/reference/rds-api/rds-methods.md)


