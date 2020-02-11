---
title: Erstellen einer Verbindungs Zeichenfolge | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c9d81ef7be98f3c65167de24b3ff59ac6f05df5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925763"
---
# <a name="creating-a-connection-string"></a>Erstellen einer Verbindungszeichenfolge
Eine Verbindungs Zeichenfolge besteht aus einer Liste von Argument/Wert-Paaren (d. h. Parametern), die durch Semikolons getrennt sind. Beispiel:  
  
```syntax
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Alle Parameter müssen entweder von ADO oder vom angegebenen Anbieter erkannt werden.  
  
 ADO erkennt die folgenden fünf Argumente in einer Verbindungs Zeichenfolge.  
  
|Argument|BESCHREIBUNG|  
|--------------|-----------------|  
|*Anbieter*|Gibt den Namen eines Anbieters an, der für die Verbindung verwendet werden soll.|  
|*Dateiname*|Gibt den Namen einer anbieterspezifischen Datei an (z. b. ein persistente Datenquellen Objekt), die voreingestellte Verbindungsinformationen enthält.|  
|*Urne*|Gibt die Verbindungs Zeichenfolge als absolute URL an, die eine Ressource identifiziert, z. b. eine Datei oder ein Verzeichnis.|  
|*Remote Anbieter*|Gibt den Namen eines Anbieters an, der beim Öffnen einer Client seitigen Verbindung verwendet werden soll. (Nur Remote Datendienst.)|  
|*Remote Server*|Gibt den Pfadnamen des Servers an, der beim Öffnen einer Client seitigen Verbindung verwendet werden soll. (Nur Remote Datendienst.)|  
  
 Andere Argumente werden an den Anbieter mit dem Namen im *Provider* -Argument übermittelt, ohne dass von ADO verarbeitet wird.  
  
 Die HelloData-Anwendung in [HelloData: eine einfache ADO-Anwendung](../../../ado/guide/data/hellodata-a-simple-ado-application.md) verwendet die folgende Verbindungs Zeichenfolge:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 In dieser Verbindungs Zeichenfolge erkennt ADO nur `"Provider=SQLOLEDB"` den-Parameter, der den Microsoft OLE DB-Anbieter für SQL Server als ADO-Datenquelle angibt. Die restlichen Argument/Wert-Paare `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`werden an diesen Anbieter ausführlich übermittelt. Der Typ und die Gültigkeit solcher Parameter sind Anbieter spezifisch. Informationen zu gültigen Parametern, die in der Verbindungs Zeichenfolge übermittelt werden können, finden Sie in der Dokumentation des jeweiligen Anbieters.  
  
 Gemäß dem OLE DB Anbieter für SQL Server Dokumentation können Sie "Server" für den *Datenquellen* Parameter und "Database" für den *ursprünglichen Katalog* Parameter ersetzen. Folglich erzeugt die folgende Verbindungs Zeichenfolge Ergebnisse, die mit der obigen identisch sind:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
