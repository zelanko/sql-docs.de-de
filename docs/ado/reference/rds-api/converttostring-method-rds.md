---
title: ConvertToString-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 426fd1fdcd3931981037b346b048de816e8596d0
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600290"
---
# <a name="converttostring-method-rds"></a>ConvertToString-Methode (RDS)
Konvertiert eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in eine MIME-Zeichenfolge, die das die Recordsetdaten darstellt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataFactory*  
 Eine Objektvariable, steht ein [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt.  
  
 *Recordset*  
 Eine Objektvariable, steht ein **Recordset** Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Mit ASP-Dateien verwenden **ConvertToString** zum Einbetten der **Recordset** in eine HTML-Seite, die generiert wird, auf dem Server, die es einem Clientcomputer übertragen.  
  
 **ConvertToString** ersten Laden der **Recordset** in der Microsoft Cursor Service-Tabelle aus, und klicken Sie dann einen ereignisdatenstrom generiert, im MIME-Format.  
  
 Auf dem Client Remote Data Service können konvertiert die MIME-Zeichenfolge wieder in einen voll funktionsfähigen **Recordset**. Dies funktioniert gut für die Behandlung von weniger als 400 Zeilen von Daten mit mehr als 1024 Byte Breite pro Zeile. Sie sollten nicht damit zum Streamen von BLOB-Daten und große Resultsets über HTTP. Keine Komprimierung über das Netzwerk für die Zeichenfolge, erfolgt sehr großer Datasets sehr viel Zeit an den Transport über HTTP, im Vergleich zu den über das Netzwerk optimierte Tablegram-Format definiert und bereitgestellt werden, indem Remote Data Service als systemeigene Transport Protocol Format dauert.  
  
> [!NOTE]
>  Wenn Sie Active Server Pages verwenden, die sich ergebende MIME-Zeichenfolge in eine Client-HTML-Seite einzubetten, achten Sie darauf, dass VBScript-Versionen vor Version 2.0 die Größe der Zeichenfolge auf 32 KB begrenzt. Wenn dieses Limit überschritten wird, wird ein Fehler zurückgegeben. Beachten Sie im Abfragebereich relativ klein, wenn der MIME-Einbettung mithilfe ASP-Dateien. Um dieses Problem zu beheben, laden Sie die neueste Version von VBScript aus der Microsoft Windows Script-Technologien-Website herunter.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ConvertToString-Methode – Beispiel (VB)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [ConvertToString-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


