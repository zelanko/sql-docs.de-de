---
title: Recordkreateoptionsenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65fe33b73cf77a27fcd69743ffb09cb05e197797
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917342"
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Gibt an, ob ein vorhandener **Datensatz** geöffnet oder ein neuer **Datensatz** für die [Open](../../../ado/reference/ado-api/open-method-ado-record.md) -Methode des [Aufzeichnungs](../../../ado/reference/ado-api/record-object-ado.md) Objekts erstellt werden soll. Die Werte können mit einem and-Operator kombiniert werden.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adkreatecollection**|0x2000|Erstellt einen neuen **Datensatz** an dem durch den *Quell* Parameter angegebenen Knoten, anstatt einen vorhandenen **Datensatz**zu öffnen. Wenn die Quelle auf einen vorhandenen Knoten zeigt, tritt ein Laufzeitfehler auf, es sei denn, **adkreatecollection** wird mit **adopenifist** oder **adkreateüberschreibung**kombiniert.|  
|**adkreatenoncollection**|0|Erstellt einen neuen **Datensatz** vom Typ [adsimplerecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adkreateüberschreibung**|0x4000000|Ändert die erstellungsflags **adkreatecollection**, **adkreatenoncollection**und **adkreatestructdoc**. Wenn oder mit diesem Wert und einem der erstellungsflagwerte verwendet wird, wird der vorhandene Datensatz überschrieben, und es wird ein neuer **Datensatz** erstellt, wenn die Quell-URL auf einen vorhandenen Knoten oder **Datensatz**verweist. Dieser Wert kann nicht in Verbindung mit **adopenises**verwendet werden.|  
|**adkreatestructdoc**|0x80000000|Erstellt einen neuen **Datensatz** vom Typ [adstructdoc](../../../ado/reference/ado-api/recordtypeenum.md), anstatt einen vorhandenen **Datensatz**zu öffnen.|  
|**adfailif NotExists**|-1|Default. Führt zu einem Laufzeitfehler, wenn die *Quelle* auf einen nicht vorhandenen Knoten zeigt.|  
|**adopenif vorhanden**|0x2000000|Ändert die erstellungsflags **adkreatecollection**, **adkreatenoncollection**und **adkreatestructdoc**. Wenn oder mit diesem Wert und einem der erstellungsflagwerte verwendet wird, muss der Anbieter den vorhandenen **Datensatz** öffnen, anstatt einen neuen Datensatz zu erstellen, wenn die Quell-URL auf ein vorhandenes Knoten-oder **Daten Satz** Objekt verweist. Dieser Wert kann nicht in Verbindung mit **adkreateüberschreibung**verwendet werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
