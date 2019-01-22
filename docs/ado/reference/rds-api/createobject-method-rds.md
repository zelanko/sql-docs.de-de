---
title: CreateObject-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d220a9abc0e2dc72d7ab65306b514a9925b4fc43
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2019
ms.locfileid: "54419925"
---
# <a name="createobject-method-rds"></a>CreateObject-Methode (RDS)
Erstellt das Proxy für das Zielobjekt für Unternehmen, und gibt einen Zeiger darauf zurück. Die Proxy-Pakete und marshallt Daten an den serverseitigen Stub für die Kommunikation mit das Geschäftsobjekt, das zum Senden von Anforderungen und Daten über das Internet. Für in-Process-Komponentenobjekte keine Proxys verwendet werden, nur ein Zeiger auf das Objekt bereitgestellt wird.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
 Remote Data Service unterstützt die folgenden Protokolle: HTTP, HTTPS (HTTP über Secure Sockets Layer), DCOM und in-Process.  
  
|Protokoll|Syntax|  
|--------------|------------|  
|HTTP|Set object = DataSpace.CreateObject("ProgId", "https\://awebsrvr")|  
|HTTPS|Set object = DataSpace.CreateObject("ProgId", "https\://awebsrvr")|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|In-Process|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>Parameter  
 *Objekt*  
 Eine Objektvariable, die ein Objekt ergibt, der im angegebenen Typ ist *ProgID*.  
  
 *DataSpace*  
 Eine Objektvariable, steht ein [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) Objekt, das zum Erstellen einer Instanz des neuen Objekts verwendet.  
  
 *ProgID*  
 Ein **Zeichenfolge** -Wert enthält, die den programmgesteuerten Bezeichner, die eine serverseitige-Objekt, das Ihre Anwendung von Geschäftsregeln implementiert angeben.  
  
 *Awebsrvr* oder *Computername*  
 Ein **Zeichenfolge** Wert, der eine URL zur Angabe des Internetinformationsdienste (Internet Information Services, IIS)-Webservers, in dem eine Instanz des Server-Business-Objekts erstellt, darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Die *HTTP-Protokoll* ist das Standardprotokoll für die Web; *HTTPS* ist ein sicheres Webprotokoll. Verwenden der *DCOM-Protokolls* , wenn ein lokales Netzwerk ohne HTTP ausgeführt. Die *in-Process-* -Protokoll ist eine lokale Dynamic Link Library (DLL), wird ein Netzwerk nicht verwendet.  
  
## <a name="applies-to"></a>Gilt für  
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [DataFactory-Objekt, Abfragemethode und CreateObject-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [DataSpace-Objekt und CreateObject-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset-Methode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


