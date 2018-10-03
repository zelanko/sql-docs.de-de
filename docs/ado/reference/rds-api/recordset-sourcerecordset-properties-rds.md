---
title: Recordset, SourceRecordset-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc0b548015cc63117cff566a2c4507b266d5ab7b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657508"
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Recordset, SourceRecordset-Eigenschaft (RDS)
Gibt an, die **Recordset** Objekt aus der ein benutzerdefiniertes Geschäftsobjekt zurückgegeben.  
  
 **Gilt für:** [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *Recordset*  
 Eine Objektvariable, steht ein **Recordset** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Sie können festlegen, die **SourceRecordset** Eigenschaft, um eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) über ein benutzerdefiniertes Geschäftsobjekt zurückgegeben.  
  
 Diese Eigenschaften ermöglichen eine Anwendung zur Handhabung des Bindungsvorgangs über einen benutzerdefinierten Prozess. Erhalten sie ein Rowset, das innerhalb einer **Recordset** , damit Sie direkt mit interagieren können der **Recordset**, Ausführen von Aktionen wie das Festlegen von Eigenschaften oder das Durchlaufen der **Recordset** .  
  
 Sie können festlegen, die **SourceRecordset** -Eigenschaft, oder erfahren Sie die **Recordset** Eigenschaft zur Laufzeit in Skriptcode.  
  
 **SourceRecordset** ist eine Nur-Schreiben-Eigenschaft, im Gegensatz zu den **Recordset** -Eigenschaft, die eine Eigenschaft schreibgeschützt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Recordset und Sourcerecordse-Eigenschaften-Beispiel (VBScript)](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [CreateRecordset-Methode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Abfragemethode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)


